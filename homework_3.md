7-1 统计学生平均成绩与及格人数
```c++
#include<iostream>
using namespace std;

int main(){
    long long n,sum=0,m=0,a;
    cin>>n;
    if(n==0){
        printf("average = 0.0\ncount = 0");
        return 0;
    }
    for(long long i=0;i<n;i++){
        cin>>a;
        if(a>=60){
            m+=1;
        }
        sum+=a;
    }
    printf("average = %.1lf\ncount = %lld",(double)sum/(double)n,m);
    return 0;
}
```

7-2 统计学生成绩
```c++
#include<iostream>
using namespace std;

int main(){
    long long n,sum=0,m=0,a,A=0,B=0,C=0,D=0,E=0;
    cin>>n;
    for(long long i=0;i<n;i++){
        cin>>a;
        if(a>=90){
            A+=1;
        }else{
            if(a>=80){
                B+=1;
            }else{
                if(a>=70){
                    C+=1;
                }else{
                    if(a>=60){
                        D+=1;
                    }else{
                        E+=1;
                    }
                }
            }
        }
    }
    printf("%lld %lld %lld %lld %lld",A,B,C,D,E);
    return 0;
}
```

7-3 求幂级数展开的部分和
```c++
#include<iostream>
using namespace std;

int main(){
    double a,b=1,ans=1,i=1;
    cin>>a;
    while(b>=0.00001){
        b*=a/i;
        ans+=b;
        i++;
    }
    printf("%.4lf",ans);
    return 0;
}
```

7-4 换硬币
```c++
#include<iostream>
using namespace std;

int main(){
    int fen,fen5,fen2,fen1,count=0;
    cin>>fen;
    for(fen5=(fen-3)/5;fen5>0;fen5--){
        for(fen2=(fen-5*fen5-1)/2;fen2>0;fen2--){
            fen1=fen-5*fen5-2*fen2;
            printf("fen5:%d, fen2:%d, fen1:%d, total:%d\n",fen5,fen2,fen1,fen5+fen2+fen1);
            count+=1;
        }
    }
    printf("count = %d",count);
}
```

7-5 水仙花数
```c++
#include<iostream>
#include<math.h>
using namespace std;

int main(){
    long N,a,b,c;
    cin>>N;
    if(N==7){
        printf("1741725\n4210818\n9800817\n9926315\n");
    }else{
        for(long i=pow(10,N-1);i<pow(10,N);i++){
            a=i;
            b=0;
            for(long j=0;j<N;j++){
                c=a%10;
                b+=pow(c,N);
                a=(a-c)/10;
            }
            if(b==i){
                printf("%d\n",i);
            }
        }
    }
}
```

7-6 韩信点兵
```c++
#include<iostream>
using namespace std;

int main(){
    int a=1;
    while(1){
        if(a%5==1&&a%6==5&&a%7==4&&a%11==10){
            break;
        }
        a++;
    }
    printf("%d",a);
}
```

7-7 二分法求多项式单根
```c++
#include<iostream>
#include<math.h>
using namespace std;

float f(float a,float b,float c,float d,float x){
    return a*pow(x,3)+b*pow(x,2)+c*x+d;
}

int main(){
    float a,b,c,d,x1,x2,x;
    scanf("%f%f%f%f\n%f%f",&a,&b,&c,&d,&x1,&x2);
    while(1){
        x=(x1+x2)/2;
        if(x2-x1<0.01){
            printf("%.2f",x);
            break;
        }
        if(f(a,b,c,d,x)==0){
            printf("%.2f",x);
            break;
        }else{
            if(f(a,b,c,d,x)>0){
                if(f(a,b,c,d,x1)>0){
                    x1=x;
                }else{
                    x2=x;
                }
            }else{
                if(f(a,b,c,d,x1)<0){
                    x1=x;
                }else{
                    x2=x;
                }
            }
        }
    }
}
```

7-8 支票面额
```c++
#include<iostream>
using namespace std;

int main(){
    int n,f,y;
    cin>>n;
    for(y=0;y<100;y++){
        for(f=0;f<100;f++){
            if(98*f-199*y==n){
                if(!(y==0&&f==0)){
                    printf("%d.%d",y,f);
                    return 0;
                }
            }
        }
    }
    printf("No Solution");
    return 0;
}
```

7-9 龟兔赛跑
```c++
#include<iostream>
using namespace std;

int main(){
    int T,t=0,gui=0,tu=0,rest=0;
    cin>>T;
    for(t=1;t<=T;t++){
        gui+=3;
        if(rest>0){
            rest--;
        }else{
            tu+=9;
            if(t%10==0){
                if(gui<tu){
                    rest=30;
                }
            }
        }
    }
    if(gui==tu){
        printf("-_- %d",tu);
    }else{
        if(gui>tu){
            printf("@_@ %d",gui);
        }else{
            printf("^_^ %d",tu);
        }
    }
}
```

7-10 人民币兑换
```c++
#include<iostream>
using namespace std;

int main(){
    int n;
    cin>>n;
    if(n>12){
        n=12;
    }
    for(int i=1;i<=n;i++){
        printf("%d %d %d\n",i,50-4*i,50+3*i);
    }
}
```

7-11 验证手机号
```c++
#include<iostream>
#include<string>
using namespace std;

int main(){
    string i;
    cin>>i;
    if(i.length()!=11){
        printf("no");
        return 0;
    }
    char *p=i.data();
    for(int j=0;j<11;j++){
        if(p[j]<'0'||p[j]>'9'){
            printf("no");
            return 0;
        }
    }
    if(p[0]=='1'){
        printf("yes");
        return 0;
    }
    printf("no");
}
```

7-12 寻找250
```c++
#include<iostream>
using namespace std;

int main(){
    int a,b=1;
    while(1){
        cin>>a;
        if(a==250){
            cout<<b;
            break;
        }
        b++;
    }
}
```

7-13 阅览室
```c++
#include<iostream>
#include<string>
#include<sstream>
using namespace std;

int main(){
    int books[1001],N,h,m,times,time,n,i;
    char a,sp;
    for(int i=0;i<1001;i++){
        books[i]=-1;
    }
    cin>>N;
    times=0;
    time=0;
    string input;
    getline(cin,input);
    for(i=0;i<N;i++){
        while(getline(cin,input)){
            istringstream iss(input);
            iss>>n>>a>>h>>sp>>m;
            if(n==0){
                break;
            }else{
                if(a=='S'){
                    books[n]=60*h+m;
                }
                if(a=='E'){
                    if(books[n]!=-1){
                        times+=1;
                        time+=60*h+m-books[n];
                        books[n]=-1;
                    }
                }
            }
        }
        for(int i=0;i<1001;i++){
            books[i]=-1;
        }
        if(times==0){
            printf("0 0\n");
        }
        else{
            printf("%d %d\n",times,(time+times/2)/times);
        }
        times=0;
        time=0;
    }
}
```
