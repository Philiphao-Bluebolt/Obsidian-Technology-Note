在ACM算法题目中，C++测试用例常以文本格式提供，考试者须使用`cin`读入测试数据。在本地测试时，手动输入数据到缓冲区很不方便，因此需要一些自动导入测试数据到缓冲区的方法，无须更改源代码中的`cin`语句即可实现自动测试。

---

> **文件读取** - 将文件`input.txt`读取到标准输入输出流`stdio`

```cpp
#include <fstream>
std::freopen("input.txt", "r", stdio)
```

> **字符串输入** - 将`cin`使用的寄存器重定向到字符输入流

```cpp
#include
string test_data = "1 2 3\n 4 5 6";
istringstream fakeinput(test_data);
cin.rdbuf(fakeinput.rdbuf());
```

> 