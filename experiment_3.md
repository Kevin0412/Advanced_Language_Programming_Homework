7-1 求交错序列前N项和
```c++
#include<iostream>
#include<math.h>
using namespace std;

int main(){
    float a,i,sum=0;
    cin>>a;
    for(i=1;i<=a;i++){
        sum+=i/(2*i-1)*pow(-1,i+1);
    }
    printf("%.3f",sum);
}
```

7-2 求分数序列前N项和
```c++
#include<iostream>
using namespace std;

int main(){
    int i,N;
    cin>>N;
    double a=2,b=1,sum=0;
    for(i=0;i<N;i++){
        sum+=a/b;
        a=a+b;
        b=a-b;
    }
    printf("%.2lf",sum);
}
```

7-3 最大公约数和最小公倍数
```c++
#include<iostream>
using namespace std;

int main(){
    int M,N,i,MIN;
    cin>>M>>N;
    if(M>N){
        MIN=N;
    }else{
        MIN=M;
    }
    for(i=MIN;i>0;i--){
        if(M%i==0&&N%i==0){
            printf("%d %d",i,M*N/i);
            break;
        }
    }
}
```

7-4 打印菱形图案
```c++
#include<iostream>
#include<math.h>
using namespace std;

int main(){
    int n,i,j;
    cin>>n;
    for(i=0;i<n;i++){
        for(j=0;j<abs(i-n/2);j++){
            cout<<"  ";
        }
        for(j;j<n-abs(i-n/2);j++){
            cout<<"* ";
        }
        cout<<endl;
    }
}
```

7-5 梅森数
```c++
#include<iostream>
#include<math.h>
using namespace std;

int main(){
    long n;
    cin>>n;
    if(n==1){
        printf("None");
        return 0;
    }
    for(long i=2;i<=n;i++){
        if(i==2 || i==3 || i==5 || i==7 || i==13 || i==17 || i==19){
            printf("%ld\n",(long)pow(2,i)-1);
        }
    }
}
```

7-6 到底是不是太胖了
```c++
#include<iostream>
using namespace std;

int main(){
    int N;
    float H,W;
    cin>>N;
    for(int i=0;i<N;i++){
        cin>>H>>W;
        if(W/2<=(H-100)*0.81){
            printf("You are tai shou le!\n");
        }else{
            if(W/2<(H-100)*0.99){
                printf("You are wan mei!\n");
            }else{
                printf("You are tai pang le!\n");
            }
        }
    }
}
```