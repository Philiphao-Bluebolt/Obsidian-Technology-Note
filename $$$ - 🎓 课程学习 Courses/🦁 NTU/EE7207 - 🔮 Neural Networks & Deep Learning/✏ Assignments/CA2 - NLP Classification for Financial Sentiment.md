
In this assignment, we classified the sentiment of several financial news broadcast script and classify their sentiments into three classes based on the wordings. The three classes were positive, negative and neutral.

I chose the FinBERT model for the training because it's a finetuned version of BERT with financial data, thus more suitable for financial problems. For the finetuning method, it's intuitive to use Supervised Finetuning (SFT) rather than Reinforcement Learning from Human Feedback (RLHF) for efficiency.

The finetuning dataset was fetched from Kaggle. During the search for dataset, I encountered some poorly labelled dataset in which a large proportion of sample sentiments were incorrectly marked so I had to check the labels of each dataset before selecting one. Eventually, I chose the public dataset [NLP : Financial News Sentiment Analysis](https://www.kaggle.com/code/khotijahs1/nlp-financial-news-sentiment-analysis/input). It contains more than 4000 labeled financial news headlines which is perfect for the task.

For each epoch in the training process, the dataset will be randomly shuffled and 20% of the samples would be chosen as test data.

The final evaluation showed that the finetuned FinBERT model can complete the sentiment classification with an accuracy of 84.6%

One of the phenomenon the experiment showed was that finetuning with an unevenly distributed datasets will probably lead to poor classification performance. For example, a NLP sentiment dataset with little negative labelled sample makes it difficult for the model to properly classify negative test sample. One of the solution is data augmentation.

Potentially, the sentiment classification task could be more detailed. The classification can be based on the discussed topic, for example countries or, rather than pure sentiment. This is a possible future improvement.

---
### Task Summary

+ **Problem**: Financial News Classification for Sentiment
+ **Coding Tools**: Python (Numpy, Pandas, Scikit-learn, Datasets, Transformers)
+ **Foundation Model**: FinBERT from HuggingFace
+ **Finetuning Method**: Supervised Finetuning (SFT)
+ **Dataset**: [NLP : Financial News Sentiment Analysis](https://www.kaggle.com/code/khotijahs1/nlp-financial-news-sentiment-analysis/input) from Kaggle
+ **Preprocessing**: Train-test Split (80% for training and 20% for testing)
+ **Evaluation**: Accuracy
+ **Final Result**: An accuracy of 84.6%

![](Pasted%20image%2020250406231123.png)

---
### Code Explanation

Import all the required packages including the data processing packages such as Numpy, Pandas, Scikit-learn, and NLP packages Datasets, Transformers.

```python

```

Firstly, the FinBERT foundation model and the tokenizer is initiated. The model is downloaded from the Hugging Face website automatically. The tokenization process will be applied to batches of data.

```python
# Initiate the tokenizer and model
model_name = 'yiyanghkust/finbert-tone'
tokenizer = AutoTokenizer.from_pretrained(model_name)
model = AutoModelForSequenceClassification.from_pretrained(model_name, num_labels=3)

def tokenize(batch):
    '''Batch-based tokenization function
    '''
    return tokenizer(batch['text'], padding=True, truncation=True, max_length=128)
```

The second stage is to input the dataset using Pandas and randomly split the samples into training set and testing set. After the spliting, the dataset is converted to the Hugging Face DatasetDict format and tokenized.

```python
# Load your CSV data
data = pd.read_csv("all-data.csv")

# Map sentiment labels to numerical values
label_mapping = {'negative': 0, 'neutral': 1, 'positive': 2}
data['label'] = data['sentiment'].map(label_mapping)

# Split dataset into training and testing
train_df, test_df = train_test_split(data, test_size=0.2, random_state=26)

# Convert to Hugging Face DatasetDict
dataset = DatasetDict({
    'train': Dataset.from_pandas(train_df.reset_index(drop=True)),
    'test': Dataset.from_pandas(test_df.reset_index(drop=True))
})

# Tokenize data
tokenized_dataset = dataset.map(tokenize, batched=True)
tokenized_dataset.set_format('torch', columns=['input_ids', 'attention_mask', 'label'])
```

I choose the batch size to be 16 and training epoch to be 3.

```python
# Define metrics function
accuracy = evaluate.load("accuracy")

def compute_metrics(eval_pred):
    logits, labels = eval_pred
    predictions = np.argmax(logits, axis=-1)
    return accuracy.compute(predictions=predictions, references=labels)

# Define training arguments
training_args = TrainingArguments(
    output_dir='./finbert-finetuned',
    eval_strategy='epoch',
    logging_strategy='epoch',
    save_strategy='epoch',
    num_train_epochs=3,
    per_device_train_batch_size=16,
    per_device_eval_batch_size=16,
    learning_rate=2e-5,
    weight_decay=0.01,
    load_best_model_at_end=True,
    metric_for_best_model='accuracy',
)
```

The training process starts with the above settings, using the tokenized financial news data to finetune the FinBERT model.

```python
# Finetune the model
trainer = Trainer(
    model=model,
    args=training_args,
    train_dataset=tokenized_dataset['train'],
    eval_dataset=tokenized_dataset['test'],
    processing_class=tokenizer,
    compute_metrics=compute_metrics,
)
trainer.train()

```

The evaluation of finetuned classifier is based on the accuracy.

```python
# Evaluate
evaluation_results = trainer.evaluate()
print(evaluation_results)
```

Eventually, the finetuned model is saved locally for future tasks.

```python
# Save model
model.save_pretrained('./finbert-finetuned-model')
tokenizer.save_pretrained('./finbert-finetuned-model')
```