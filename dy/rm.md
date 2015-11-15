## HelloWorld

> 要完成“helloworld”程序，要编写程序文本，编译，加载，运行


### 编写程序文本

*helloworld.c*
    #include <stdio.h>              //加载标准函数库
    
    main(){                         //main函数（程序入口）
        printf("hello world!\n");   //使用标准函数库中printf打印函数
    }                               //‘\n’是一个转义字符，代表换行
    

### 编译

*在UNIX类系统中,系统自带有gcc编译器*

```bash
$ gcc helloworld.c
```

直接运行上边命令，就已经将helloworld编译为a.out,此时当前路径下生成a.out


### 运行


*直接运行编译后生成的文件a.out*

```bash
$ ./a.out
hello world!
```




    