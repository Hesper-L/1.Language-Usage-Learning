

# matlab学习语句

#### 输入、输出语句

- **输入语句**

	- 输入数值

		```matlab
		>> x = input('please input a number:')
		please input a number:
		
		>> 22
		x = 22
		```

	- 输入字符串

		```matlab
		>> x = input('please input a string:','s')
		please input a string:
		
		>> this is a string
		x = this is a string
		```

		

- **输出语句**

	<font size=4 color="blue">输出显示命令</font>

	自由格式**disp**

	```matlab
	>>disp(23+454-29*4)
	361
	
	>>disp([11 22 33; 44 55 66; 77 88 99])
	11 22 33
	44 55 66
	77 88 99
	
	>>disp('this is a string')
	this is a string
	```

	格式化输出**fprintf**

	```matlab
	>>fprintf('The area is %8.5\n,area')
	The area is 12.56637 % 输出值为8位数含5位小数
	```

	

	<font size=4 color="blue">错误消息显示命令</font>

	```matlab
	>>error('this is an error')
	this is an error
	```

	