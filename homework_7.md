7-1 时间换算
```c++
#include<iostream>
using namespace std;

int main(){
    int h,m,s,n;
    scanf("%d:%d:%d\n%d",&h,&m,&s,&n);
    s+=n;
    m+=s/60;
    h+=m/60;
    s%=60;
    m%=60;
    h%=24;
    printf("%02d:%02d:%02d",h,m,s);
    return 0;
}
```

7-2 通讯录排序
```c++
#include<iostream>
using namespace std;

int main(){
    struct fd{
        char name[11];
        int birth;
        char tel[18];
    };
    int n,i;
    cin>>n;
    struct fd friends[n];
    for(i=0;i<n;i++){
        cin>>friends[i].name>>friends[i].birth>>friends[i].tel;
    }
    int a[n],min,mini=0,j;
    for(i=0;i<n;i++)a[i]=1;
    for(j=0;j<n;j++){
        min=21000000;
        for(i=0;i<n;i++){
            if(a[i]){
                if(min>friends[i].birth){
                    min=friends[i].birth;
                    mini=i;
                }
            }
        }
        a[mini]=0;
        printf("%s %d %s\n",friends[mini].name,friends[mini].birth,friends[mini].tel);
    }
    return 0;
}
```

7-3 找出总分最高的学生
```c++
#include<iostream>
using namespace std;

int main(){
    int i,n,max=0,maxi=0;
    cin>>n;
    struct {
        char a[6];
        char b[10];
        int c;
        int d;
        int e;
    } f[n];
    for(i=0;i<n;i++){
        cin>>f[i].a>>f[i].b>>f[i].c>>f[i].d>>f[i].e;
        if(max<f[i].c+f[i].d+f[i].e){
            max=f[i].c+f[i].d+f[i].e;
            maxi=i;
        }
    }
    printf("%s %s %d",f[maxi].b,f[maxi].a,max);
    return 0;
}
```

7-4 有理数均值
```c++
#include<iostream>
#include<math.h>
using namespace std;

struct R{
    int a;
    int b;
};

int gcd(int a,int b){
    if(a==0||b==0)return 1;
    a=abs(a);
    b=abs(b);
    if(a<b){
        int c=b;
        b=a;
        a=c;
    }
    if(a%b==0)return b;
    else return gcd(b,a%b);
}

struct R add(struct R a,struct R b){
    struct R ans;
    ans.b=a.b*b.b;
    ans.a=a.a*b.b+b.a*a.b;
    int c=gcd(ans.a,ans.b);
    ans.a/=c;
    ans.b/=c;
    return ans;
}

int main(){
    int n,i;
    scanf("%d",&n);
    struct R ans,a;
    ans.a=0;
    ans.b=1;
    for(i=0;i<n;i++){
        scanf("%d/%d",&a.a,&a.b);
        a.b*=n;
        ans=add(ans,a);
    }
    if(ans.a==0){
        puts("0");
        return 0;
    }
    if(abs(ans.b)==1){
        cout<<ans.a*ans.b;
        return 0;
    }
    if((ans.a>0&&ans.b>0)||(ans.a<0&&ans.b<0)){
        printf("%d/%d",abs(ans.a),abs(ans.b));
        return 0;
    }
    printf("-%d/%d",abs(ans.a),abs(ans.b));
    return 0;
}
```

7-5 一帮一
```c++
#include<iostream>
using namespace std;

int main(){
    int i,n;
    cin>>n;
    struct{
        int a;
        char b[9];
        int c;
    }a[n];
    for(i=0;i<n;i++){
        cin>>a[i].a>>a[i].b;
        a[i].c=1;
    }
    int j=0,k;
    for(i=0;i<n/2;i++){
        if(a[j].c)
        for(k=n-1;k>j;k--){
            if(a[k].c)
            if(a[k].a!=a[j].a){
                printf("%s %s\n",a[j].b,a[k].b);
                a[k].c=0;
                a[j].c=0;
                break;
            }
        }
        j++;
    }
    return 0;
}
```

7-6 考试座位号
```c++
#include<iostream>
using namespace std;

int main(){
    int i,n;
    cin>>n;
    struct{
        char a[17];
        int b;
        int c;
    }a[n];
    for(i=0;i<n;i++){
        cin>>a[i].a>>a[i].b>>a[i].c;
    }
    int m,k,j;
    cin>>m;
    for(i=0;i<m;i++){
        cin>>k;
        for(j=0;j<n;j++){
            if(a[j].b==k){
                printf("%s %d\n",a[j].a,a[j].c);
                break;
            }
        }
    }
    return 0;
}
```

7-7 共用体类型应用
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

7-8 CPA招新Ⅱ
```c++
#include<iostream>
using namespace std;

int main(){
    int a[4]={0,0,0,0},b[4],c[4]={0,3,1,2},i,j,k;
    char e;
    while(cin>>e){
        if(e=='A')a[0]+=1;
        else if(e=='B')a[1]+=1;
        else if(e=='C')a[2]+=1;
        else if(e=='D')a[3]+=1;
    }
    for(i=0;i<4;i++){
        k=0;
        for(j=0;j<i;j++){
            if(a[i]<a[j])b[j]++;
            else if(a[i]==a[j]&&c[i]>c[j])b[j]++;
            else k++;
        }
        b[i]=k;
    }
    for(i=3;i>=0;i--){
        for(j=0;j<4;j++){
            if(b[j]==i){
                if(j==0)printf("Competition department %d people!\n",a[0]);
                else if(j==2)printf("Office %d people!\n",a[2]);
                else if(j==3)printf("Organization Department %d people!\n",a[3]);
                else if(j==1)printf("Propaganda Department %d people!\n",a[1]);
            }
        }
    }
    return 0;
}
```

7-9 足球联赛排名
```c++
#include<bits/stdc++.h>
using namespace std;

struct team{
    int score;
    int win;
    int lose;
};
bool f(struct team a,struct team b){
    if(a.score<b.score){
        return true;
    }else if(a.score==b.score){
        if(a.win-a.lose<b.win-b.lose){
            return true;
        }else if(a.win-a.lose==b.win-b.lose&&a.win<b.win){
            return true;
        }
    }
    return false;
}
int main(){
    struct team a[1000];
    int t;
    cin>>t;
    for(int i=0;i<t;i++){
        memset(a,0,sizeof(a));
        int n;
        cin>>n;
        for(int i=0;i<n*(n-1)/2;i++){
            int x,y,z,w;
            cin>>x>>y>>z>>w;
            if(z>w){
                a[x].score+=3;
            }else if(z<w){
                a[y].score+=3;
            }else{
                a[x].score++;
                a[y].score++;
            }
            a[x].win+=z;
            a[y].lose+=z;
            a[y].win+=w;
            a[x].lose+=w;
        }
        int b[1000];
        for(int j=0;j<n;j++){
            b[j]=j+1;
        }
        for(int j=n-2;j>=0;j--){
            for(int l=0;l<=j;l++){
                if(f(a[b[l]],a[b[l+1]])){
                    int x=b[l];
                    b[l]=b[l+1];
                    b[l+1]=x;
                }
            }
        }
        for(int j=0;j<n;j++){
            if(j!=0){
                cout<<' ';
            }
            cout<<b[j];
        }
        cout<<endl;
    }
    return 0;
}
```