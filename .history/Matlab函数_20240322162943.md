[TOC]



# sprintf

将数据格式化为字符串或字符向量

## 语法

```matlab
str = sprintf(formatSpec,A1,...,An)
[str,errmsg] = sprintf(formatSpec,A1,...,An)
str = sprintf(literalText)
```



## 说明

[示例](https://ww2.mathworks.cn/help/matlab/ref/sprintf.html#btf_b3i)

`str = sprintf(formatSpec,A1,...,An)` 使用 `formatSpec` 指定的格式化操作符格式化数组 `A1,...,An` 中的数据，并在 `str` 中返回结果文本。`sprintf` 函数按列顺序格式化 `A1,...,An` 中的值。如果 `formatSpec` 是字符串，则输出 `str` 也是字符串。否则，`str` 是字符向量。

要以字符串数组或字符向量元胞数组形式返回多个格式化文本段，请使用 `compose` 函数。

如果操作失败，`[str,errmsg] = sprintf(formatSpec,A1,...,An)` 将以字符向量形式返回一条错误消息。否则，`errmsg` 为空。

`str = sprintf(literalText)` 转换 `literalText` 中的转义字符序列，例如 `\n` 和 `\t`。它会原样返回所有其他字符。如果 `literalText` 包含格式化操作符（例如 `%f`），则 `str` 将丢弃该字符以及之后的所有字符。

### 使用位置标识符 (n$) 对输入重新排序 



尝试此示例Copy Command  Copy Code

使用 `n$` 位置标识符将输入值重新排序。

```matlab
A1 = 'X';
A2 = 'Y';
A3 = 'Z';
formatSpec = ' %3$s %2$s %1$s';
str = sprintf(formatSpec,A1,A2,A3)
str = 
' Z Y X'
```

**注意：**如果输入参数为数组，则不能使用标识符指定该输入参数中的特定数组元素。

### 根据元胞数组中的值创建字符向量 

```
C = { 1,   2,   3 ;
     'AA','BB','CC'};

str = sprintf(' %d %s',C{:})
str = 
' 1 AA 2 BB 3 CC'
```

语法 `C{:}` 创建一个逗号分隔的数组列表，该列表以列顺序包含 `C` 中每个元胞的内容。例如，`C{1}==1` 和 `C{2}=='AA'`。



### 输入长语句

如果语句无法容纳在一行中，请使用省略号（三个句点）`...`，后跟 **Return** 或 **Enter** 以指示该语句在下一行继续。例如，

```
s = 1 -1/2 + 1/3 -1/4 + 1/5 - 1/6 + 1/7 ...
      - 1/8 + 1/9 - 1/10 + 1/11 - 1/12;
```

`=`、`+` 和 - 符号周围的空白是可选的，但可提高可读性。





**可选操作符**

可选标识符、标志、字段宽度、精度和子类型操作符进一步定义了输出文本的格式。

- **标识符**

	处理函数输入参数的顺序。使用语法 `n$`，其中 `n` 代表函数调用中其他输入参数的位置。

	**示例：**`('%3$s %2$s %1$s %2$s','A','B','C')` 将输入参数 `'A'`、`'B'`、`'C'` 输出为：`C B A B`。

	**注意：**如果输入参数为数组，则不能使用标识符指定该输入参数中的特定数组元素。

- **标志**

| `'–'` | 左对齐。 **示例：**`%-5.2f` **示例：**`%-10s`                |
| ----- | ------------------------------------------------------------ |
| `'+'` | 始终为任何数值输出符号字符（+ 或 –）。 **示例：**`%+5.2f` 右对齐文本。 **示例：**`%+10s` |
| `' '` | 在值之前插入空格。 **示例：**`% 5.2f`                        |
| `'0'` | 在值之前补零以填充字段宽度。 **例如：**`%05.2f`              |
| `'#'` | 修改选定的数值转换：对于 `%o`、`%x` 或 `%X`，将输出 `0`、`0x` 或 `0X` 前缀。对于 `%f`、`%e` 或 `%E`，即使精度为零也将输出小数点。对于 `%g` 或 `%G`，不删除尾随零或小数点。**示例：**`%#5.0f` |



## 脚本和函数

### 概述

MATLAB® 提供了一个强大的编程语言和交互式计算环境。您可以使用此语言在 MATLAB 命令行中一次输入一个命令，也可以向某个文件写入一系列命令，按照执行任何 MATLAB 函数的相同方式来执行这些命令。使用 MATLAB 编辑器或任何其他文件编辑器可以创建您自己的函数文件。按照调用任何其他 MATLAB 函数或命令的相同方式来调用这些函数。

两种程序文件：

- 脚本，不接受输入参数或返回输出参数。它们处理工作区中的数据。
- 函数，可接受输入参数，并返回输出参数。内部变量是函数的局部变量。

如果您是新 MATLAB 程序员，您只需在当前文件夹中创建您希望尝试的程序文件。当您创建的文件越来越多时，您可能希望将这些文件组织到其他文件夹和个人工具箱，以便将其添加到您的 MATLAB 搜索路径中。

如果您复制多个函数名称，MATLAB 会执行在搜索路径中显示的第一个函数。

要查看程序文件（例如，`myfunction.m`）的内容，请使用

```
type myfunction
```

### 脚本

当调用*脚本*时，MATLAB 仅执行在文件中找到的命令。脚本可以处理工作区中的现有数据，也可以创建要在其中运行脚本的新数据。尽管脚本不会返回输出参数，其创建的任何变量都会保留在工作区中，以便在后续计算中使用。此外，脚本可以使用 [`plot`](https://ww2.mathworks.cn/help/matlab/ref/plot.html) 等函数生成图形输出。

例如，创建一个名为 `magicrank.m` 的文件，该文件包含下列 MATLAB 命令：

```
% Investigate the rank of magic squares
r = zeros(1,32);
for n = 3:32
   r(n) = rank(magic(n));
end
bar(r)
```

键入语句

```
magicrank
```

使 MATLAB 执行命令、计算前 30 个幻方矩阵的秩，并绘制结果的条形图。执行完文件之后，变量 `n` 和 `r` 将保留在工作区中。

![img](D:/`Programme_tool/Typora/picture/p10_zh_CN.png)

### 函数

函数是可接受输入参数并返回输出参数的文件。文件名和函数名称应当相同。函数处理其自己的工作区中的变量，此工作区不同于您在 MATLAB 命令提示符下访问的工作区。

`rank` 提供了一个很好的示例。文件 `rank.m` 位于文件夹

```
toolbox/matlab/matfun
```

您可以使用以下命令查看文件

```
type rank
```

下面列出了此文件：

```
function r = rank(A,tol)
%   RANK Matrix rank.
%   RANK(A) provides an estimate of the number of linearly
%   independent rows or columns of a matrix A.
%   RANK(A,tol) is the number of singular values of A
%   that are larger than tol.
%   RANK(A) uses the default tol = max(size(A)) * norm(A) * eps.

s = svd(A);
if nargin==1
   tol = max(size(A)') * max(s) * eps;
end
r = sum(s > tol);
```

函数的第一行以关键字 [`function`](https://ww2.mathworks.cn/help/matlab/ref/function.html) 开头。它提供函数名称和参数顺序。本示例中具有两个输入参数和一个输出参数。

第一个空行或可执行代码行前面的后续几个行是提供帮助文本的注释行。当键入以下命令时，会输出这些行

```
help rank
```

帮助文本的第一行是 H1 行，当对文件夹使用 [`lookfor`](https://ww2.mathworks.cn/help/matlab/ref/lookfor.html) 命令或请求 `help` 时，MATLAB 会显示此行。

文件的其余部分是用于定义函数的可执行 MATLAB 代码。函数体中引入的变量 `s` 以及第一行中的变量（即 `r`、`A` 和 `tol`）均为函数的*局部*变量；他们不同于 MATLAB 工作区中的任何变量。

本示例演示了 MATLAB 函数不同于其他编程语言函数的一个方面，即可变数目的参数。可以采用多种不同方法使用 [`rank`](https://ww2.mathworks.cn/help/matlab/ref/rank.html) 函数：

```
rank(A)
r = rank(A)
r = rank(A,1.e-6)
```

许多函数都按此方式运行。如果未提供输出参数，结果会存储在 `ans` 中。如果未提供第二个输入参数，此函数会运用默认值进行计算。函数体中提供了两个名为 [`nargin`](https://ww2.mathworks.cn/help/matlab/ref/nargin.html) 和 [`nargout`](https://ww2.mathworks.cn/help/matlab/ref/nargout.html) 的数量，用于告知与函数的每次特定使用相关的输入和输出参数的数目。`rank` 函数使用 `nargin`，而不需要使用 `nargout`。

### 函数类型

MATLAB 提供了多种不同函数用于编程。

#### 匿名函数

*匿名函数*是一种简单形式的 MATLAB 函数，该函数在一个 MATLAB 语句中定义。它包含一个 MATLAB 表达式和任意数目的输入和输出参数。您可以直接在 MATLAB 命令行中定义匿名函数，也可以在函数或脚本中定义匿名函数。这样，您可以快速创建简单函数，而不必每次为函数创建文件。

根据表达式创建匿名函数的语法为

```
f = @(arglist)expression
```

下面的语句创建一个求某个数字的平方的匿名函数。当调用此函数时，MATLAB 会将您传入的值赋值给变量 `x`，然后在方程 `x.^2` 中使用 `x`：

```
sqr = @(x) x.^2;
```

要执行 `sqr` 函数，请键入

```
a = sqr(5)
a =
   25
```

#### 主函数和局部函数

任何非匿名函数必须在文件中定义。每个此类函数文件都包含一个必需的*主函数*（最先显示）和任意数目的*局部函数*（位于主函数后面）。主函数的作用域比局部函数更广。因此，主函数可以从定义这些函数的文件外（例如，从 MATLAB 命令行或从其他文件的函数中）调用，而局部函数则没有此功能。局部函数仅对其自己的文件中的主函数和其他局部函数可见。

[函数](https://ww2.mathworks.cn/help/matlab/learn_matlab/scripts-and-functions.html#f4-25892)部分中显示的 `rank` 函数就是一个主函数的示例。

#### 私有函数

*私有函数*是一种主函数。其特有的特征是：仅对一组有限的其他函数可见。如果您希望限制对某个函数的访问，或者当您选择不公开某个函数的实现时，此种函数非常有用。

私有函数位于带专有名称 `private` 的子文件夹中。它们是仅可在母文件夹中可见的函数。例如，假定文件夹 `newmath` 位于 MATLAB 搜索路径中。`newmath` 的名为 `private` 子文件夹可包含只能供 `newmath` 中的函数调用的特定函数。

由于私有函数在父文件夹外部不可见，因此可以使用与其他文件夹中的函数相同的名称。如果您希望创建您自己的特定函数的版本，并在其他文件夹中保留原始函数，此功能非常有用。由于 MATLAB 在标准函数之前搜索私有函数，因此在查找名为 `test.m` 的非私有文件之前，它将查找名为 `test.m` 的私有函数。

#### 嵌套函数

您可以在函数体中定义其他函数。这些函数称为外部函数中的*嵌套*函数。嵌套函数包含任何其他函数的任何或所有组成部分。在本示例中，函数 `B` 嵌套在函数 `A` 中：

```
function x = A(p1, p2)
...
B(p2)
   function y = B(p3)
   ...
   end
...
end
```

与其他函数一样，嵌套函数具有其自己的工作区，可用于存储函数所使用的变量。但是，它还可以访问其嵌套在的所有函数的工作区。因此，举例来说，主函数赋值的变量可以由嵌套在主函数中的任意级别的函数读取或覆盖。类似地，嵌套函数中赋值的变量可以由包含该函数的任何函数读取或被覆盖。

### 全局变量

如果您想要多个函数共享一个变量副本，只需在所有函数中将此变量声明为 [`global`](https://ww2.mathworks.cn/help/matlab/ref/global.html)。如果您想要基础工作区访问此变量，请在命令行中执行相同操作。全局声明必须在函数中实际使用变量之前进行。全局变量名称使用大写字母有助于将其与其他变量区分开来，但这不是必需的。例如，在名为 `falling.m` 的文件创建一个新函数：

```
function h = falling(t)
global GRAVITY
h = 1/2*GRAVITY*t.^2;
```

然后，以交互方式输入语句

```
global GRAVITY
GRAVITY = 32;
y = falling((0:.1:5)');
```

通过上述两条全局语句，可以在函数内使用在命令提示符下赋值给 `GRAVITY` 的值。然后，您可以按交互方式修改 `GRAVITY` 并获取新解，而不必编辑任何文件。

### 命令与函数语法

您可以编写接受字符参数的 MATLAB 函数，而不必使用括号和引号。也就是说，MATLAB 将

```
foo a b c
```

解释为

```
foo('a','b','c')
```

但是，当使用不带引号的命令格式时，MATLAB 无法返回输出参数。例如，

```
legend apples oranges
```

使用 `apples` 和 `oranges` 作为标签在绘图上创建图例。如果您想要 [`legend`](https://ww2.mathworks.cn/help/matlab/ref/legend.html) 命令返回其输出参数，必须使用带引号的格式：

```
[legh,objh] = legend('apples','oranges');
```

此外，如果其中任一参数不是字符向量，必须使用带引号的格式。



**小心**

虽然不带引号的命令语法非常方便，但在某些情况下可能会出现使用不当的情形，而 MATLAB 并不会产生错误信息。

#### 在代码中构造字符参数

带引号的函数格式可用于在代码中构造字符参数。下面的示例处理多个数据文件，即 `August1.dat`、`August2.dat` 等。它使用函数 [`int2str`](https://ww2.mathworks.cn/help/matlab/ref/int2str.html)，该函数将整数转换为字符以便生成文件名：

```matlab
for d = 1:31
   s = ['August' int2str(d) '.dat'];
   load(s) 
   % Code to process the contents of the d-th file
end
```