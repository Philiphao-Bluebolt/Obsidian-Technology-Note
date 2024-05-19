
---
## Shell函数

Shell函数可以用来定义全新的命令，一般在`.bashrc`中使用

`$1, $2, $3 ...`表示第n个参数的引用

```bash
my_cmd(){
	echo "Hello $1! $2! $3!"
}
```