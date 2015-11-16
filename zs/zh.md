> 指针可以完成普通操作无法完成的任务，比如很典型的换值：<br/>
将两个变量传入函数swap(int x,int y)，交换值。由于C语言函数调用是以传值的方式，所以在函数中操作的值并非原调用函数中的值，而是其拷贝副本。


## 交换失败
swap.c

    void swap(int x , int y){
        int tmp;
        tmp = x;
        x=y;
        y=tmp;
    }
    
调用函数:

    swap(a,b);
    
这样调用只是把传入swap中的拷贝副本值交换了，而原来的a,b没有任何变化

![swap1](http://7xocno.com1.z0.glb.clouddn.com/swap1.png)

---
## 交换成功

### 参数指针


swap.c

    void swap(int *x,int *y){
    
        int tmp;
        tmp = *x;
        *x = *y;
        *y = tmp;
    }
    
调用函数:

    swap(&a,&b);

oK，这样就会把原来的值交换了


![swap2](http://7xocno.com1.z0.glb.clouddn.com/swap2.png)
