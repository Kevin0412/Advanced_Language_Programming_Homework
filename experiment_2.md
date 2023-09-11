7-1 阶梯电价
```c
#include<stdio.h>

int main(){
    float a,c;
    scanf("%f",&a);
    if(a<0){
        printf("Invalid Value!");
    }else{
        c=a*0.53;
        if(a>50){
            c+=(a-50)*0.05;
        }
        printf("cost = %.2f",c);
    }
}
```

7-2 高速公路超速处罚
```c
#include<stdio.h>

int main(){
    float v1,v2;
    scanf("%f%f",&v1,&v2);
    if(v1/v2<1.1){
        printf("OK");
    }else{
        if(v1/v2<1.5){
            printf("Exceed %d%%. Ticket 200",(int)(v1/v2*100-100+0.5));
        }else{
            printf("Exceed %d%%. License Revoked",(int)(v1/v2*100-100+0.5));
        }
    }
}
```

7-3 出租车计价
```c
#include<stdio.h>

int main(){
    float a,b;
    scanf("%f%f",&a,&b);
    if(a<=3){
        printf("%d",10+(int)(b/5)*2);
    }else{
        if(a<=10){
            printf("%d",10+(int)((a-3)*2+0.5)+(int)(b/5)*2);
        }else{
            printf("%d",10+7*2+(int)((a-10)*3+0.5)+(int)(b/5)*2);
        }
    }
}
```

7-4 计算天数
```c
#include<stdio.h>

int main(){
    int y,m,d,ds;
    int md[12]={31,28,31,30,31,30,31,31,30,31,30,31};
    scanf("%d/%d/%d",&y,&m,&d);
    ds=d;
    if(y%4==0 &&(y%100!=0 || y%400==0)){
        md[1]=29;
    }
    for(int n=0;n<m-1;n++){
        ds+=md[n];
    }
    printf("%d",ds);
}
```

7-5 计算个人所得税
```c
#include<stdio.h>

int main(){
    float a;
    scanf("%f",&a);
    if(a<=1600){
        printf("0.00");
    }else{
        if(a<=2500){
            printf("%.2f",(a-1600)*0.05);
        }else{
            if(a<=3500){
                printf("%.2f",(a-1600)*0.1);
            }else{
                if(a<=4500){
                    printf("%.2f",(a-1600)*0.15);
                }else{
                    printf("%.2f",(a-1600)*0.2);
                }
            }
        }
    }
}
```

7-6 三天打鱼两天晒网
```c
#include<stdio.h>

int main(){
    int a;
    scanf("%d",&a);
    if(a%5==0||a%5==4){
        printf("Drying in day %d",a);
    }else{
        printf("Fishing in day %d",a);
    }
}
```

7-7 稳赢
```c++
#include<iostream>
using namespace std;

int main(){
    int K,n=0;
    string a;
    cin>>K;
    while(1){
        n++;
        cin>>a;
        if(a=="End"){
            break;
        }
        if(n%(K+1)==0){
            cout<<a<<endl;
        }else{
            if(a=="ChuiZi"){
                cout<<"Bu"<<endl;
            }else{
                if(a=="JianDao"){
                    cout<<"ChuiZi"<<endl;
                }else{
                    cout<<"JianDao"<<endl;
                }
            }
        }
    }
}
```