7-1 素数对猜想
```c++
#include<iostream>
#include<math.h>
using namespace std;

int isprime(long n){
    double a=sqrt(n);
    if(n==1){
        return 0;
    }
    for(long i=2;i<=a;i++){
        if(n%i==0){
            return 0;
        }
    }
    return 1;
}

int main(){
    int n,num=0;
    cin>>n;
    for(int i=5;i<=n;i+=2){
        if(isprime(i)&&isprime(i-2)){
            num+=1;
        }
    }
    cout<<num;
}
```

7-2 函数-斐波那契数列
```c++
#include<iostream>
using namespace std;

int main(){
    long n,a=1,b=1,c=2;
    cin>>n;
    if(n==1||n==2){
        cout<<1;
        return 0;
    }
    for(long i=3;i<=n;i++){
        c=a+b;
        a=b;
        b=c;
    }
    cout<<c;
}
```

7-3 用函数求两个整数的最大公约数和最小公倍数
```c++
#include<iostream>
#include<math.h>
using namespace std;

long gcd(long m, long n) {
    m=abs(m);
    n=abs(n);
    if(m%n==0){
        return n;
    }else{
        gcd(n,m%n);
    }
}

int main(){
    long m,n,o;
    while(cin>>m>>n){
        o=gcd(abs(m),abs(n));
        if(m>0&&n>0){
            printf("%d %d\n",o,m*n/o);
        }else{
            printf("%d %d\n",o,-abs(m*n)/o);
        }
    }
}
```

7-4 寻找孪生素数
```c++
#include<iostream>
#include<math.h>
using namespace std;

int isprime(long n){
    double a=sqrt(n);
    if(n<2){
        return 0;
    }
    for(long i=2;i<=a;i++){
        if(n%i==0){
            return 0;
        }
    }
    return 1;
}

int main(){
    long n;
    cin>>n;
    while(!(isprime(n+1)&&isprime(n+3))){
        n++;
    }
    printf("%d %d",n+1,n+3);
}
```

7-5 五位以内的对称素数
```c++
#include<iostream>
#include<math.h>
using namespace std;

int isprime(long n){
    double a=sqrt(n);
    if(n==1){
        return 0;
    }
    for(long i=2;i<=a;i++){
        if(n%i==0){
            return 0;
        }
    }
    return 1;
}

int is(long n){
    if(n>=100000){
        return 0;
    }
    if(!isprime(n)){
        return 0;
    }
    if(n<10){
        return 1;
    }
    if(n<100){
        if(n==11){
            return 1;
        }
        return 0;
    }
    if(n<1000){
        if(n/100==n%10){
            return 1;
        }
        return 0;
    }
    if(n<10000){
        if(n/1000==n%10&&n/10%10==n/100%10){
            return 1;
        }
        return 0;
    }
    if(n/10000==n%10&&n/1000%10==n/10%10){
        return 1;
    }
    return 0;
}

int main(){
    long n;
    while(cin>>n){
        if(is(n)){
            printf("Yes\n");
        }else{
            printf("No\n");
        }
    }
}
```

7-6 h0094. 乒乓球
```c++
#include <iostream>
#include <cstring>
using namespace std;
int win[62503]; 
int w,l;
int main(){
    char s;
     for(int i=1;cin>>s&&s!='E';i++){
          if(s=='W') win[i]=1; 
          else win[i]=2; 
    }

    for(int i=1;1;i++){
        if(win[i]==1)w++;
        if(win[i]==2)l++;
        if(win[i]==0){
            cout<<w<<":"<<l<<endl<<endl;
            break;
        }
        if(w-l>=2||l-w>=2)
        if(w>=11||l>=11){
            cout<<w<<":"<<l<<endl;
            w=0;
            l=0;
        }
    }
    w=0;
    l=0;
    for(int i=1;1;i++){
        if(win[i]==1)w++;
        if(win[i]==2)l++;
        if(win[i]==0){
            cout<<w<<":"<<l;
            break;
        }
        if(w-l>=2||l-w>=2)
        if(w>=21||l>=21){
            cout<<w<<":"<<l<<endl;
            w=0;
            l=0;
        }
    }
}
```

7-7 十进制转二进制
```c++
#include<iostream>
using namespace std;

void ToBin(int n){
    int a=1;
    while(n/a>1){
        a*=2;
    }
    while(a>=1){
        printf("%d",n/a);
        n%=a;
        a/=2;
    }
}

int main(){
    int n;
    while(cin>>n){
        ToBin(n);
        printf("\n");
    }
}
```

7-8 身份证排序
```c++
#include<iostream>
using namespace std;

int birthday(char s[18]){
    int ans=0;
    for(int i=6;i<14;i++){
        ans+=(int)(s[i]-'0');
        ans*=10;
    }
    return ans;
}

int main(){
    int n;
    cin>>n;
    char s[n][18];
    int b[n],a[n],c;
    for(int i=0;i<n;i++){
        for(int j=0;j<18;j++){
            cin>>s[i][j];
        }
        b[i]=birthday(s[i]);
        c=0;
        for(int j=0;j<i;j++){
            if(b[j]>b[i]){
                a[j]+=1;
            }else{
                c+=1;
            }
        }
        a[i]=c;
    }
    for(int i=0;i<n;i++){
        for(int j=0;j<n;j++){
            if(a[j]==i){
                for(int k=0;k<18;k++){
                    printf("%c",s[j][k]);
                }
                printf("\n");
                break;
            }
        }
    }
}
```

7-9 h0112. 跳台阶
```c++
#include<iostream>
using namespace std;

int main(){
    long n,a=1,b=1,c=2;
    cin>>n;
    n+=1;
    if(n==1||n==2){
        cout<<1;
        return 0;
    }
    for(long i=3;i<=n;i++){
        c=a+b;
        a=b;
        b=c;
    }
    cout<<c;
}
```

7-10 完美的素数
```c++
#include<iostream>
#include<math.h>
using namespace std;

int isprime(long n){
    double a=sqrt(n);
    if(n<2){
        return 0;
    }
    for(long i=2;i<=a;i++){
        if(n%i==0){
            return 0;
        }
    }
    return 1;
}

int main(){
    long n,m,o;
    while(1){
        cin>>o;
        m=0;
        n=o;
        if(n==0){
            break;
        }
        if(isprime(n)){
            while(n>0){
                m+=n%10;
                n/=10;
            }
            if(isprime(m)){
                printf("%d\n",o);
            }
        }
    }
    
}
```