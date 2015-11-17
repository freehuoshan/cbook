## 字符串常量


> 本质上来说，字符串常量就是一个字符数组，没有任何不同。而数组的本质就是指针，所以完全可以使用指针的方式操作字符串常量


### 详述

** 字符串常量的尾部都有一个空字符'\0',如"hello world\n"，其真实长度要比引号中的长度大一个字节**


** 如: printf("hello world\n");**


**向printf函数传入了一个字符串常量,而本质上是传入了一个指向"hello world\n"这个字符串常量首地址的一个指针，只不过这个指针名是匿名的。printf在打印时会移动指针打印出内容直到遇到字符'\0'停止打印。**

## 注意


> char arrmess[] = "hello world";<br/>
char *pmess = "hello world";

这两各语句是有很大差别的：


可以这样说: arrmess是一个数组，pmess是一个指针。那么可以说arrmess是一个常量指针，pmess是一个变量指针


![char-point](http://7xocno.com1.z0.glb.clouddn.com/char-point.png)


** 对于pmess = "hello world";是将匿名指针的内容拷贝到pmess中，让pmess指针指向字符串。**

** arrmess是一个常量指针，不可以改变再指向其他地址。**

** pmess是一个变量指针，可以改变再指向其他地址**







