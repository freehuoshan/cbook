> **有效的指针运算：**包括相同类型指针之间的赋值运算；指针同整数之间的加减运算；指向相同数组中元素的指针之间减法或比较运算；将指针赋值为0或指针与0之间的比较运算；其他所有形式的指针运算都属于非法的。


## 分配内存，释放内存


    #define ALLOCSIZE 10000             /* 给予空间总大小 */
    static char allocbuf[ALLOCSIZE];    /* 将总空间抽象为一个数组，实质还是一个指针 */
    static char *allocp = allocbuf;     /* 闲置空间起始指针allocp，初始化为数组起始位置 */
    char *alloc(int n)                  /* 分配空间后，返回分配空间的起始位置指针 */
    {
        if (allocbuf + ALLOCSIZE - allocp>= n)
        { 
            allocp += n;
            return allocp-n;
        }
        else
        {
            return 0;
        }
    }
    void afree(char *p)                 /* 释放空间，实质只是移动闲置空间起始位置指针 */
    {
        if (p >= allocbuf && p < allocbuf + ALLOCSIZE)
        allocp = p;
    }

![内存分配](http://7xocno.com1.z0.glb.clouddn.com/address-yunsuan.png)


    