
+ 🎧️ **[C++](#C++)**
+ 🐍 **[Python](#Python)**
+ 🧮 **[算法逻辑](#算法逻辑)**

---
## C++

+ **空容器`size()`减一导致数值溢出**：由于容器返回的大小值默认为无符号整型，当容器大小为空时，减一变负值会导致无符号整型数溢出。正确写法是用`<=`、`>=`代替`<`、`>`

```cpp
if (i > arr.size() - 1)
// 改为
if (i >= arr.size())
```

+ **数字字符使用`to_string()`误转为ASCII码**：函数`to_string`会把单个字符转换为对应的ASCII码字符串而非直接转换为字符串；字符转字符串的正确方法是在空字符串后连接字符

```cpp
char c = '1';
str = to_string(c);
// 改为
str = std::string() + c;
// 或
std::string str(1, c);
```

+ **数组越界`gcc`不报错**：`gcc`编译器默认不检查容器访问越界等未定义行为；若要加上这个功能，在编译时调用模块`-fsanitize=address,undefined`，否则只能插桩调试

```
g++ -std=c++17 -g -fsanitize=address,undefined -O1 main.cpp -o main
```


---
## Python




---
## 算法逻辑

+ **二分查找循环条件误写为`low != high`**：若查找目标不存在，两个指针在最后一步搜索会互相跨越而不触发终止，可能导致数组越界；二分查找的正确循环条件应为`low <= high`

```python
arr = [1, 2, 4, 5]

```