@def title = "阿里巴巴笔试记录（3月25日）"
@def date = "03/25/2022"
@def tags = ["meta", "julia"]

# 阿里巴巴笔试记录（3月25日）





## 算法题
1. 验证账户是否错误
2. 第二题：牛牛学减法
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

3. 计算N条直线所有可能的交点个数

## 单选 
linux命令  SQL  排序算法 等等

## 多选 

页面置换算法 银行家算法  HTTP 哈夫曼树 树 网络




时间：9.-10.30
题型：5单选，5多选，3编程
单选多选：linux、mysql基础、数据结构
哈夫曼编码、排序算法、计算冲突域和广播域数目
编程：
第一道：判断字符串是否合法，有重复判断
第二道：5个正整数找4个大于0的数各减1，求可执行减法运算的最大次数
第三道：计算N条直线所有可能的交点个数