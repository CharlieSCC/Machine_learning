# argparse 是一个命令行参数解析模块

为什么选项参数有的加一个横杠，又有的是两个横杠的情况，如“-h”与“–help”?

命令行为了简化输入，选项参数可以合并，即"ls -l -h"命令与“ls -lh”是相等的。换句话说，大于一个字母的选项参数会被分别解析。为了避免上述情况发生，多于一个字母的选项参数，使用两个横杠。

# 第一步：导包并创建对象

	使用argparse的第一步就是导入该包，并且创建一个ArgumentParser对象

  	import argparse

  	parser = argparse.ArgumentParser()

  	创建对象时，ArgumentParser该方法的参数一般只使用"description="，即

  	import argparse

  	parser = argparse.ArgumentParser(description='这个程序是做什么的')
	
# 第二步：添加自己所需命令行参数

	向已创建的对象中添加自己所需的命令行参数
	
	parser.add_argument('integers', metavar='N', type=int, nargs='+', help='an integer for the accumulator')
	
	parser.add_argument('--sum', dest='accumulate', action='store_const', const=sum, default=max, help='sum the integers (default: find the max)')
	
# 第三步：解析命令行参数

	ArgumentParser对象通过parse_args()方法解析参数。将命令行的每个参数根据第二步具体选项转换为相应的类型，然后赋值给Namespace对象并返回。
