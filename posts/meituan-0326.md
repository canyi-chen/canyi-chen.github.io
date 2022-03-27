@def title = "美团笔试记录（3月26日）"
@def date = "03/26/2022"
@def tags = ["meta", "julia"]


# 美团笔试记录（3月26日）

## 算法题目

1. 给出一个字符串，可以重新排列顺序，问所有的子串中abccca最多出现几次。

```python
strs = input()
dic = {
    'a': 0,
    'b': 0,
    'c': 0
}
for s in strs:
    if s in dic:
        dic[s] += 1
nums = list(dic.values())

print(min((nums[0] - 1), nums[1], int(nums[2]/3)))
```

2. 给出一个递增数组，要求找到一个点，使这个点到1号点和n号店的距离之差最小。

```python
n = int(input())
nums = list(map(int, input().split()))

median = (nums[0]/2 + nums[n - 1]/2)

tmp = [0]*n

for i in range(n):
    tmp[i] = abs(nums[i] - median)

r = min(tmp)
print(int(2*r))
```

3. 给出n个数，要求从中选任意个数，使得他们的和最大，且为7的倍数。
   
```cpp
#include<bits/stdc++.h>
using namespace std;
typedef long long ll;
const int maxn= 1e6+7 ;
const int inf = 0x3f3f3f3f;
int n , a[maxn];
int dp[maxn][10];
int main(){
    scanf("%d",&n);
    for(int i = 1; i <= n; i ++){
        scanf("%d",&a[i]);
    }
    memset(dp , -inf , sizeof(dp));
    dp[0][0] = 0;
    for(int i = 1; i <= n; i ++){
        for(int j = 0; j < 7; j ++){
            dp[i][j] = max(dp[i][j] , dp[i - 1][j]);
            dp[i][j] = max(dp[i][j] , dp[i - 1][((j - a[i]) % 7 + 7) % 7] + a[i]);
            //printf ("%d %d %d\n",i , j , dp[i][j]);
        }
 
    }
    printf ("%d\n",dp[n][0]);
}
```

4. 给出长度为n的数组，求所有长度为奇数的子段的中位数之和。
```cpp
#include<bits/stdc++.h>
using namespace std;
typedef long long ll;
const int maxn= 1e6+7 ;
const int inf = 0x3f3f3f3f;
int n , a[maxn];
priority_queue<int>q1,q2;
void init(){
    while(q1.size()) q1.pop();
    while(q2.size()) q2.pop();
}
void add(int now){
    if(q2.size() == 0){
        q2.push(-now);
        return ;
    }
    if(now >= -q2.top()){
        q2.push(-now);
        if(q2.size() > q1.size() + 1){
            int x = q2.top();
            q2.pop();
            q1.push(-x);
        }
    }
    else{
        q1.push(now);
 
        if(q1.size() > q2.size()){
            int x = q1.top();
            q1.pop();
            q2.push(-x);
        }
    }
}
int main(){
    scanf("%d",&n);
    ll ans = 0;
    for(int i = 1; i <= n; i ++){
        scanf("%d",&a[i]);
        ans += a[i];
    }
    for(int l = 1; l <= n; l ++){
        init();
        add(a[l]);
        for(int r = l + 1;r <= n; r ++){
            add(a[r]);
            if((r - l + 1) % 2){
                ans -= q2.top();
            }
        }
    }
    printf ("%lld\n",ans);
}
```

5. 有n个任务，完成每个任务需要的时间为l[i]l[i],在完成该任务前，必须先完成一些前置任务，多个任务可以同时进行，问每个任务的最早完成时间。
```cpp
#include<bits/stdc++.h>
using namespace std;
typedef long long ll;
const int maxn= 1e6+7 ;
const int inf = 0x3f3f3f3f;
int n;
int l[maxn] , now[maxn] , de[maxn],ans , vis[maxn];
vector<int> vec[maxn] , e[maxn];
void topo(){
    queue<int> que;
    for(int i = 1; i <= n; i ++){
        if(de[i] == 0){
            que.push(i);
            vis[i] = 1;
            now[i] = now[i] + l[i];
        }
    }
    while(que.size()){
        int u = que.front();
        que.pop();
        for(int i = 0; i < e[u].size(); i ++){
            int to = e[u][i];
            de[to]--;
            now[to] = max(now[to] , now[u]);
            if(de[to] == 0 && vis[to] == 0){
                que.push(to);
                vis[to] = 1;
                now[to] += l[to];
            }
        }
    }
}
int main(){
    scanf("%d",&n);
    for(int i = 1; i <= n; i ++){
        scanf("%d",&l[i]);
        int c , x;
        scanf("%d",&c);
        de[i] = c;
        for(int j = 1; j <= c; j ++){
            scanf("%d",&x);
            vec[i].push_back(x);
            e[x].push_back(i);
        }
    }
    topo();
    for(int i = 1; i <= n; i ++){
        printf ("%d ",now[i]);
    }
}
```

## 不定项选择题

* 梯度下降与最速下降