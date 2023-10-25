# 变量和可变性

C 以及 C++ 中, 我们使用变量来存放各种各样的数据。 为了方便区分和比较, C++对变量设置了类型，不同类型的变量只能存放对应类型的数据，并且
占用不同大小的内存空间。

## 基本数据类型

| 类型 | 关键字 |
-------|-------|
| 无类型 | void |
| 布尔型 | bool |
| 字符型 | char |
| 整型 | int |
| 浮点型 | float |
| 双浮点型 | double |
| 宽字符型 | wchar_t |


### 修饰符

一些基本类型可以使用一个或多个类型修饰符进行修饰：

`signed` `unsigned` `short` `long`

比如
```cpp
unsigned int a = 12 // 无符号整型
```


> `wchar_t` 其实就是 `short int` 的别名
> ```cpp
> typedef short int wchar_t // 将 wchar_t 定义成 short int
>```