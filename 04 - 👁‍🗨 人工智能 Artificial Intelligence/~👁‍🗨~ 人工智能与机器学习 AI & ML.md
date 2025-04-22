> "We should make machines think and work like mankind" —— 人工智能技术的终极目的

+ **网站**：[Kaggle](https://www.kaggle.com/) | [Hugging Face](https://huggingface.co/)

+ 🗺 [领域](#领域) - [四大](#四大领域%20AI-ML-NN-DL) | [[#]]
+ 🛠 [[#工具]] - [网站](#网站%20Websites) | [开发库](#开发库%20Dev%20Packages)
+ 📖 学习 - [陌生概念](#陌生概念%20Unfamiliar%20Concept) |


---
## 领域

人工智能技术是一个学科交叉程度很高的领域

+ **实现基础**：数学、计算机科学、电子硬件、物理、神经科学、心理学
+ **应用领域**：数据科学、机器人、控制科学

### 四大领域 AI-ML-NN-DL

+ 🤖 **人工智能**（AI）是一个宽泛的领域，其研究目的是让机器可以解决决策、感知、学习等普遍认为只有人类智能才能解决的任务。

+ 📰 **机器学习**（ML）是人工智能技术的一类，其特点是可以像人类一样从过去的经验（即数据）获得对一般情况的预测和判断能力（决策），最简单的机器学习算法是📐 **线性回归**

+ 🕸 **神经网络**（NN）是模拟人类神经元连接方式的一类机器学习模型，通过调整神经元之间连接的权重实现网络的训练

+ 🌌 **深度学习**（DL）是神经网络

### 按需求分类

+ 数据类型：自然语言处理（NLP）、图像处理、音频处理

+ 语义分割
+ 强化学习
+ 生成式AI
+ 具身智能
+ 

###


---
## 工具 Toolkit

+ **网站**
	+ Kaggle：
	+ Hugging Face：
+ **Python库**
	+ Scikit-learn：
	+ PyTorch：
	+ Tensorflow：
	+ Keras：


---
## 陌生概念

+ RAG

+ 前馈神经网络（Feed-Forward Neural Network）

	指的是一类单向神经网络，缩写FFNN，信息从输入层单向地往输出层移动，不存在回路结构。循环神经网络（RNN）和卷积神经网络（CNN）不属于前馈神经网络

+ 多层感知机（Multilayer Perceptron）

	缩写MLP，是一种前馈神经网络，特点是每个神经元的连接没有跳层

+ 向量化环境（Vectorized Envirnment）

	强化学习的一种并行训练技巧，一个向量化环境包含多个相同的子环境副本，智能体（Agent）在同一时刻同时对多个独立的子环境副本并行执行不同的动作，以提高观测（Observation）和奖励（Reward）数据的产生速度

+ 策略熵系数（Policy Entropy Coefficient）

	也称为熵权重（Entropy Weight），强化学习的超参数，用于控制策略优化的随机程度（Stochastics），即倾向于探索（Exploration）的程度。策略熵系数越大，策略随机程度越高，越倾向于探索未知状态。

+ 学习率（Learning Rate）

	深度学习的常见超参数，控制网络优化速度（梯度下降速度）的系数，过大（激进）的学习率会导致网络模型无法稳定收敛，过小（保守）的学习率会导致网络模型收敛速度慢、陷入局部最小值点

+ 价值函数损失系数（Value Function Loss Coefficient）

+ 最大梯度范数（Max Gradient Norm）

	也称最大梯度阈值（Threshold），深度学习的重要超参数，用于防止梯度爆炸，反向传播过程中范数（大小）超过这个值的梯度会被削减到此值，防止出现过大的梯度。

+ Batch

	（这个概念一般不翻译）在强化学习的框架下，Batch指的是一部分经验（Experiences）的合集。Batch具体包含哪部分经验则由实际算法决定
	
	Minibatch是Batch的一部分，是输入神经网络的单位，这种训练方法可以提高稳定性和效率

+ 经验（Experiences）

	也称为转换过程（Transition），是一组观测（Observation）、动作（Action）、奖励（Reward）、下一个观测（Next Observation）的合称，所以单环境训练时一步（Step）就产生一经验

+ 折扣因子"Gamma"（Discount Factor）

	折扣因子"Gamma"是一个强化学习的超参数，取值范围为$[0,1]$，用于描述计算未来奖励（Reward）时的衰减系数，直观上，Gamma取值越小，策略越倾向于考虑短期奖励，即越“短视

+ Episode

	（这个概念一般不翻译）在强化学习领域，Episode指的是智能体与环境进行的一次从初始状态到终止状态的完整交互，有时候，为了避免智能体在环境中卡在某些状态，我们也会规定超过一定步数以后结束当前的Episode

+ 基线算法（Baselines）



