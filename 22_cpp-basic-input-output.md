# C++ 基本的输入输出

C++ 标准库提供了一组丰富的输入/输出功能，我们将在后续的章节进行介绍。本章将讨论 C++ 编程中最基本和最常见的 I/O 操作。

C++ 的 I/O 发生在流中，流是字节序列。如果字节流是从设备（如键盘、磁盘驱动器、网络连接等）流向内存，这叫做 **输入操作** 。如果字节流是从内存流向设备（如显示屏、打印机、磁盘驱动器、网络连接等），这叫做 **输出操作** 。

## I/O 库头文件

下列的头文件在 C++ 编程中很重要。

| 头文件 | 函数和描述 |
| ---- | ---- |
| &lt;iostream&gt; | 该文件定义了  **cin、cout、cerr**  和  **clog**  对象，分别对应于标准输入流、标准输出流、非缓冲标准错误流和缓冲标准错误流。 |
| &lt;iomanip&gt; | 该文件通过所谓的参数化的流操纵器（比如  **setw**  和  **setprecision** ），来声明对执行标准化 I/O 有用的服务。 |
| &lt;fstream&gt; | 该文件为用户控制的文件处理声明服务。我们将在文件和流的相关章节讨论它的细节。 |

## 标准输出流（cout）

预定义的对象  **cout**  是  **ostream**  类的一个实例。cout 对象"连接"到标准输出设备，通常是显示屏。 **cout**  是与流插入运算符 &lt;&lt; 结合使用的，如下所示：

```C++
#include <iostream>
 
using namespace std;
 
int main( )
{
   char str[] = "Hello C++";
 
   cout << "Value of str is : " << str << endl;
}
```

当上面的代码被编译和执行时，它会产生下列结果：

```C++
Value of str is : Hello C++
```

C++ 编译器根据要输出变量的数据类型，选择合适的流插入运算符来显示值。&lt;&lt; 运算符被重载来输出内置类型（整型、浮点型、double 型、字符串和指针）的数据项。

流插入运算符 &lt;&lt; 在一个语句中可以多次使用，如上面实例中所示， **endl**  用于在行末添加一个换行符。

## 标准输入流（cin）

预定义的对象  **cin**  是  **istream**  类的一个实例。cin 对象附属到标准输入设备，通常是键盘。 **cin**  是与流提取运算符 &gt;&gt; 结合使用的，如下所示：

```C++
#include <iostream>
 
using namespace std;
 
int main( )
{
   char name[50];
 
   cout << "请输入您的名称： ";
   cin >> name;
   cout << "您的名称是： " << name << endl;
 
}
```

当上面的代码被编译和执行时，它会提示用户输入名称。当用户输入一个值，并按回车键，就会看到下列结果：

```C++
请输入您的名称： cplusplus
您的名称是： cplusplus
```

C++ 编译器根据要输入值的数据类型，选择合适的流提取运算符来提取值，并把它存储在给定的变量中。

流提取运算符 &gt;&gt; 在一个语句中可以多次使用，如果要求输入多个数据，可以使用如下语句：

```C++
cin >> name >> age;
```

这相当于下面两个语句：

```C++
cin >> name;
cin >> age;
```

## 标准错误流（cerr）

预定义的对象  **cerr**  是  **ostream**  类的一个实例。cerr 对象附属到标准错误设备，通常也是显示屏，但是  **cerr**  对象是非缓冲的，且每个流插入到 cerr 都会立即输出。

**cerr**  也是与流插入运算符 &lt;&lt; 结合使用的，如下所示：

```C++
#include <iostream>
 
using namespace std;
 
int main( )
{
   char str[] = "Unable to read....";
 
   cerr << "Error message : " << str << endl;
}
```

当上面的代码被编译和执行时，它会产生下列结果：

```C++
Error message : Unable to read....
```

## 标准日志流（clog）

预定义的对象  **clog**  是  **ostream**  类的一个实例。clog 对象附属到标准错误设备，通常也是显示屏，但是  **clog**  对象是缓冲的。这意味着每个流插入到 clog 都会先存储在缓冲在，直到缓冲填满或者缓冲区刷新时才会输出。

**clog**  也是与流插入运算符 &lt;&lt; 结合使用的，如下所示：

```C++
#include <iostream>
 
using namespace std;
 
int main( )
{
   char str[] = "Unable to read....";
 
   clog << "Error message : " << str << endl;
}
```

当上面的代码被编译和执行时，它会产生下列结果：

```C++
Error message : Unable to read....
```

通过这些小实例，我们无法区分 cout、cerr 和 clog 的差异，但在编写和执行大型程序时，它们之间的差异就变得非常明显。所以良好的编程实践告诉我们，使用 cerr 流来显示错误消息，而其他的日志消息则使用 clog 流来输出。
