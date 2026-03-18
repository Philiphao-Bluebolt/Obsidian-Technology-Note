+ **参考** - [CPlusPlus](https://cplusplus.com/reference/utility/pair/pair/)

配对是标准库 utility 引入的泛型模板类，用于储存一对数据。

```cpp
#include <utility>
```

---
## 常见用法

+ **创建配对**

```cpp
std::pair<int, bool> my_pair(10, false);
my_pair_2 = std::make_pair(7, true);
```

+ **读取数值**

```cpp
auto [value, isTrue] = my_pair;
value2 = my_pair_2.first;
isTrue2 = my_pair_2.second;
```