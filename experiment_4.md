7-1 输出全排列
```c++
#include<iostream>
using namespace std;

int jc(int n){
    int ans=1;
    for(int i=2;i<=n;i++){
        ans*=i;
    }
    return ans;
}

int main(){
    int n;
    cin>>n;
    int a[n],digit,c,b,j;
    b=jc(n);
    for(int l=0;l<b;l++){
        j=l;
        for(int i=0;i<n;i++){
            a[i]=1;
        }
        for(int i=n;i>0;i--){
            digit=j/jc(i-1)+1;
            j-=jc(i-1)*(digit-1);
            c=0;
            for(int k=0;k<n;k++){
                c+=a[k];
                if(digit==c){
                    printf("%d",k+1);
                    a[k]=0;
                    break;
                }
            }
        }
        printf("\n");
    }
    return 0;
}
```

7-2 判断素数
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
    int N;
    cin>>N;
    long p;
    for(int i=0;i<N;i++){
        cin>>p;
        if(isprime(p)){
            printf("Yes\n");
        }else{
            printf("No\n");
        }
    }
}
```

7-3 出生年
```c++
#include<iostream>
using  namespace std;

int diff_num(int year){
    int a[4]={year/1000,year%1000/100,year%100/10,year%10};
    int ans=1,add;
    for(int i=1;i<4;i++){
        add=1;
        for(int j=0;j<i;j++){
            if(a[j]==a[i]){
                add=0;
                break;
            }
        }
        ans+=add;
    }
    return ans;
}

int main(){
    int ans=0,year,n;
    cin>>year>>n;
    while(diff_num(year)!=n){
        year++;
        ans++;
    }
    if(year<10){
        printf("%d 000%d",ans,year);
    }else{
        if(year<100){
            printf("%d 00%d",ans,year);
        }else{
            if(year<1000){
                printf("%d 0%d",ans,year);
            }else{
                printf("%d %d",ans,year);
            }
        }
    }
    
    return 0;
}
```

7-4 Jack cheng的烦恼3
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
    long n,b;
    cin>>n;
    if(!isprime(n)){
        printf("no");
        return 0;
    }
    b=0;
    while(n!=0){
        b+=n%10;
        n/=10;
    }
    if(isprime(b)){
        printf("yes");
        return 0;
    }
    printf("no");
    return 0;
}
```