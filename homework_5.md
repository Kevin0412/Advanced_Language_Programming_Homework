7-1 求最大值及其下标
```c++
#include<iostream>
using namespace std;

int main(){
    int a,n,max,maxi=0;
    cin>>n>>max;
    for(int i=1;i<n;i++){
        cin>>a;
        if(a>max){
            max=a;
            maxi=i;
        }
    }
    printf("%d %d",max,maxi);
    return 0;
}
```

7-2 找出不是两个数组共有的元素
```c++
#include<iostream>
using namespace std;

int main(){
    int n,m,i,j,out,space=0;
    cin>>n;
    int a[n];
    for(i=0;i<n;i++){
        cin>>a[i];
    }
    cin>>m;
    int b[m];
    for(i=0;i<m;i++){
        cin>>b[i];
    }
    for(i=0;i<n;i++){
        out=1;
        for(j=0;j<m;j++){
            if(a[i]==b[j]){
                out=0;
                break;
            }
        }
        for(j=0;j<i;j++){
            if(a[i]==a[j]){
                out=0;
                break;
            }
        }
        if(out){
            if(space){
                printf(" ");
            }else{
                space=1;
            }
            printf("%d",a[i]);
        }
    }
    for(i=0;i<m;i++){
        out=1;
        for(j=0;j<n;j++){
            if(b[i]==a[j]){
                out=0;
                break;
            }
        }
        for(j=0;j<i;j++){
            if(b[i]==b[j]){
                out=0;
                break;
            }
        }
        if(out){
            if(space){
                printf(" ");
            }else{
                space=1;
            }
            printf("%d",b[i]);
        }
    }
    return 0;
}
```

7-3 矩阵运算
```c++
#include<iostream>
using namespace std;

int main(){
    int n,i,j,sum=0,a;
    cin>>n;
    for(i=0;i<n;i++){
        for(j=0;j<n;j++){
            cin>>a;
            if(i+j!=n-1&&i!=n-1&&j!=n-1){
                sum+=a;
            }
        }
    }
    cout<<sum;
    return 0;
}
```

7-4 求一批整数中出现最多的个位数字
```c++
#include<iostream>
using namespace std;

int main(){
    long n[10],a,b,m,max=0;
    cin>>m;
    for(int i=0;i<10;i++){
        n[i]=0;
    }
    for(long i=0;i<m;i++){
        cin>>a;
        if(a==0){
            n[0]+=1;
        }
        while(a>0){
            b=a%10;
            n[b]+=1;
            a/=10;
        }
    }
    for(int i=0;i<10;i++){
        if(n[i]>max){
            max=n[i];
        }
    }
    printf("%ld:",max);
    for(int i=0;i<10;i++){
        if(n[i]==max){
            printf(" %d",i);
        }
    }
    printf("\n");
    return 0;
}
```

7-5 字符串转换成十进制整数
```c++
#include<iostream>
using namespace std;

int main(){
    char c;
    long a=0,d=1;
    int b=1;
    while(1){
        cin>>c;
        if(c=='-'&&b){
            d=-1;
        }
        else if(c<='9'&&c>='0'){
            a*=16;
            a+=(long)(c-'0');
            b=0;
        }else if(c>='a'&&c<='f'){
            a*=16;
            a+=(long)(c-'a'+10);
            b=0;
        }else if(c>='A'&&c<='F'){
            a*=16;
            a+=(long)(c-'A'+10);
            b=0;
        }else if(c=='#'){
            break;
        }
    }
    cout<<d*a;
    return 0;
}
```

7-6 数字加密
```c++
#include<iostream>
using namespace std;

int main(){
    int a,b[4];
    cin>>a;
    for(int i=0;i<4;i++){
        b[i]=(a+9)%10;
        a/=10;
    }
    printf("The encrypted number is %d%d%d%d",b[1],b[0],b[3],b[2]);
    return 0;
}
```

7-7 交换最小值和最大值
```c++
#include<iostream>
using namespace std;

int main(){
    long n,i;
    cin>>n;
    long a[n];
    for(i=0;i<n;i++){
        cin>>a[i];
    }
    long min=a[0],mini=0;
    for(i=1;i<n;i++){
        if(a[i]<min){
            min=a[i];
            mini=i;
        }
    }
    a[mini]=a[0];
    a[0]=min;
    long max=a[n-1],maxi=n-1;
    for(i=1;i<n-1;i++){
        if(a[i]>max){
            max=a[i];
            maxi=i;
        }
    }
    a[maxi]=a[n-1];
    a[n-1]=max;
    for(i=0;i<n;i++){
        printf("%ld ",a[i]);
    }
    return 0;
}
```

7-8 螺旋方阵
```c++
#include<iostream>
using namespace std;

int main(){
    int n,x=0,y=0,b=0;
    cin>>n;
    int a[n][n];
    for(int i=0;i<n;i++){
        for(int j=0;j<n;j++){
            a[i][j]=0;
        }
    }
    for(int i=1;i<=n*n;i++){
        a[x][y]=i;
        if(b==0){
            if(x==n-1||a[x+1][y]!=0){
                b+=1;
            }else x++;
        }
        if(b==1){
            if(y==n-1||a[x][y+1]!=0){
                b+=1;
            }else y++;
        }
        if(b==2){
            if(x==0||a[x-1][y]!=0){
                b+=1;
            }else x--;
        }if(b==3){
            if(a[x][y-1]!=0){
                b=0;
                x++;
            }else y--;
        }
    }
    for(int i=0;i<n;i++){
        for(int j=0;j<n;j++){
            if(a[j][i]<10){
                printf("  %d",a[j][i]);
            }else{
                printf(" %d",a[j][i]);
            }
        }
        printf("\n");
    }
    return 0;
}
```

7-9 字符串字母大小写转换
```c++
#include<iostream>
using namespace std;

int main(){
    int i=0;
    char b[80],c;
    cin.get(b,80,'\n');
    while(1){
        c=b[i];
        if(c=='#'){
            break;
        }
        else if(c>='a'&&c<='z'){
            printf("%c",c-'a'+'A');
        }else if(c>='A'&&c<='Z'){
            printf("%c",c-'A'+'a');
        }else printf("%c",c);
        i++;
    }
    return 0;
}
```

7-10 装箱问题
```c++
#include<iostream>
using namespace std;

int main(){
    int n,i,j,a,boxes=0;
    cin>>n;
    int box[n];
    for(i=0;i<n;i++){
        box[i]=100;
    }
    for(i=0;i<n;i++){
        cin>>a;
        for(j=0;j<n;j++){
            if(a<=box[j]){
                box[j]-=a;
                printf("%d %d\n",a,j+1);
                break;
            }
        }
    }
    for(i=0;i<n;i++){
        if(box[i]!=100){
            boxes++;
        }else break;
    }
    cout<<boxes;
    return 0;
}
```

7-11 IP地址转换
```c++
#include<iostream>
using namespace std;

int main(){
    char c;
    int a;
    for(int i=0;i<4;i++){
        a=0;
        for(int j=0;j<8;j++){
            cin>>c;
            a*=2;
            if(c=='1'){
                a+=1;
            }
        }
        cout<<a;
        if(i!=3) printf(".");
    }
    return 0;
}
```

7-12 猴子选大王
```c++
#include<iostream>
using namespace std;

int main(){
    int n,i=0,j=1,k=-1;
    cin>>n;
    int a[n];
    for(i=0;i<n;i++){
        a[i]=0;
    }
    i=0;
    while(1){
        if(a[i]!=3){
            a[i]=j;
            j++;
            if(j>3){
                j=1;
            }
            if(k==i){
                break;
            }else{
                k=i;
            }
        }
        i++;
        if(i>=n){
            i=0;
        }
    }
    cout<<k+1;
    return 0;
}
```

7-13 大炮打蚊子
```c++
#include<iostream>
using namespace std;

int main(){
    int m,n,i,j,k,l,x,y,d;
    char c;
    cin>>m>>n;
    int a[m][n];
    for(i=0;i<m;i++)
    for(j=0;j<n;j++){
        cin>>c;
        if(c=='#'){
            a[i][j]=2;
        }else{
            a[i][j]=-2;
        }
    }
    cin>>k;
    for(l=0;l<k;l++){
        d=0;
        cin>>x>>y;
        a[x][y]-=2;
        if(x-1>=0)a[x-1][y]-=1;
        if(y-1>=0)a[x][y-1]-=1;
        if(x+1<m)a[x+1][y]-=1;
        if(y+1<n)a[x][y+1]-=1;
        for(i=0;i<m;i++)
        for(j=0;j<n;j++){
            if(a[i][j]<=-2){
                a[i][j]=-2;
            }else if(a[i][j]<=0){
                d+=1;
                a[i][j]=-2;
            }
        }
        printf("%d\n",d);
    }
    return 0;
}
```

7-14 数组循环左移
```c++
#include<iostream>
using namespace std;

int main(){
    int m,n,i;
    cin>>m>>n;
    int a[m];
    for(i=0;i<m;i++){
        cin>>a[i];
    }
    for(i=0;i<m;i++){
        cout<<a[(i+n)%m];
        if(i<m-1){
            printf(" ");
        }
    }
    return 0;
}
```

7-15 输出小于均值的数
```c++
#include<iostream>
using namespace std;

int main(){
    long a[10],i,sum=0;
    for(i=0;i<10;i++){
        cin>>a[i];
        sum+=a[i];
    }
    for(i=0;i<10;i++){
        if(a[i]*10<sum){
            printf("%d ",a[i]);
        }
    }
    return 0;
}
```

7-16 杨辉三角
```c++
#include<iostream>
using namespace std;

int main(){
    int n,i,j;
    cin>>n;
    int a[n],b[n];
    for(i=1;i<=n;i++){
        for(j=0;j<i;j++){
            if(j==0||j==i-1)b[j]=1;
            else b[j]=a[j-1]+a[j];
        }
        for(j=0;j<i;j++){
            if(b[j]<10)printf("   %d",b[j]);
            else if(b[j]<100)printf("  %d",b[j]);
            else if(b[j]<100)printf(" %d",b[j]);
            else printf("%d",b[j]);
            a[j]=b[j];
        }
        printf("\n");
    }
    return 0;
}
```

7-17 到底有多二
```c++
#include<iostream>
using namespace std;

int main(){
    char n;
    float a=0,b=0,c=1,d=1;
    while(cin>>n){
        if(n=='-'){
            c=1.5;
            b--;
        }
        if(n=='2')a++;
        b++;
    }
    if((n-'0')%2==0){
        d=2;
    }
    printf("%.2f%%",a/b*c*d*100);
    return 0;
}
```

7-18 出租
```c++
#include<iostream>
using namespace std;

int main(){
    long long tel;
    cin>>tel;
    int t[11],i,num[10],nums=0,j=0,k=0;
    for(i=0;i<10;i++){
        num[i]=0;
    }
    for(i=0;i<11;i++){
        t[i]=tel%10;
        num[t[i]]=1;
        nums+=1;
        tel/=10;
    }
    printf("int[] arr = new int[]{");
    int arr[nums];
    for(i=9;i>=0;i--){
        if(num[i]){
            arr[j]=i;
            if(j>0)printf(",");
            printf("%d",i);
            j++;
        }
    }
    printf("};\nint[] index = new int[]{");
    for(i=10;i>=0;i--)
    for(k=0;k<j;k++){
        if(arr[k]==t[i]){
            if(i<10)printf(",");
            printf("%d",k);
            break;
        }
    }
    printf("};");
    return 0;
}
```

7-19 把一个字符串中的所有字符按从小到大排序
```c++
#include<iostream>
using namespace std;

int main(){
    char c[20],b;
    int i,j,k;
    for(i=0;i<20;i++){
        c[i]=0;
    }
    i=0;
    while(cin>>b){
        c[i]=b;
        j=i;
        while(j>0){
            if(c[j]<c[j-1]){
                c[j]=c[j-1];
                c[j-1]=b;
            }else break;
            j--;
        }
        i++;
    }
    for(k=0;k<i;k++){
        printf("%c",c[k]);
    }
    return 0;
}
```

7-20 查验身份证
```c++
#include<iostream>
using namespace std;

int main(){
    int n,i,j,p=1,q,sum,a[17]={7,9,10,5,8,4,2,1,6,3,7,9,10,5,8,4,2},b[11]={'1','0','X','9','8','7','6','5','4','3','2'};
    char c[18],d;
    cin>>n;
    cin.getline(c,19,'\n');
    for(i=0;i<n;i++){
        cin.getline(c,19,'\n');
        sum=0;
        q=1;
        for(j=0;j<17;j++){
            if(c[j]<='9'&&c[j]>='0'){
                sum+=(int)(c[j]-'0')*a[j];
            }else{
                printf("%s\n",c);
                p=0;
                q=0;
                break;
            }
        }
        if(b[sum%11]!=c[17]&&q){
            printf("%s\n",c);
            p=0;
        }
    }
    if(p)printf("All passed");
    return 0;
}
```

7-21 出生年
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

7-22 点赞
```c++
#include<iostream>
using  namespace std;

int main(){
    int i,j,k,n,m,a[1000],max=0,maxa=0;
    cin>>n;
    for(i=0;i<1000;i++){
        a[i]=0;
    }
    for(i=0;i<n;i++){
        cin>>m;
        for(j=0;j<m;j++){
            cin>>k;
            a[k-1]+=1;
        }
    }
    for(i=0;i<1000;i++){
        if(a[i]>=max){
            max=a[i];
            maxa=i;
        }
    }
    printf("%d %d",maxa+1,max);
    return 0;
}
```

7-23 矩阵A乘以B
```c++
#include<iostream>
using namespace std;

int main(){
    int i,j,Ra,Ca,Rb,Cb;
    cin>>Ra>>Ca;
    int a[Ra][Ca];
    for(i=0;i<Ra;i++)
    for(j=0;j<Ca;j++)
    cin>>a[i][j];
    cin>>Rb>>Cb;
    int b[Rb][Cb];
    for(i=0;i<Rb;i++)
    for(j=0;j<Cb;j++)
    cin>>b[i][j];
    if(Ca!=Rb){
        printf("Error: %d != %d",Ca,Rb);
        return 0;
    }else{
        int sum,k;
        printf("%d %d\n",Ra,Cb);
        for(i=0;i<Ra;i++){
            for(j=0;j<Cb;j++){
                sum=0;
                for(k=0;k<Ca;k++)sum+=a[i][k]*b[k][j];
                printf("%d",sum);
                if(j!=Cb-1)printf(" ");
            }
            printf("\n");
        }
        return 0;
    }
}
```

7-24 个位数统计
```c++
#include<iostream>
using namespace std;

int main(){
    char c;
    int a[10],i;
    for(i=0;i<10;i++)a[i]=0;
    while(cin>>c)a[c-'0']+=1;
    for(i=0;i<10;i++)if(a[i]!=0)printf("%d:%d\n",i,a[i]);
    return 0;
}
```

7-25 考试座位号
```c++
#include<iostream>
using namespace std;

int main(){
    int n;
    cin>>n;
    char a[n][17];
    int b[n],c[n],i;
    for(i=0;i<n;i++){
        cin>>a[i];
        cin>>b[i];
        cin>>c[i];
    }
    int m,d,e;
    cin>>m;
    for(i=0;i<m;i++){
        cin>>d;
        for(e=0;e<n;e++){
            if(b[e]==d){
                printf("%s %d\n",a[e],c[e]);
                break;
            }
        }
    }
    return 0;
}
```

7-26 A-B
```c++
#include<iostream>
using namespace std;

int main(){
    char a[10002],b[10002];
    int c;
    cin.getline(a,10001,'\n');
    cin.getline(b,10001,'\n');
    for(int i=0;i<10001;i++){
        if(a[i]==0)break;
        c=1;
        for(int j=0;j<10001;j++){
            if(b[j]==0)break;
            if(a[i]==b[j]){
                c=0;
                break;
            }
        }
        if(c){
            printf("%c",a[i]);
        }
    }
    return 0;
}
```

7-27 判断题
```c++
#include<iostream>
using namespace std;

int main(){
    int n,m;
    cin>>n>>m;
    int s[m],a[m],b,i,c,j;
    for(i=0;i<m;i++)cin>>s[i];
    for(i=0;i<m;i++)cin>>a[i];
    for(i=0;i<n;i++){
        b=0;
        for(j=0;j<m;j++){
            cin>>c;
            if(c==a[j])b+=s[j];
        }
        printf("%d\n",b);
    }
    return 0;
}
```

7-28 评委打分
```c++
#include<iostream>
using namespace std;

int main(){
    int a[10],i;
    for(i=0;i<10;i++)cin>>a[i];
    int n,b;
    cin>>n;
    for(i=0;i<n;i++){
        cin>>b;
        a[b-1]+=10;
    }
    for(i=0;i<10;i++){
        printf("%d",a[i]);
        if(i<9)printf(" ");
    }
    return 0;
}
```

7-29 结伴同行去秋游
```c++
#include<iostream>
using namespace std;

int main(){
    int n;
    cin>>n;
    int a[n],i;
    for(i=0;i<n;i++)cin>>a[i];
    for(i=0;i<n/2;i++)printf("%d %d\n",a[i],a[n-i-1]);
    return 0;
}
```

7-30 摘苹果
```c++
#include<iostream>
using namespace std;

int main(){
    int n;
    cin>>n;
    int a[n],i;
    for(i=0;i<n;i++)cin>>a[i];
    int b,c=0;
    cin>>b;
    for(i=0;i<n;i++)if(b+30>=a[i])c++;
    cout<<c;
    return 0;
}
```

7-31 校门外的树
```c++
#include<iostream>
using namespace std;

int main(){
    int l;
    cin>>l;
    int a[l+1],i;
    for(i=0;i<=l;i++)a[i]=1;
    int m;
    cin>>m;
    int b,c,j;
    for(i=0;i<m;i++){
        cin>>b>>c;
        for(j=b;j<=c;j++){
            a[j]=0;
        }
    }
    int d=0;
    for(i=0;i<=l;i++)if(a[i])d++;
    cout<<d;
    return 0;
}
```

7-32 PAT考试日期
```c++
#include<iostream>
using namespace std;

int main(){
    int n,q;
    cin>>n>>q;
    int b,k,i,j,a[n][100];
    for(i=0;i<n;i++)
    for(j=0;j<100;j++)
    a[i][j]=0;
    for(i=0;i<n;i++){
        cin>>k;
        for(j=0;j<k;j++){
            cin>>b;
            a[i][b-1]=1;
        }
    }
    int c;
    for(j=0;j<100;j++){
        c=0;
        for(i=0;i<n;i++)c+=a[i][j];
        if(c>=q){
            cout<<j+1;
            return 0;
        }
    }
    cout<<0;
    return 0;
}
```

7-33 超市贴花
```c++
#include<iostream>
using namespace std;

int main(){
    int n,a[1000],i,b,c=0,d;
    cin>>n;
    for(i=0;i<1000;i++){
        a[i]=0;
    }
    for(i=0;i<n;i++){
        cin>>b;
        a[b-1]+=1;
    }
    for(i=0;i<998;i++){
        d=a[i];
        if(a[i+1]<d)d=a[i+1];
        if(a[i+2]<d)d=a[i+2];
        c+=d;
        a[i]-=d;
        a[i+1]-=d;
        a[i+2]-=d;
    }
    cout<<c;
    return 0;
}
```

7-34 及格率
```c++
#include<iostream>
using namespace std;

int main(){
    float n,m=0,i,a;
    cin>>n;
    for(i=0;i<n;i++){
        cin>>a;
        if(a>=60){
            m++;
        }
    }
    if(n==0){
        printf("%.2f",n);
    }else{
        printf("%.2f",m/n);
    }
    return 0;
}
```

7-35 英美姓名(*)
```c++
#include<iostream>
using namespace std;

int main(){
    char a[31],b[31],c[31];
    cin.getline(a,30,'\n');
    cin.getline(b,30,'\n');
    cin.getline(c,30,'\n');
    int d=1,e=0;
    if(a[0]!='\0'){
        printf("%s",a);
        e=1;
        d=0;
    }
    if(b[0]!='\0'){
        if(e)printf(" ");
        printf("%s",b);
        e=1;
        d=0;
    }
    if(c[0]!='\0'){
        if(e)printf(" ");
        printf("%s",c);
        d=0;
    }
    if(d)printf("Noname");
    return 0;
}
```

7-36 猜数字
```c++
#include<iostream>
#include<math.h>
using namespace std;

int main(){
    int n,i;
    cin>>n;
    float a[n],c=0;
    char b[n][9];
    for(i=0;i<n;i++){
        cin>>b[i];
        cin>>a[i];
        c+=a[i]/n/2;
    }
    float min=abs(a[0]-c);
    int mini=0;
    for(i=1;i<n;i++){
        if(min>abs(a[i]-c)){
            min=abs(a[i]-c);
            mini=i;
        }
    }
    printf("%.0f %s",c,b[mini]);
    return 0;
}
```

7-37 求集合数据的均方差
```c++
#include<iostream>
#include<math.h>
using namespace std;

int main(){
    int n,i;
    cin>>n;
    double a[n],avg;
    for(i=0;i<n;i++){
        cin>>a[i];
        avg+=a[i]/n;
    }
    double ans=0;
    for(i=0;i<n;i++)ans+=(a[i]-avg)*(a[i]-avg)/n;
    printf("%.5lf",sqrt(ans));
    return 0;
}
```

7-38 组合数的和
```c++
#include<iostream>
using namespace std;

int main(){
    int n,a=0,c,i;
    cin>>n;
    for(i=1;i<=n;i++){
        cin>>c;
        a+=c;
    }
    cout<<a*(n-1)*11;
    return 0;
}
```

7-39 用扑克牌计算24点
```c++
#include<iostream>
using namespace std;

int main(){
    float e[4],ans,ans1;
    int i;
    for(i=0;i<4;i++)cin>>e[i];
    int d[24][4]={{0,1,2,3},
{0,1,3,2},
{0,2,1,3},
{0,2,3,1},
{0,3,1,2},
{0,3,2,1},
{1,0,2,3},
{1,0,3,2},
{1,2,0,3},
{1,2,3,0},
{1,3,0,2},
{1,3,2,0},
{2,0,1,3},
{2,0,3,1},
{2,1,0,3},
{2,1,3,0},
{2,3,0,1},
{2,3,1,0},
{3,0,1,2},
{3,0,2,1},
{3,1,0,2},
{3,1,2,0},
{3,2,0,1},
{3,2,1,0}};
    char opr[6]={'+','-','*','/','-','/'},out[8],out1[12],out2[16];
    int j,k,l,m,n[3];
    for(i=0;i<24;i++)
    for(j=0;j<4;j++)
    for(k=0;k<6;k++)
    for(l=0;l<6;l++){
        ans=e[d[i][0]];
        n[0]=j;
        n[1]=k;
        n[2]=l;
        for(m=0;m<3;m++){
            if(n[m]==0)ans+=e[d[i][m+1]];
            else if(n[m]==1)ans-=e[d[i][m+1]];
            else if(n[m]==2)ans*=e[d[i][m+1]];
            else if(n[m]==3)ans/=e[d[i][m+1]];
            else if(n[m]==4)ans=e[d[i][m+1]]-ans;
            else ans=e[d[i][m+1]]/ans;
        }
        if(ans==24){
            sprintf(out,"(%.0f%c%.0f)",e[d[i][0]],opr[j],e[d[i][1]]);
            if(k<4)sprintf(out1,"(%s%c%.0f)",out,opr[k],e[d[i][2]]);
            else sprintf(out1,"(%.0f%c%s)",e[d[i][2]],opr[k],out);
            if(l<4)sprintf(out2,"%s%c%.0f",out1,opr[l],e[d[i][3]]);
            else sprintf(out2,"%.0f%c%s",e[d[i][3]],opr[l],out1);
            printf("%s",out2);
            return 0;
        }
    }
    for(i=0;i<24;i++)
    for(j=0;j<4;j++)
    for(k=0;k<4;k++)
    for(l=0;l<4;l++){
        ans=e[d[i][0]];
        ans1=e[d[i][2]];
        if(j==0)ans+=e[d[i][1]];
        else if(j==1)ans-=e[d[i][1]];
        else if(j==2)ans*=e[d[i][1]];
        else ans/=e[d[i][1]];
        if(k==0)ans1+=e[d[i][3]];
        else if(k==1)ans1-=e[d[i][3]];
        else if(k==2)ans1*=e[d[i][3]];
        else ans1/=e[d[i][3]];
        if(l==0)ans+=ans1;
        else if(l==1)ans-=ans1;
        else if(l==2)ans*=ans1;
        else ans/=ans1;
        if(ans==24){
            printf("(%.0f%c%.0f)%c(%.0f%c%.0f)",e[d[i][0]],opr[j],e[d[i][1]],opr[l],e[d[i][2]],opr[k],e[d[i][3]]);
            return 0;
        }
    }
    printf("-1");
    return 0;
}
```

7-40 实验内容四 题目4_11
```c++
#include<iostream>
using namespace std;

int main(){
    int y,m,d=1,w,ms[12]={31,28,31,30,31,30,31,31,30,31,30,31},a,i;
    cin>>y>>m;
    if((y%4==0&&y%100!=0)||y%400==0)ms[1]=29;
    w=(d+2*m+3*(m+1)/5+y+y/4)%7;
    printf("     SUN     MON     TUE     WED     THU     FRI     SAT\n");
    for(i=0;i<w;i++)printf("        ");
    for(i;i<w+ms[m-1];i++){
        if(i-w+1<10)printf("       %d",i-w+1);
        else printf("      %d",i-w+1);
        if(i%7==6)printf("\n");
    }
    return 0;
}
```