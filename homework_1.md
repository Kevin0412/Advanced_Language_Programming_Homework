<<<<<<< HEAD
7-1 基本格式输入输出
```c
#include<stdio.h>

int main(){
    char a;
    int b;
    float c;
    scanf("%c%d%f",&a,&b,&c);
    printf("%c\n%d\n%.6f\n",a,b,c);
    return 0;
}
```

7-2 求学生考试的总分total和平均分average
```c
#include<stdio.h>

int main(){
    float a,b,c;
    scanf("%f%f%f",&a,&b,&c);
    printf("sum = %.2f; average = %.2f\n",a+b+c,(a+b+c)/3.0);
    return 0;
}
```

7-3 3-1读入一个字母，输出与之对应的ASCII 码值。
```c
#include<stdio.h>

int main(){
    char a;
    scanf("%c",&a);
    printf("%d",a);
    return 0;
}
```

7-4 printf练习：打印C语言最常见的4种数据类型关键字int float double char，关键字用空格隔开，结尾注意不输出换行。
```c
#include<stdio.h>

int main(){
    printf("int float double char");
}
```

7-5 V形图案
```c
#include<stdio.h>

int main(){
    printf("*        *\n");
    printf("**      **\n");
    printf("***    ***\n");
    printf("****  ****\n");
    printf("**********");
}
```

7-6 求圆的周长和面积
```c
#include<stdio.h>
#define pi 3.14159

int main(){
    float r;
    scanf("%f",&r);
    printf("s=%.2f\nv=%.2f",2*r*pi,r*r*pi);
    return 0;
}
```

7-7 今天我要赢
```c
#include<stdio.h>

int main(){
    printf("I\'m gonna win! Today!\n2022-04-23");
}
```

7-8 输入一个字符ch，然后输出与它前后相邻的两个字符
```c
#include<stdio.h>

int main(){
    char c;
    scanf("%c",&c);
    printf("%c%c",c-1,c+1);
}
```

7-9 求两点之间的距离。
```c
#include<stdio.h>
#include<math.h>

int main(){
    int x1,y1,x2,y2;
    scanf("%d%d%d%d",&x1,&y1,&x2,&y2);
    printf("%.2f",sqrt(pow(x1-x2,2)+pow(y1-y2,2)));
}
```

7-10 求圆的周长和面积（const）
```c
#include<stdio.h>

int main(){
    const float pi=3.14159;
    float r;
    scanf("%f",&r);
    printf("c=%.2f\ns=%.2f",2*r*pi,r*r*pi);
    return 0;
}
```

7-11 逆序的两位数
```c
#include<stdio.h>

int main(){
    char a,b;
    scanf("%c%c",&a,&b);
    if(b=='0'){
        printf("%c",a);
    }
    else{
        printf("%c%c",b,a);
    }
}
```

7-12 求两个整数的和
```c
#include<stdio.h>

int main(){
    int a,b;
    scanf("%d%d",&a,&b);
    printf("%d + %d = %d",a,b,a+b);
}
=======
7-1 基本格式输入输出
```c
#include<stdio.h>

int main(){
    char a;
    int b;
    float c;
    scanf("%c%d%f",&a,&b,&c);
    printf("%c\n%d\n%.6f\n",a,b,c);
    return 0;
}
```

7-2 求学生考试的总分total和平均分average
```c
#include<stdio.h>

int main(){
    float a,b,c;
    scanf("%f%f%f",&a,&b,&c);
    printf("sum = %.2f; average = %.2f\n",a+b+c,(a+b+c)/3.0);
    return 0;
}
```

7-3 3-1读入一个字母，输出与之对应的ASCII 码值。
```c
#include<stdio.h>

int main(){
    char a;
    scanf("%c",&a);
    printf("%d",a);
    return 0;
}
```

7-4 printf练习：打印C语言最常见的4种数据类型关键字int float double char，关键字用空格隔开，结尾注意不输出换行。
```c
#include<stdio.h>

int main(){
    printf("int float double char");
}
```

7-5 V形图案
```c
#include<stdio.h>

int main(){
    printf("*        *\n");
    printf("**      **\n");
    printf("***    ***\n");
    printf("****  ****\n");
    printf("**********");
}
```

7-6 求圆的周长和面积
```c
#include<stdio.h>
#define pi 3.14159

int main(){
    float r;
    scanf("%f",&r);
    printf("s=%.2f\nv=%.2f",2*r*pi,r*r*pi);
    return 0;
}
```

7-7 今天我要赢
```c
#include<stdio.h>

int main(){
    printf("I\'m gonna win! Today!\n2022-04-23");
}
```

7-8 输入一个字符ch，然后输出与它前后相邻的两个字符
```c
#include<stdio.h>

int main(){
    char c;
    scanf("%c",&c);
    printf("%c%c",c-1,c+1);
}
```

7-9 求两点之间的距离。
```c
#include<stdio.h>
#include<math.h>

int main(){
    int x1,y1,x2,y2;
    scanf("%d%d%d%d",&x1,&y1,&x2,&y2);
    printf("%.2f",sqrt(pow(x1-x2,2)+pow(y1-y2,2)));
}
```

7-10 求圆的周长和面积（const）
```c
#include<stdio.h>

int main(){
    const float pi=3.14159;
    float r;
    scanf("%f",&r);
    printf("c=%.2f\ns=%.2f",2*r*pi,r*r*pi);
    return 0;
}
```

7-11 逆序的两位数
```c
#include<stdio.h>

int main(){
    char a,b;
    scanf("%c%c",&a,&b);
    if(b=='0'){
        printf("%c",a);
    }
    else{
        printf("%c%c",b,a);
    }
}
```

7-12 求两个整数的和
```c
#include<stdio.h>

int main(){
    int a,b;
    scanf("%d%d",&a,&b);
    printf("%d + %d = %d",a,b,a+b);
}
>>>>>>> 6760633ed1846071f4f178f4a3bdc9af4c2b6179
```