7-1 计算正五边形的面积和周长
```c++
#include<iostream>
#include<math.h>
using namespace std;

int main(){
    float a;
    cin>>a;
    cout<<a*a*sqrt(25+10*sqrt(5))/4<<endl;
    cout<<5.0*a<<endl;
}
```

7-2 问候
```c++
#include<iostream>
using namespace std;

int main(){
    string name;
    cout<<"Hello!What's your name?"<<endl;
    cin>>name;
    cout<<name<<",Welcome to learn OOP using C++!"<<endl;
}
```

7-3 北邮VC++实验题1 输出日期
```c
#include<stdio.h>

int main(){
    int y,m,d;
    scanf("%d%d%d",&y,&m,&d);
    printf("%d年%d月%d日",y,m,d);
}
```

7-4 英文字母 - C/C++ 变量及简单数据类型
```c
#include<stdio.h>

int main(){
    char a;
    int b;
    scanf("%c\n%d",&a,&b);
    printf("%d\n%c",a-64,b+64);
}
```

7-5 游客检票 - C/C++ 变量及简单数据类型
```c
#include<stdio.h>

int main(){
    float A,B,C,m,n;
    scanf("%f\n%f",&m,&n);
    B=(6*n-8*m)/(n-m);
    A=(8-B)*m;
    C=A/(10-B);
    printf("Original number of visitors: %.1f\n",A);
    printf("New arriavlas per minute: %.1f\n",B);
    printf("Check time when 10 gates are opened: %.1f",C);
}
```

7-6 菲姐游泳 - C/C++ 语法基础
```c
#include<stdio.h>

int main(){
    int a,b,c,d;
    scanf("%d%d%d%d",&a,&b,&c,&d);
    if(b<d){
        printf("%d:%d",c-a,d-b);
    }else{
        printf("%d:%d",c-a-1,d-b+60);
    }
}
```

7-7 最短跑道长度 - C/C++ 语法基础
```c
#include<stdio.h>

int main(){
    float v,a;
    scanf("%f\n%f",&v,&a);
    printf("The shortest length of run  way: %.2f",v*v/2/a);
}
```