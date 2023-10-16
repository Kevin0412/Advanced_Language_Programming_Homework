7-1 输出学生成绩
```c++
#include<iostream>
using namespace std;

int main(){
    int n,i;
    double a,average,max=0,min=100;
    cin>>n;
    for(i=0;i<n;i++){
        cin>>a;
        average+=a/n;
        if(max<a)max=a;
        if(min>a)min=a;
    }
    printf("average = %.2f\nmax = %.2f\nmin = %.2f\n",average,max,min);
    return 0;
}
```

7-2 共用体类型应用
```c++
#include<iostream>
#include<string>
using namespace std;

int main(){
    int i,n;
    cin>>n;
    string a,b,e;
    char c,d[80];
    int w=0,t=0;
    for(i=0;i<n;i++){
        cin>>a;
        cin>>b;
        cin>>c;
        if(c=='t')t++;
        else if(c=='w')w++;
        cin>>d;
        cout<<a<<" "<<b<<" "<<c<<" "<<d;
        if(d[0]=='a'){
            cin>>e;
            cout<<" "<<e;
        }
        cout<<endl;
    }
    printf("tcount = %d, wcount = %d",t,w);
    return 0;
}
```

7-3 找商品（结构体）
```c++
#include<iostream>
using namespace std;

int main(){
    int i,n;
    cin>>n;
    struct{
        char a[80];
        double b;
        int c;
    }d,e;
    cin>>d.a>>d.b>>d.c;
    for(i=1;i<n;i++){
        cin>>e.a>>e.b>>e.c;
        if(e.c>d.c){
            d=e;
        }
        else if(e.c==d.c&&e.b>d.b){
            d=e;
        }
    }
    printf("%s %.2lf %d",d.a,d.b,d.c);
    return 0;
}
```

7-4 竞赛淘汰
```c++
#include<iostream>
using namespace std;

int main(){
    int n,i,j,k;
    double r;
    cin>>n>>r;
    struct{
        int a;
        double b;
        int c;
        double d;
        int e;
    }f[n];
    for(i=0;i<n;i++){
        f[i].a=i+1;
        cin>>f[i].b>>f[i].c;
        f[i].d=f[i].b/f[i].c;
        k=0;
        for(j=0;j<i;j++){
            if(f[i].d>f[j].d)k++;
            else f[j].e+=1;
        }
        f[i].e=k;
    }
    for(j=0;j<n;j++){
        if(f[j].e==0){
            printf("%d %.0lf %d %.2lf\n",f[j].a,f[j].b,f[j].c,f[j].d);
            break;
        }
    }
    for(i=1;i<n*r;i++){
        for(j=0;j<n;j++){
            if(f[j].e==i){
                printf("%d %.0lf %d %.2lf\n",f[j].a,f[j].b,f[j].c,f[j].d);
                break;
            }
        }
    }
    return 0;
}
//最后一个点没过
```
