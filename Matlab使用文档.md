#### 桌面基础

当前文件夹、命令窗口、工作区

分号结束语句不会在命令窗口显示输出结果

向上、向下箭头键重复使用以前的命令

#### 矩阵与数组

##### 创建矩阵

###### 行数组

用逗号或空格分割元素

###### 列数组

用分号分割每行

##### 另一种方法：使用函数

```matlab
ones()、zeros()、rand()
```



#### 矩阵与数组运算

```matlab
% 转置
a'

% 矩阵乘法，
计算行和列之间的内积
*	

不是整型矩阵-> matlab将数字存储为浮点值

% 使用format命令显示更多的十进制数字,只影响数字显示
format long 	format short		

% 求逆
inv(a)	

% 执行元素乘法
.*

% 连接运算符
[]

% 连接函数
A = [1 3 5];
B = [3 6 9];
union(A,B)
ans = 1×5

     1     3     5     6     9

% 求根
sqrt(-1)
用i，j表示复数的虚数部分
```



###### 数组索引

指定行列下标

**A=magic(4)**

魔方矩阵——行和、列和都相等



超出索引打咩

可以在赋值语句左侧指定当前维度之外的元素，数组大小增加以适应元素。

###### 引用数组的多个元素

使用冒号运算符

单独的冒号指定该维度中的所有元素





```matlab
###### 查看工作区内容
whos
Name Size Bytes Class Attributes
A 4x4 128 double
B 3x5x2 240 double

save myfile.mat
保存将当前工作文件夹中的工作区保存在一个以.mat为扩展名的压缩文件中

从mat文件导入数据到工作空间使用load命令。
load myfile.mat

myText = ‘Hello, world’;
If the text includes a single quote, use two single quotes within the definition.

如果文本中包含单引号，则在定义中使用两个单引号。
otherText = ‘You”re right’
otherText =
‘You’re right’

你可以将字符数组如矩阵一样用方括号合并。
longText = [myText,' - ',otherText]
longText =
‘Hello, world - You’re right’

要将数值转换成字符，使用函数，如num2str 或int2str
```



当有多个输出参数时，将它们括在方括号中：

***[maxA,location] = max(A)***

maxA = 5	location = 3



将任何字符输入括在单引号中：

***disp(‘hello world’)***

hello world



##### 创建二维线图，就要使用***plot***函数

您可以对轴进行标记并添加标题。

- ***xlabel(‘x’)***

- ***ylabel(‘sin(x)’)***
- ***title(‘Plot of the Sine Function’)***
- ***plot(x,y,’r–’)***

若要将图添加到现有图形，请使用 ***hold***。

在***hold off*** 或关闭窗口之前，所有的图都会出现在当前的图形窗口中。


##### 3-D Plots三维图

三维图通常显示一个函数在两个变量中定义的曲面，z＝f（x，y）
对Z，首先创建一个（x，y）点的集合在函数定义域使用***meshgrid***

- ***[X,Y] = meshgrid(-2:.2:2);***

- ***Z = X .\* exp(-X.^2 - Y.^2);***

然后，创建一个表面图。

- ***surf(X,Y,Z)***

***surf***及其伴随***meshgrid***在三个维度上显示表面。***surf***以彩色显示连接线和表面的面。***mesh***产生线框表面，仅将连接定义点的线染色。

##### 用***subplot*** 函数在同一窗口不同区域显示多个图。

***subplot*** 函数的前两个参数指明行和列图的数量。第三个输入指定哪个区域绘图。例如，在2*2格在图形窗口中创建四个图。

1. ***t = 0:pi/10:2*pi;**

2. ***[X,Y,Z] = cylinder(4\*cos(t));***

	[x,y,z]=cylinder(r,n) 函数一个半径为r、高度为1的圆柱体的x，y，z轴的坐标值，圆柱体沿其周长有n个等距分布的点

3. ***subplot(2,2,1); mesh(X); title(‘X’);***

4. ***subplot(2,2,2); mesh(Y); title(‘Y’);***

5. ***subplot(2,2,3); mesh(Z); title(‘Z’);***

6. ***subplot(2,2,4); mesh(X,Y,Z); title(‘X,Y,Z’);***



###### 程序和脚本

To create a script, use the ***edit*** command,

要创建脚本，请使用 ***edit*** 命令，

***edit plotrand***



###### 使用百分号（***%\***）符号添加注释。

***% Generate random data from a uniform distribution***



在脚本中，可以循环使用部分代码，并有条件地使用关键字（如***for\***, ***while\***, ***if\***, 和 ***switch\***.
）切换执行部分。
For example, create a script named calcmean.m that uses a ***for*** loop to calculate the mean of five random samples and the overall mean.
例如，创建一个叫calcmean.m 的脚本，用一个***for***循环来计算五个随机样本均值和总体均值 。

***nsamples = 5;***

***npoints = 50;***

***for k = 1:nsamples***

***currentData = rand(npoints,1);***

***sampleMean(k) = mean(currentData);***

***end***

***overallMean = mean(sampleMean)\***

```matlab
现在，修改for循环，以便每次迭代时都可以查看结果。在命令窗口中显示文本，包括当前迭代次数，并从分配过程样本删除分号。
for k = 1:nsamples
iterationString = [‘Iteration #’,int2str(k)];
disp(iterationString)
currentData = rand(npoints,1);
sampleMean(k) = mean(currentData)
end
overallMean = mean(sampleMean)
When you run the script, it displays the intermediate results, and then calculates the overall mean.
但你运行这个脚本时，它会显示中间的结果然后计算其总体均值。
calcmean
Iteration #1
sampleMean =
0.3988
Iteration #2
sampleMean =
0.3988 0.4950
Iteration #3
sampleMean =
0.3988 0.4950 0.5365
Iteraion #4
sampleMean =
0.3988 0.4950 0.5365 0.4870
Iteration #5
sampleMean =
0.3988 0.4950 0.5365 0.4870 0.5501
overallMean =
0.4935

在编辑器中，在calcmean.m的末尾添加条件语句用来根据平均值显示不同的信息。
if overallMean < .49
disp(‘Mean is less than expected’)
elseif overallMean > .51
disp(‘Mean is greater than expected’)
else
disp(‘Mean is within the expected range’)
end

运行calcmean并验证计根据算出的平均值而正确的消息显示。例如:
overallMean =
0.5178
Mean is greater than expected
```



默认情况下，MATLAB安装程序创建的MATLAB文件夹位于搜索路径上。如果要在另一个文件夹中存储和运行程序，请将其添加到搜索路径中。在当前文件夹浏览器中选择文件夹，右键单击，然后选择“添加到路径”。



###### 帮助和文档

所有MATLAB函数都有支持文档，包括示例，并描述函数输入、输出和调用语法。有几种方法可以从命令行访问此信息：

使用***doc***命令在单独的窗口中打开函数文档。

在命令窗口中显示函数提示（函数文档的语法部分），在输入函数输入参数的打开括号后暂停。
***mean(***

使用 ***help*** 命令在命令窗口中查看函数文档的缩略文本版本。
***help mean***

### 实时脚本

您可以使用*实时脚本*中的格式设置选项来增强代码，而不是以纯文本编写代码和注释。实时脚本有助于您查看代码和输出并与之交互，还可以包含格式化文本、方程和图像。

例如，通过选择**另存为**并将文件类型更改为 MATLAB 实时代码文件 (`*.mlx`)，将 `mysphere` 转换为实时脚本。然后，用格式化文本替换代码注释。例如：

- 将注释行转换为文本。选择以百分比符号开头的每一行，然后选择**文本**、![img](https://ww2.mathworks.cn/help/matlab/learn_matlab/textbutton.png)。删除百分比符号。
- 重写文本以替换代码行末尾的注释。要将等宽字体应用于文本中的函数名，请选择 ![M](https://ww2.mathworks.cn/help/matlab/learn_matlab/monospacem.png)。要添加方程，请在**插入**选项卡上选择**方程**。

![Text and font options are in the Text section of the Live Editor tab.](D:/`Programme_tool/Typora/picture/liveeditor2.png)
