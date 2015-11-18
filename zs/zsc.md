> 根据数组索引n返回指向字符串的指针。



    char *month_name(int n)
    {
        static char *name[] = {
            "Illegal month",
            "January", "February", "March",
            "April", "May", "June",
            "July", "August", "September",
            "October", "November", "December"
        };
        return name[n];
    }
    
    
** 数组name中实质上存放的是指向每个字符串首地址的指针，所以根据索引n返回对应name的元素就是指向字符串的指针。**