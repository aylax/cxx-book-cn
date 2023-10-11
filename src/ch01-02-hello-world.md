## Hello, World!

我们已经安装好了 C++，接着编写第一个 C++ 程序。按照传统，在学习一门新语言时都会编写一个输出“Hello, world!”（你好，世界）的简单程序，本章我们也是如此。

> 注意：本书假定你已经熟悉基本的命令行。C++ 本身对编辑器、工具或代码存放的位置都没有特殊要求。所以要是你更喜欢 IDE 而不是命令行的话，可以随意选用你喜爱的 IDE。目前很多 IDE 都提供了一定程度的 C++ 支持。有关详细信息，请查看 IDE 的文档。

### 创建项目目录

首先，创建一个存放 C++ 代码的目录。C++ 不关心代码存放的位置，但是对于本书中的练习和项目，我们建议在操作系统的主目录（home，在 Windows 下即用户目录）中创建一个 *projects* 目录，并保存你的全部项目。

打开终端，输入下面命令来创建 *projects* 目录，以在此目录里面创建 “Hello, world!” 项目目录。

对于 Linux、macOS 和 Windows 的 PowerShell，请输入以下命令：

```console
$ mkdir ~/projects
$ cd ~/projects
$ mkdir hello_world
$ cd hello_world
```

对于 Windows CMD，输入以下内容：

```cmd
> mkdir "%USERPROFILE%\projects"
> cd /d "%USERPROFILE%\projects"
> mkdir hello_world
> cd hello_world
```

### 编写和运行 C++ 程序

接下来，创建一个源文件并命名为 *main.cpp*。C++ 文件通常以 *.cpp* 扩展名结尾。如果文件名中使用了多个单词，请使用下划线将它们隔开。例如，命名为 *hello_world.cpp*，而不是 *helloworld.cpp*。

现在打开刚创建好的 *main.cpp* 文件，输入示例 1-1 中的代码。

<span class="filename">文件名：main.cpp</span>

```cpp
#include <iostream>

using namespace std;

int main() {
    cout << "Hello, world!";
    return 0;
}
```

<span class="caption">示例 1-1：一个打印 `Hello, world!` 的程序</span>

保存文件，并回到终端窗口。在 Linux 或 macOS 上，输入以下命令，编译并运行文件：

```console
$ g++ main.cpp -o main
$ ./main
Hello, world!
```

在 Windows 上，输入 `.\main.exe` 来代替 `./main`：

```powershell
> g++ main.cpp -o .\main.exe
> .\main.exe
Hello, world!
```

不管你使用哪种操作系统，该字符串 `Hello, world!` 都应打印到了终端上。如果看不到此输出，请参考“安装”小节的[“疑难解答”][troubleshooting]<!-- ignore -->小节来查找解决方法。

如果 `Hello, world!` 打印成功，那么祝贺你！你已经正式编写了一个 C++ 程序。你已经成为了一名 C++ 开发者——欢迎加入 C++ 大家庭！

### C++ 程序剖析

让我们详细回顾一下 “Hello, world!” 程序发生了什么。这是拼图的第一块:

```cpp
#include<iostream>

using namespace std;

int main() {
  cout << "Hello, world!";
  return 0;
}
```

这几行定义了 C++ 的函数。`main` 函数（也称为主函数）很特殊：它始终是每个可执行 C++ 程序中运行的第一个代码。

第一行引入了一个C++库文件(iostream: 流输入输出库)，用于辅助处理c++程序的输入输出，这一行结尾不需要加分号`;`。

第二行则是使用了一个名字叫 `std`的命名空间 (`using`: 使用, `namespace`: 命名空间)。命名空间指定了*标识符*的可见范围 (比如: 标识符 `cout` 就是由命名空间 `std` 提供的), 命名空间可以解决*标识符*的重名问题。在C++中, 标准库程序的标识符都属于命名空间 `std`。

第三行声明一个名为 `main` 的函数，不带参数。如果有参数，那么它们被将放在括号 `()` 内。int 指定了函数的结果类型(也叫返回值类型)为整数。

另外，请注意，函数主体用大括号 `{}` 括起来。C++ 需要函数体的所有内容都被括号包围起来。一种好的代码风格是将左大括号放在函数声明的同一行，且之间带有一个空格。

`main` 函数内部是以下代码：

```cpp
    cout << "Hello, world!";
    return 0;
```

该行完成了此简单程序中的所有工作：它将文本打印到屏幕上, 然后返回结果值 0。这里有 4 个要注意的重要细节。

首先，C++ 风格的缩进推荐使用 4 个空格，而不是制表符。

其次，`std::cout` 是我们的 *标准输出流对象*, `<<` 则是我们的 *输出流运算符*。

第三，你看到 `"Hello, world!"` 字符串。我们将这个字符串作为参数通过运算符 `<<` 传递给对象 `std::cout`，然后字符串便会被打印到屏幕上。

第四，我们用分号（`;`，注意这是英文分号）结束该行，这表明该表达式已结束，下一个表达式已准备好开始。C++ 代码的大多数行都以一个 `;` 结尾。 函数代码块末尾的 `return 0;` 告诉我们函数的返回结果是0。

### 编译和运行是独立的步骤

刚才我们运行一个新创建的程序。现在我们将分解这个过程，并检查每个步骤。

在运行 C++ 程序之前，必须使用 C++ 编译器来编译它，输入 `g++` 命令并传入源文件的名称，如下所示：

```console
# Windows平台
$ g++ main.cpp -o main.exe
```

```
# Mac or Linux 平台下
$ g++ main.cpp -o main
```

编译成功后，C++ 就会输出一个二进制可执行文件。

在 Linux、macOS 或 Windows 的 PowerShell 中，可通过输入 `ls` 命令来查看可执行文件。在 Linux 和 macOS 中，你将看到两个文件。使用 Windows 的 PowerShell，你将看到与使用 CMD 相同的三个文件。

```console
$ ls
main  main.cpp
```

对于 Windows 的 CMD，可输入以下内容：

```cmd
> dir /B %= the /B option says to only show the file names =%
main.exe
main.cpp
```

这显示了带有 *.cpp* 扩展名的源代码文件，可执行文件（在 Windows 上是 *main.exe*，在所有其他平台上是 *main*）。在这里，运行 *main* 或者 *main.exe* 文件，如下所示：

```console
$ ./main # or .\main.exe on Windows
```

如果 *main.cpp* 是 “Hello, world!” 程序，这将会打印 `Hello, world!` 到终端上。

如果你只熟悉动态语言，如 Ruby、Python 或 JavaScript，你很可能不习惯分多个步骤来编译和运行程序的方式。C++ 是一门**预编译**(*ahead-of-time compiled*)语言，这意味着你可以编译一个程序，将编译后的可执行文件给别人，即使他们没有安装 C++编译器 也可以运行程序。如果你为其他人提供 *.rb*、*.py* 或 *.js* 文件，那么对方也需要分别安装对应 Ruby、Python 或 JavaScript 的语言支持环境。但是在这些语言中，只需要一条命令来编译和运行程序。一切都是语言设计权衡的结果。

[troubleshooting]: ch01-01-installation.html#troubleshooting
