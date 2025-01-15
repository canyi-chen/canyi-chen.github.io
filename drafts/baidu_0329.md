@def title = "百度笔试记录（3月29日）"
@def date = "03/25/2022"
@def tags = ["meta", "julia"]

## 乘法表的最大值
```
给出一个乘法表，现在有一个新的乘法表规则，输入 n 和 k， 取第 n 行中的前k个乘积反转的最大值（有点绕 直接看用例好理解一些）
例子：n = 8, k = 9 数据范围：(1 <= n, k <= 1000)
解释：第n行前k个数字的正常情况下的乘积为：
1
8, 16, 24, 32, 40, 48, 56, 64, 72
反转后的乘积
1
8, 61, 42, 23, 4, 84, 65, 46, 27
取反转后结果的最大值： 84
```

```python
def compute(n, k):
    max_ans = 0
    for i in range(1, k + 1):
        if i*n<10:
            max_ans = max(max_ans, i*n)
            continue
        s = str(i*n)
        now = int(s[::-1])
        max_ans = max(max_ans, now)
    return max_ans




n, k = list(map(int, input().split()))

print(compute(n, k))
```

## 找数对

```
给出一个t个N，实现f函数，找出符合条件数对数量, 就是说从N中找两个数（A 和 B），使得A * B == N， gcd(A,B) == 1
gcd(A, B) = 1
lcm(A, B) = A * B
例子：
输入：30
返回： 4
解释： 可以构成的数对为：(1, 30), (5, 6), (15, 2), (3, 10)
去重： 因为(1,30)数对已经有了， 就不能有(30, 1)了，后面同理
```

```python
from math import gcd, sqrt
T = int(input())



for _ in range(T):
    N = int(input())
    ans = 0
    for i in range(1, int(sqrt(N)) + 1):
        if N%i == 0 and gcd(N//i, i) == 1:
            ans += 1

    print(int(ans))
```

## 构造完美数

```
给出一个数，只包含1， 2， 3的数字称为完美数，如果当前数字不符合完美数的要求，那么返回可以构造的最大的不超过当前数字的完美数。
例子：1. 输入 213 => 返回 213
2. 输入 2244 => 返回 2233
3. 输入 3355 => 返回 3333
4. 输入 100 => 返回 33
```