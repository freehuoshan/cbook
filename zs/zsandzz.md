## 指针数组


![point-addr](http://7xocno.com1.z0.glb.clouddn.com/point-addr.png)





## 代码


> 以下代码是一个输入字符，然后根据每行排序，最后输出的程序，里边几乎涉及了C语言指针的所有细节

    #include <stdio.h>
    #include <string.h>
    
    #define MAXLINES 3                                   	/* 打印行数峰值 */
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
    
    int getline2(char *, int);
    char *alloc(int);
    
    /* 读取输入的字符，返回行数 */
    int readlines(char *lineptr[], int maxlines)
    {
        int len, nlines;                                    /* len:每行长度，nlines:行数 */
        char *p, line[MAXLEN];
        nlines = 0;
        while ((len = getline2(line, MAXLEN)) > 0){
            if (nlines >= maxlines || (p = alloc(len)) == NULL)
                return 1;
            else {
    //          line[len - 1]= '\0';       /* delete newline */
                strcpy(p, line);							/* 将字符数组内容拷贝到p指向的地址 */
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
    int getline2(char *s,int lim)
    {
        int c, i;
        for (i=0; i < lim - 1 && (c=getchar())!=EOF && c!='\n'; ++i)
            s[i] = c;
        if (c == '\n') {
            s[i] = c;
            ++i;
        }
        s[i] = '\0';
        return i;
    }
    
    #define ALLOCSIZE 10000             /* 给予空间总大小 */
    static char allocbuf[ALLOCSIZE];    /* 将总空间抽象为一个数组，实质还是一个指针 */
    static char *allocp = allocbuf;     /* 闲置空间起始指针allocp，初始化为数组起始位置 */
    
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
    
    /* qsort: sort v[left]...v[right] into increasing order */
    void qsort(char *v[], int left, int right)
    {
    	int i, last;
    	void swap(char *v[], int i, int j);
    	if (left >= right) /* do nothing if array contains */
    	return;
    	/* fewer than two elements */
    	swap(v, left, (left + right)/2);
    	last = left;
    	for (i = left+1; i <= right; i++)
    		if (strcmp(v[i], v[left]) < 0)
    			swap(v, ++last, i);
    	swap(v, left, last);
    	qsort(v, left, last-1);
    	qsort(v, last+1, right);
    }
    
    
    /* swap: interchange v[i] and v[j] */
    void swap(char *v[], int i, int j)
    {
    	char *temp;
    	temp = v[i];
    	v[i] = v[j];
    	v[j] = temp;
    }
