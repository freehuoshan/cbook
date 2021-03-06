> 在C语言中，二维数组实际上是一个特殊的一维数组，相当于一个一维数组中每个元素是一个一维数组。因为数组就是一个指针，所以本质上说，二维数据就是一个指针数组。


![duo-arr](http://7xocno.com1.z0.glb.clouddn.com/duo-arr1.png)


** 此时data[0]即\*data是指向第一行的指针，存放第一行起始地址,(\*data)[1]即data[0][1]是第一行第二列值<br/>
data[1]即\*(data+1)是指向第二行的指针，存放第二行起始地址，(\*(data+1))[1]即data[1][1]是第二行第二列的值**


## 代码

> day_of_year：将某年某月某日，转换为某年第几天<br/>
month_day:将某年第几天，转换为某年某月某日


    static char daytab[2][13] = {
    {0, 31, 28, 31, 30, 31, 30, 31, 31, 30, 31, 30, 31},
    {0, 31, 29, 31, 30, 31, 30, 31, 31, 30, 31, 30, 31}
    };
    
    /* day_of_year: 将某年某月某日，转换为某年第几天 */
    int day_of_year(int year, int month, int day)
    {
        int i, leap;
        leap = year%4 == 0 && year%100 != 0 || year%400 == 0;
        for (i = 1; i < month; i++)
            day += daytab[leap][i];
        return day;
    }
    /* month_day: 将某年第几天，转换为某年某月某日 */
    void month_day(int year, int yearday, int *pmonth, int *pday)
    {
        int i, leap;
        leap = year%4 == 0 && year%100 != 0 || year%400 == 0;
        for (i = 1; yearday > daytab[leap][i]; i++)
            yearday = daytab[leap][i];
        *pmonth = i;
        *pday = yearday;
    }


## 注意

###*C语言中，多维数组除第一维可以不指定下标外，其余各维必须指定下标*


## 总结

因为数组即指针，所以数组的数组即多维数组就是指针数组；因为指针即数组，所以指针数组就是多维数组。即char *pchar[] = pchar[][]