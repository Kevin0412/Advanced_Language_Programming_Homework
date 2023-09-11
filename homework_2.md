7-1 点与圆的位置关系
```c
#include<stdio.h>

int main(){
    int Cx,Cy,r,x,y;
    scanf("%d%d%d\n%d%d",&Cx,&Cy,&r,&x,&y);
    if((x-Cx)*(x-Cx)+(y-Cy)*(y-Cy)>r*r){
        printf("OUT\n");
    }else{
        if((x-Cx)*(x-Cx)+(y-Cy)*(y-Cy)==r*r){
            printf("ON\n");
        }else{
            printf("IN\n");
        }
    }
}
```

7-2 取款情况
```c
#include<stdio.h>

int main(){
    double a,b,c,d;
    scanf("%lf%lf%lf%lf",&a,&b,&c,&d);
    if(a!=12345 || b!=567890){
        printf("帐号或密码错误\n");
    }else{
        if(d>=c){
            printf("余额不足\n");
        }else{
            if(d>20000){
                printf("超过单次取款限额\n");
            }else{
                printf("取款成功:%.2f-%.2f=%.2f\n",c,d,c-d);
            }
        }
    }
}
```

7-3 判断输入字符类型
```c
#include<stdio.h>

int main(){
    char a;
    scanf("%c",&a);
    if(a>='A' && a<='Z'){
        printf("%c",a+'a'-'A');
    }else{
        if(a>='a' && a<='z'){
            printf("%c",a);
        }else{
            printf("Non-English Characters");
        }
    }
}
```

7-4 谁能进图书馆
```c
#include<stdio.h>

int main(){
    int a,b,c,d;
    scanf("%d%d%d%d",&a,&b,&c,&d);
    if(a<b){
        if(c>=a && d>=a){
            printf("%d-Y %d-Y\n",c,d);
            printf("huan ying ru guan");
        }else{
            if(c>=b){
                printf("%d-Y %d-Y\n",c,d);
                printf("qing 1 zhao gu hao 2");
            }else{
                if(d>=b){
                    printf("%d-Y %d-Y\n",c,d);
                    printf("qing 2 zhao gu hao 1");
                }else{
                    if(c<a && d<a){
                        printf("%d-N %d-N\n",c,d);
                        printf("zhang da zai lai ba");
                    }else{
                        if(c<a){
                            printf("%d-N %d-Y\n",c,d);
                            printf("2: huan ying ru guan");
                        }else{
                            printf("%d-Y %d-N\n",c,d);
                            printf("1: huan ying ru guan");
                        }
                    }
                }
            }
        }
    }
}
```

7-5 输入一个小写字母，输出它后面的第3个字母。比如输入的字母是'a'，则输出‘d’,输入的是‘z’,则输出'c'
```c
#include<stdio.h>

int main(){
    char a;
    scanf("%c",&a);
    a+=3;
    if(a>'z'){
        a-=26;
    }
    printf("%c",a);
}
```

7-6 【多分支-if语句之最终价格】某商场打折促销，满400减100，满800减250，满1200减400。请为收银员设计一个程序，计算优惠后的最终价格。
```c
#include<stdio.h>

int main(){
    float a;
    scanf("%f",&a);
    if(a>=1200){
        a-=400;
    }else{
        if(a>=800){
            a-=250;
        }else{
            if(a>=400){
                a-=100;
            }
        }
    }
    printf("最终价格是:%.2f",a);
}
```

7-7 判断水仙花数
```c
#include<stdio.h>

int main(){
    int a;
    scanf("%d",&a);
    if(a>99 && a<1000){
        if(a==153 || a==370 || a==371 || a==407){
            printf("%d是水仙花数",a);
        }else{
            printf("%d不是水仙花数",a);
        }
    }else{
        printf("请输入一个三位数");
    }
}
```

7-8 sdut-C语言实验-24小时制转换为12小时制
```c
#include<stdio.h>

int main(){
    int h,m;
    scanf("%d:%d",&h,&m);
    if(m<0 || m>59){
        printf("Value for minutes must be in the range 0 to 59");
    }else{
        if(h<12 && h>-1){
            if(h==0 && m==0){
                printf("12:00(midnight)");
            }else{
                if(h==0){
                    printf("12:%02d(AM)",m);
                }else{
                    printf("%02d:%02d(AM)",h,m);
                }
            }
        }else{
            if(h>11 && h<24){
                h-=12;
                if(h==0 && m==0){
                    printf("12:00(noon)");
                }else{
                    if(h==0){
                        printf("12:%02d(PM)",m);
                    }else{
                        printf("%02d:%02d(PM)",h,m);
                    }
                }
            }else{
                printf("Value for hours must be in the range 0 to 23");
            }
        }
    }
}
```

7-9 追赶问题
```c++
#include<iostream>
using namespace std;

int main(){
    double d,v1,v2,s1,s2;
    int h1,m1,m2;
    cin>>d>>v1>>v2;
    scanf("%d:%d:%lf",&h1,&m1,&s1);
    if(v1>=v2){
        printf("None");
    }else{
        double r1,r2;
        r1=s1+(double)(h1*3600+m1*60);
        r2=r1+d*3600.00/(v2-v1);
        m2=((int)r2)/60;
        s2=r2-(double)(m2*60);
        printf("%02d:%02d:%05.2lf\n",(m2/60)%24,m2%60,s2);
    }
}
```

7-10 后天
```c
#include<stdio.h>

int main(){
    int k,n,y,m,d;
    int month_day[12]={31,28,31,30,31,30,31,31,30,31,30,31};
    scanf("%d",&n);
    for(k=0;k<n;k++){
        scanf("%d-%d-%d",&y,&m,&d);
        if((y%4==0 && y%100!=0)|| y%400==0){
            month_day[1]=29;
        }else{
            month_day[1]=28;
        }
        d+=2;
        if (d>month_day[m-1]){
            d-=month_day[m-1];
            m+=1;
        }
        if(m>12){
            m=1;
            y+=1;
        }
        printf("%04d-%02d-%02d",y,m,d);
        if(k<n-1){
            printf("\n");
        }
    }
}
```

7-11 扑克牌牌点
```c
#include<stdio.h>

int main(){
    long a;
    scanf("%ld",&a);
    if(a==1){
        printf("A");
    }
    if(a>1 && a<10){
        printf("%ld",a);
    }
    if(a==10){
        printf("T");
    }
    if(a==11){
        printf("J");
    }
    if(a==12){
        printf("Q");
    }
    if(a==13){
        printf("K");
    }
    if(a<1 || a>13){
        printf("none");
    }
}
```

7-12 程序员买包子
```c++
#include<iostream>
using namespace std;

int main(){
    string X;
    int N,M,K;
    cin>>N>>X>>M>>K;
    if(K==N){
        cout<<"mei you mai "<<X<<" de";
    }else{
        if(K==M){
            cout<<"kan dao le mai "<<X<<" de";
        }else{
            cout<<"wang le zhao mai "<<X<<" de";
        }
    }
}
```

7-13 进化论
```c
#include<stdio.h>

int main(){
    int n,A,B,C;
    scanf("%d",&n);
    for(int k=0;k<n;k++){
        scanf("%d%d%d",&A,&B,&C);
        if(C==A*B){
            printf("Lv Yan\n");
        }else{
            if(C==A+B){
                printf("Tu Dou\n");
            }else{
                printf("zhe du shi sha ya!\n");
            }
        }
    }
}
```