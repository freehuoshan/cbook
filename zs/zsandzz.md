## 指针数组


![point-addr](http://7xocno.com1.z0.glb.clouddn.com/point-addr.png)







    #include <stdio.h>
    #include <string.h>
    
    #define MAXLINES 5000                                   /* 打印行数峰值 */
    char *lineptr[MAXLINES];                                /* 指针数组，元素指向每行首地址 */
    
    int readlines(char *lineptr[], int nlines);
    void writelines(char *lineptr[], int nlines);
    void qsort(char *lineptr[], int left, int right);
    
    //对输入行排序
    main()
    {
        int nlines;                                         /* 输入的行数 */
        if ((nlines = readlines(lineptr, MAXLINES)) >= 0) {
            qsort(lineptr, 0, nlines - 1);
            writelines(lineptr, nlines);
            return 0;
        } else {
            printf("error: input too big to sort\n");
            return 1;
        }
    }
    
    #define MAXLEN 1000                                     /* 每行长度峰值 */
    
    int getline(char *, int);
    char *alloc(int);
    
    /* 读取输入的字符，返回行数 */
    int readlines(char *lineptr[], int maxlines)        
    {
        int len, nlines;                                    /* len:每行长度，nlines:行数 */
        char *p, line[MAXLEN];
        nlines = 0;
        while ((len = getline(line, MAXLEN)) > 0){          /* 将字符串读取到line数组，然后让指针数组元素指向line数组首地址
            if (nlines >= maxlines || p = alloc(len) == NULL)
                return 1;
            else {
    //          line[len - 1]= '\0';       /* delete newline */
                strcpy(p, line);
                lineptr[nlines++] = p;
            }
        }
        return nlines;
    }
    
    /* 打印输入所有行 */
    void writelines(char *lineptr[], int nlines)
    {
        int i;
        for (i = 0; i < nlines; i++)
        printf("%s\n", lineptr[i]);
    }
    
    
    /* 读写输入到s字符中，返回字符数组长度 */
    int getline(char s[],int lim)
    {
        int c, i;
        for (i=0; i < lim1 && (c=getchar())!=EOF && c!='\n'; ++i)
            s[i] = c;
        if (c == '\n') {
            s[i] = c;
            ++i;
        }
        s[i] = '\0';
        return i;
    }
    
     /* 分配空间后，返回分配空间的起始位置指针 */
    char *alloc(int n) 
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