> 多维数组与指针数组的唯一区别归根到底还是（指针是变量指针，数组为常量指针）


![point-duoarr](http://7xocno.com1.z0.glb.clouddn.com/point-duoarr.png)


**当char arr[10][10];时，会为arr分配10*10的存储空间。**

**当char *parr[10];时，只会为parr分配10个指针空间。
在程序运行过程中如果parr某个元素指向了5个空间字符串，那么就为其分配5个空间，另一个元素指向了8个空间字符串，那么就为其分配8个空间。**


究其原因在于，**二维数组中:**相当于一个一维数组其元素是一个数组(每个元素长度固定)(常量指针)。<br/>
**指针数组中:**相当于一个一维数组元素是一个指针（指向的位置，元素数目不固定）（变量指针）。<br/>

即:上图中\*parr，\*(parr+9)是一个变量指针，而arr[0],arr[9]是一个常量指针

\*parr[10] = \*(parr[10]) = parr[10][] （可以看到，指针数组中，指针指向的字符长度不确定。）<br/>
上边是让指针指向了行首地址。如果这样：
parr[10][] = (\*parr)[],就相当于让指针指向了列首地址。

char[10][10] = (*char)[10]




