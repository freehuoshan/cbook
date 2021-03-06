## 指针与数组的本质
---

> 从本质上来说，指针即数组，数组即指针。唯一的区别是，指针是一个变量其值可以改变，而数组名这个指针一旦定义就不可再改变

pointaddr.c

    #include <stdio.h>
    
    main()
    {
            int num=2015;
            int *p = &num;
            int arr[] = {1,2,3,4,5,6};
    
            printf("address:%x,num:%d\n",&num,num);
            printf("p:%x,*p:%d\n",p,*p);
            printf("p+1:%x\n",p+1);
            printf("p[0]:%d,&p[0]:%x\n",p[0],&p[0]);
            printf("p[1]:%d,&p[1]:%x\n",p[1],&p[1]);
            printf("p[2]:%d,&p[2]:%x\n",p[2],&p[2]);
            printf("p[-1]:%d,&p[-1]:%x\n",p[-1],&p[-1]);
            printf("arr[0]:%d,&arr[0]:%x\n",arr[0],&arr[0]);
            printf("arr[-1]:%d,&arr[-1]:%x\n",arr[-1],&arr[-1]);
            printf("arr[-2]:%d,&arr[-2]:%x\n",arr[-2],&arr[-2]);
            printf("arr[7]:%d,&arr[7]:%x\n",arr[7],&arr[7]);
            printf("%d\n",*&num);
    }

输出结果:

```
[root@landa1 tmp]# ./a.out 
address:1e580554,num:2015
p:1e580554,*p:2015
p+1:1e580558
p[0]:2015,&p[0]:1e580554
p[1]:509085012,&p[1]:1e580558
p[2]:32767,&p[2]:1e58055c
p[-1]:0,&p[-1]:1e580550
arr[0]:1,&arr[0]:1e580530
arr[-1]:0,&arr[-1]:1e58052c
arr[-2]:4195880,&arr[-2]:1e580528
arr[7]:0,&arr[7]:1e58054c
2015
```

### 以上代码已经能够充分说明问题:<br/>
> **指针:**是一个存储内存地址编码的变量。以指针变量p为例:p[5]表示指针p向右移动五个步长后该位置存储的值，也可以通过\*(p+5)表示，其实p[5]最终的计算也是转换为\*(p+5)计算，计算过程是这样的:p+5得到内存编码地址，再使用*运算符取得该位置存储的值<br/>


>**数组:**是一种特殊的指针，其值不可改变，数组名便是这个指针名。

###*可以说指针是变量指针，数组是常量指针*

---

## 图解

<center>[看大图](http://7xocno.com1.z0.glb.clouddn.com/2015-11-16%2022%3A44%3A47屏幕截图.png)

![pointaddr](http://7xocno.com1.z0.glb.clouddn.com/2015-11-16%2022%3A44%3A47屏幕截图.png)

