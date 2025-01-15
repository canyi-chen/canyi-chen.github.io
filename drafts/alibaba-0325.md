@def title = "阿里巴巴笔试记录（3月25日）"
@def date = "03/25/2022"
@def tags = ["meta", "julia"]

# 阿里巴巴笔试记录（3月25日）




## 算法题

### 第一题：验证账户是否错误

### 第二题：牛牛学减法


* 题目：牛牛今年上幼儿园了，老师叫他学习减法。老师给了他五个数字，他每次操作可以选择其中的四个数字减一，减一之后的数字不能小于零——因为幼儿园的牛牛还没有接触过负数。
现在牛牛想知道，自己最多可以进行多少次这样的操作？
* 输入:
```
2
5 4 3 2 1
1 1 1 10000 1
```
* 输出:
```
3
1
```
* 代码
* Python
```python
T = int(input())
def check(nums, x):
    s = 0
    for i in range(5):
        if nums[i] < x:
            # at least x - nums[i] cannot be minus
            s += x - nums[i]
    if s > x:
        return False
    return True
for _ in range(T):
    nums = list(map(int, input().split()))
    l, r = 0, int(1.3e9)

    while l<r:
        # binary search
        mid = (l + r + 1) // 2
        # print((l, mid, r))
        if check(nums, mid):
            l = mid
        else:
            r = mid - 1

    print(l)
```

* Java
```java
import java.util.*;
public class Main{
    public static void main(String args[]){
        Scanner in = new Scanner(System.in);
        int t = in.nextInt();
        for (int i = 0; i < t; i++){
            int[] data = new int[5];
            for (int j = 0; j < 5; j++){
                data[j] = in.nextInt();
            }
            System.out.println(maxTime(data));
        }
    }
     
    public static long maxTime(int[] data) {
        int n = 4;
        var tot = 0L;
        for (var b : data) {
            tot += b;
        }
        var l = 0L;
        var r = tot / n;
        while (l < r) {
            var x = (l + r + 1) / 2;
            var sum = 0L;
            for (var b : data) {
                sum += Math.min(b, x);
            }
            if (n * x <= sum) {
                l = x;
            } else {
                r = x - 1;
            }
        }
        return l;
    }
 
}
```

### 计算N条直线所有可能的交点个数

## 单选 
linux命令  SQL  排序算法 等等

## 多选 

页面置换算法 银行家算法  HTTP 哈夫曼树 树 网络



```
时间：9.-10.30
题型：5单选，5多选，3编程
单选多选：linux、mysql基础、数据结构
哈夫曼编码、排序算法、计算冲突域和广播域数目
编程：
第一道：判断字符串是否合法，有重复判断
第二道：5个正整数找4个大于0的数各减1，求可执行减法运算的最大次数
第三道：计算N条直线所有可能的交点个数
```
