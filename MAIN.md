## 初级难度

### 输入处理（重要）： HJ5.进制转换

**描述**

写出一个程序，接受一个十六进制的数，输出该数值的十进制表示。

数据范围：1≤n≤2<sup>31</sup>

输入描述：输入一个十六进制的数值字符串。

输出描述：输出该数值的十进制字符串。不同组的测试用例用\n隔开。

**示例1**

```bash

0xAA #输入

170 #输出

```

**答案**

```python

print(int(input(), 16))

# 知识点:python3 中2、8、16进制转换方法bin、oct、hex

```

### 排列组合： NC61.两数之和

**描述

给出一个整型数组 numbers 和一个目标值 target，请在数组中找出两个加起来等于目标值的数的下标，返回的下标按升序排列。

（注：**返回**的数组下标从1开始算起，保证target一定可以由数组里面2个数字相加得到）

数据范围：
$$2≤len(numbers)≤10^5,−10≤numbers_i≤10^9,0≤target≤10^9$$

要求：空间复杂度 O(n)，时间复杂度O(nlogn)

```python

class Solution:
    def twoSum(self, numbers: List[int], target: int) -> List[int]:
        tmp_dict = {}
        for i in range(len(numbers)):
            if target - numbers[i] in tmp_dict.keys():
                return [tmp_dict[target - numbers[i]] + 1, i + 1]
            tmp_dict[numbers[i]] = i
```

### 快速排序： HJ3.明明的随机数

**描述

明明生成了N个1到500之间的随机整数。请你删去其中重复的数字，即相同的数字只保留一个，把其余相同的数去掉，然后再把这些数从小到大排序，按照排好的顺序输出。

数据范围:$$1≤n≤1000$$
输入的数字大小满足:$$1≤val≤500$$
**输入描述：

第一行先输入随机整数的个数 N 。 接下来的 N 行每行输入一个整数，代表明明生成的随机数。 具体格式可以参考下面的"示例"。

**输出描述：

输出多行，表示输入数据处理后的结果

```python
N = int(input())
list_1 = []
for i in range(N):
    x = int(input())
    if x not in list_1:
        list_1.append(x)
    list_1.sort()
for i in list_1:
    print(i)
```

**哈希表： HJ10.字符个数统计**
**描述**

编写一个函数，计算字符串中含有的不同字符的个数。字符在 ASCII 码范围内( 0~127 ，包括 0 和 127 )
，换行表示结束符，不算在字符里。不在范围内的不作统计。多个相同的字符只计算一次

例如，对于字符串 abaca 而言，有 a、b、c 三种不同的字符，因此输出 3 。

数据范围： $$1≤n≤500$$
**输入描述**：

输入一行没有空格的字符串。

**输出描述：

输出 输入字符串 中范围在(0~127，包括0和127)字符的种数。

```python
print(len(set(input())))
```

### 递归： NC68.跳台阶

**描述

一只青蛙一次可以跳上1级台阶，也可以跳上2级。求该青蛙跳上一个 n 级的台阶总共有多少种跳法（先后次序不同算不同的结果。

数据范围：$$1≤n≤40$$要求：时间复杂度：O(n)，空间复杂度：O(1)
**示例1

```bash
2 # 输入
2 # 输出
# 说明：青蛙要跳上两级台阶有两种跳法，分别是：先跳一级，再跳一级或者直接跳两级。因此答案为2
```

**答案**

```python
class Solution:
    def jumpFloor(self, number: int) -> int:
        if number < 4:
            return number
        else:
            list1 = [1, 2, 3]
            for i in range(3, number):
                x = list1[i - 1] + list1[i - 2]
                list1.append(x)
            return list1[-1]
```

### HJ17.坐标移动

**描述**
开发一个坐标计算工具， A表示向左移动，D表示向右移动，W表示向上移动，S表示向下移动。从（0,0）点开始移动，从输入字符串里面读取一些坐标，并将最终输入结果输出到输出文件里面。  
***输入：***  
合法坐标为A(或者D或者W或者S)+ 数字（两位以内）
坐标之间以;分隔。
非法坐标点需要进行丢弃。如AA10; A1A; \$%$; YAD; 等。
下面是一个简单的例子如：
A10;S20;W10;D30;X;A1A;B10A11;;A10;  
***处理过程：***

```text
起点（0,0）
+   A10 = (-10,0）
+   S20 = (-10,-20)
+   W10 = (-10,-10)
+   D30 = (20,-10)
+   x = 无效
+   A1A = 无效
+   B10A11 = 无效
+  一个空不影响
+   A10 = (10,-10)
结果 (10,-10)
```

数据范围：每组输入的字符串长度满足 1≤n≤10000 ，坐标保证满足−2<sup>31</sup> ≤x, y≤2<sup>31</sup>−1 ，且数字部分仅含正数
**输入描述：**
一行字符串  
**输出描述：**
最终坐标，以逗号分隔  
**示例1**

```bash
A10;S20;W10;D30;X;A1A;B10A11;;A10; # 输入
10,-10                             # 输出
```

**答案**

```python
string = input()
str_list = string.split(';')
d = {}
for item in str_list:
    if len(item) > 1 and item[0] in list('ADSW') and item[1:].isdecimal():
        d[item[0]] = d.get(item[0], 0) + int(item[1:])
x, y = (d['D'] - d['A']), (d['W'] - d['S'])
print('%d,%d' % (x, y))
```

## HJ20.密码验证合格程序
**描述**  
密码要求:  
1.长度超过8位  
2.包括大小写字母.数字.其它符号,以上四种至少三种  
3.不能有长度大于2的包含公共元素的子串重复 （注：其他符号不含空格或换行）  
数据范围：输入的字符串长度满足 1≤n≤100  
输入描述：一组字符串。  
输出描述：如果符合要求输出：OK，否则输出NG  
**答案**
```python
while True:
    try:
        line = input()
        a = 0
        b = 0
        c = 0
        d = 0
        flag = True
        for i in line:
            if i.isdigit():
                a = 1
            elif i.islower():
                b = 1
            elif i.isupper():
                c = 1
            else:
                d = 1
        for j in range(len(line) - 3):
            if line.count(line[j:j + 3]) > 1:
                flag = False
            if len(line) > 8 and (a + b + c + d) >= 3 and flag:
                print("OK")
            else:
                print("NG")
    except:
        break
```

## \*HJ23.删除字符串中出现次数最少的字符
**描述**  
实现删除字符串中出现次数最少的字符，若出现次数最少的字符有多个，则把出现次数最少的字符都删除。输出删除这些单词后的字符串，字符串中其它字符保持原来的顺序。
数据范围：输入的字符串长度满足 1≤n≤20，保证输入的字符串中仅出现小写字母。  
输入描述：字符串只包含小写英文字母, 不考虑非法输入，输入的字符串长度小于等于20个字节。  
输出描述： 删除字符串中出现次数最少的字符后的字符串。
```python
str1 = input()
d = {}
for i in str1:
    d[i] = str1.count(i)
min = min(d.values())
for k, v in d.items():
    if v == min:
        str1 = str1.replace(k, "")
print(str1)
```
## \*HJ33.整数与 IP 地址间的转换
**描述**  
原理：ip地址的每段可以看成是一个0-255的整数，把每段拆分成一个二进制形式组合起来，然后把这个二进制数转变成
一个长整数。  
举例：一个ip地址为10.0.3.193
每段数字             相对应的二进制数  
10                   00001010  
0                    00000000  
3                    00000011  
193                  11000001
组合起来即为：00001010 00000000 00000011 11000001,转换为10进制数就是：167773121，即该IP地址转换后的数字就是它了。  
数据范围：保证输入的是合法的 IP 序列

输入描述：  
输入   
1 输入IP地址  
2 输入10进制型的IP地址

输出描述：
输出
1 输出转换成10进制的IP地址
2 输出转换后的IP地址
```python
while True:
    try:
        a=list(map(int,input().split('.')))
        b=int(input())
        c=''
        for i in a:
            s=bin(i)[2:]
            while (len(s)<8):
                s='0'+s
            c += s
        print(int(c,2))
        b=bin(b)[2:]
        while (len(b)<32):
            b= '0'+b
        print(str(int(b[0:8],2))+'.'+str(int(b[8:16],2))+'.'+str(int(b[16:24],2))+'.'+str(int(b[24:32],2)))
    except:
        break
```
## HJ101.输入整型数组和排序标识
**描述**  
输入整型数组和排序标识，对其元素按照升序或降序进行排序  
数据范围：1≤n≤1000，元素大小满足 0≤val≤100000   
输入描述：  
第一行输入数组元素个数  
第二行输入待排序的数组，每个数用空格隔开  
第三行输入一个整数0或1。0代表升序排序，1代表降序排序  
输出描述：
输出排好序的数字
```python
while True:
    try:
        a=int(input())
        b=list(map(int,input().split()))
        c=int(input())
        ans=sorted(b,reverse=c)
        res=''
        for i in ans:
            res=res+str(i)+" "
        print(res)
    except:
        break
```

## leetcode 1839 最长子字符串
**描述**  
当一个字符串满足如下条件时，我们称它是 美丽的 ：

所有 5 个英文元音字母（'a' ，'e' ，'i' ，'o' ，'u'）都必须 至少 出现一次。
这些元音字母的顺序都必须按照 字典序 升序排布（也就是说所有的 'a' 都在 'e' 前面，所有的 'e' 都在 'i' 前面，以此类推）
比方说，字符串 "aeiou" 和 "aaaaaaeiiiioou" 都是 美丽的 ，但是 "uaeio" ，"aeoiu" 和 "aaaeeeooo" 不是美丽的 。

给你一个只包含英文元音字母的字符串 word ，请你返回 word 中 最长美丽子字符串的长度 。如果不存在这样的子字符串，请返回 0 。  
**子字符串**是字符串中一个连续的字符序列。

```text
示例 1：  
输入：word = "aeiaaioaaaaeiiiiouuuooaauuaeiu"  
输出：13  
解释：最长子字符串是 "aaaaeiiiiouuu" ，长度为 13 。

示例 2：  
输入：word = "aeeeiiiioooauuuaeiou"  
输出：5  
解释：最长子字符串是 "aeiou" ，长度为 5 。

示例 3：  
输入：word = "a"  
输出：0  
解释：没有美丽子字符串，所以返回 0 。
```
**答案**
```python
class Solution:
    def longestBeautifulSubstring(self, word: str) -> int:
        if len(word) < 5: return 0
        sample = "aeiouu"
        queue = []
        mx = 0
        cnt = 0

        for i in word:
            if i == "a" and not queue:
                cnt += 1
                queue.append(i)
            elif queue:
                if len(queue) < 5 and i == sample[len(queue)]:
                    cnt += 1
                    queue.append(i)
                elif i == queue[-1]:
                    cnt += 1
                    continue
                elif i != queue[-1]:
                    if len(queue) == 5:
                        mx = max(mx, cnt)
                    queue = []
                    cnt = 0
                    if i == "a":
                        cnt+=1
                        queue.append(i)

        if len(queue) == 5:
            mx = max(mx, cnt)
        return mx
```
## HJ46 截取字符串
**描述**  
输入一个字符串和一个整数k,截取字符串前k个字符并输出  
数据范围：字符串长度满足 1≤n≤1000，1≤k≤n 
输入描述：  
1.输入待截取的字符串  
2.输入一个正整数k，代表截取的长度

输出描述：  
截取后的字符串  
**答案** 
```python
print(input()[0:int(input())])
```

## NC149 字符串匹配KMP算法
**描述**
给你一个文本串T，一个非空模板串S，问S在T中出现了多少次  
数据范围：  
1≤len(S)≤500000,1≤len(T)≤1000000  
要求：空间复杂度 O(len(S))，时间复杂度O(len(S)+len(T))  
```text
示例1
输入："ababab","abababab"
返回值：2

示例2
输入："abab","abacabab"
返回值：1
```
**答案**
```python
class Solution:
    def kmp(self , S , T ):
        ns=len(S)
        nt=len(T)
        n=0
        for i in range(nt-ns+1):
            if S[0]==T[i]:
                k=T[i:i+ns]
                if S==k:
                    n+=1
        return n
```
## NC100 字符串转换成整数
**描述**
写一个函数 StrToInt，实现把字符串转换成整数这个功能。不能使用 atoi 或者其他类似的库函数。传入的字符串可能有以下部分组成:  
1. 若干空格
2. (可选)一个符号字符（'+' 或 '-')  
3. 数字，字母，符号，空格组成的字符串表达式
4. 若干空格

转换算法如下:  
```text
1.去掉无用的前导空格   
2.第一个非空字符为+或者-号时，作为该整数的正负号，如果没有符号，默认为正数  
3.判断整数的有效部分：  
    3.1 确定符号位之后，与之后面尽可能多的连续数字组合起来成为有效整数数字，如果没有有效的整数部分，那么直接返回0  
    3.2 将字符串前面的整数部分取出，后面可能会存在存在多余的字符(字母，符号，空格等)，这些字符可以被忽略，它们对于函数不应该造成影响  
    3.3  整数超过 32 位有符号整数范围 [−231,  231 − 1] ，需要截断这个整数，使其保持在这个范围内。具体来说，小于−231的整数应该被调整为−231，大于231−1的整数应该被调整为231−1  
4.去掉无用的后导空格
```
数据范围:  
1.0 <=字符串长度<= 100  
2.字符串由英文字母（大写和小写）、数字（0-9）、' '、'+'、'-' 和 '.' 组成
```text
示例1  
输入："82"
返回值：82

示例2
输入："   -12  "
返回值：-12
说明：去掉前后的空格，为-12  

示例3
输入："4396 clearlove"
返回值：4396
说明：6后面的字符不属于有效的整数部分，去除，但是返回前面提取的有效部分

示例4
输入："clearlove 4396"
返回值：0

示例5
输入："-987654321111"
返回值：-2147483648
```
**答案**
```python
class Solution:
    def StrToInt(self , s: str) -> int:
        s = s.strip()
        if not s:
            return 0
        sign = -1 if s[0]=='-' else 1
        if s[0]=='-' or s[0] == '+':
            s = s[1:]
        num = 0
        for i in s:
            if i.isdigit():
                num *= 10
                num += ord(i) - 48
            else:
                break
        return min(max(sign*num,-2**31),2**31-1)
```
## HJ70 矩阵乘法计算量估算
**描述**
矩阵乘法的运算量与矩阵乘法的顺序强相关。  
例如：
A是一个50×10的矩阵，B是10×20的矩阵，C是20×5的矩阵  
计算A*B*C有两种顺序：((AB)C)或者(A(BC))，前者需要计算15000次乘法，后者只需要3500次。  
编写程序计算不同的计算顺序需要进行的乘法次数。  
数据范围：矩阵个数1≤n≤15, 行列数:1≤row<sub>i</sub>，col<sub>i</sub>≤100**保证给出的字符串表示的计算顺序唯一**。  
进阶：时间复杂度：O(n) ，空间复杂度：O(n)  
**输入描述：**  
输入多行，先输入要计算乘法的矩阵个数n，每个矩阵的行数，列数，总共2n的数，最后输入要计算的法则  
计算的法则为一个字符串，仅由左右括号和大写字母（'A'~'Z'）组成，保证括号是匹配的且输入合法！
**输出描述：**
输出需要进行的乘法次数  
**示例子1**
```text
输入：3
     50 10
     10 20
     20 5
     (A(BC))
输出：3500
```
**答案**
```python
while True:
    try:
        n = int(input())
        arr = []
        order = []
        res = 0
        for i in range(n):
            arr.append(list(map(int, input().split())))
        f = input()
        for i in f:
            if i.isalpha():
                order.append(arr[ord(i) - 65])
            elif i == ')' and len(order) >= 2:
                a = order.pop()
                b = order.pop()
                res += b[0] * b[1] * a[1]
                order.append([b[0], a[1]])
        print(res)
    except:
        break
```
## 合并表记录
**描述**
数据表记录包含表索引index和数值value（int范围的正整数），请对表索引相同的记录进行合并，即将相同索引的数值进行求和运算，输出按照index值升序进行输出。  

提示:  
0 <= index <= 11111111  
1 <= value <= 100000

**输入描述：**  
先输入键值对的个数n（1 <= n <= 500）  
接下来n行每行输入成对的index和value值，以空格隔开

**输出描述：**  
输出合并后的键值对（多行）

```text
输入:4
    0 1
    0 2
    1 2
    3 4
    
输出:0 3
    1 2
    3 4
```
**答案**
```python
b = {}
for i in range(int(input())):
    contents = input().split(" ")
    key, value = int(contents[0]), int(contents[1])
    b[key] = b[key] + value if key in b.keys() else value
for key in sorted(b.keys(),reverse=False):
    print(key,b[key])
```
## *HJ14.字符串排序
**描述**
给定n个字符串，请对n个字符串按照字典序排列。  
数据范围： 1≤n≤1000，字符串长度满足 1≤len≤100   
**输入描述**  
输入第一行为一个正整数n(1≤n≤1000),下面n行为n个字符串(字符串长度≤100),字符串中只含有大小写字母。  
**输出描述**  
数据输出n行，输出结果为按照字典序排列的字符串。
```text
输入:9
    cap
    to
    cat
    card
    two
    too
    up
    boat
    boot
输出:
    boat
    boot
    cap
    card
    cat
    to
    too
    two
    up
```
**答案**  
```python
l=list()
for i in range(int(input())):
    l.append(input())
l.sort(key=str)
for i in l:
    print(i)
```
## HJ27.查找兄弟单词
**描述**  
定义一个单词的“兄弟单词”为：交换该单词字母顺序（注：可以交换任意次），而不添加、删除、修改原有的字母就能生成的单词。  
兄弟单词要求和原来的单词不同。例如： ab 和 ba 是兄弟单词。 ab 和 ab 则不是兄弟单词。  
现在给定你 n 个单词，另外再给你一个单词 x ，让你寻找 x 的兄弟单词里，按字典序排列后的第 k 个单词是什么？  
**注意：** 字典中可能有重复单词。  

**数据范围：**  
1≤n≤1000,输入的字符串长度满足 1≤len(str)≤10,1≤k<n   
输入描述：  
输入只有一行。 先输入字典中单词的个数n，再输入n个单词作为字典单词。 然后输入一个单词x 最后后输入一个整数k  
输出描述：  
第一行输出查找到x的兄弟单词的个数m 第二行输出查找到的按照字典顺序排序后的第k个兄弟单词，没有符合第k个的话则不用输出。  
**示例：**
```bash
输入：3 abc bca cab abc 1
输出：2
     bca
```
**答案**  
```python
while True:
    try:
        ss=input().split()
        n=int(ss[0])
        dict=ss[1:n+1]
        s=ss[-2]
        m=int(ss[-1])
        a=[]
        for i in dict:
            if len(i)==len(s) and i!=s and sorted(i)==sorted(s):
                a.append(i)
        print(len(a))
        if a and m<=len(a):
            print(sorted(a)[m-1])
    except:
        break
```
## *NC37.合并区间
**描述**  
给出一组区间，请合并所有重叠的区间。
请保证合并后的区间按区间起点升序排列。

数据范围：区间组数 0≤n≤2×10<sup>5</sup>，区间内的值都满足 0≤val≤2×10<sup>5</sup>  
要求：空间复杂度O(n)，时间复杂度O(nlogn)  
进阶：空间复杂度O(val)，时间复杂度O(val)
**示例1**
```text
输入:       [[10,30],[20,60],[80,100],[150,180]]
返回值:     [[10,60],[80,100],[150,180]]
```
**答案**
```python
class Solution:
    def merge(self , intervals: List[Interval]) -> List[Interval]:
        if not intervals:
            return []
        intervals.sort(key = lambda x :x.start)
        res = [intervals[0]]
         
        for i in intervals[1:]:
            if i.start > res[-1].end:
                res.append(i)
            elif i.end >= res[-1].end:
                res[-1].end = i.end
        return res
```
## *HJ68.成绩排序
**描述** 
给定一些同学的信息（名字，成绩）序列，请你将他们的信息按照成绩从高到低或从低到高的排列,相同成绩  

都按先录入排列在前的规则处理。  

例示：  
jack      70  
peter     96  
Tom       70  
smith     67  

从高到低  成绩  
peter     96  
jack      70  
Tom       70  
smith     67  

从低到高  

smith     67  

jack      70  

Tom       70  
peter     96  

注：0代表从高到低，1代表从低到高  

数据范围：人数：1≤n≤200 
进阶：时间复杂度：O(nlogn) ，空间复杂度：O(n)  
**输入描述：**  
第一行输入要排序的人的个数n，第二行输入一个整数表示排序的方式，之后n行分别输入他们的名字和成绩，以一个空格隔开

**输出描述：**  
按照指定方式输出名字和成绩，名字和成绩之间以一个空格隔开
**示例**
```bash
输入：3
     0
     fang 90
     yang 50
     ning 70
输出：fang 90
     ning 70
     yang 50
```
**答案** 
```python
while True:
    try:
        num = int(input())
        flag = False if int(input().strip()) == 1 else True
        out = []
        for i in range(num):
            info = input().split()
            out.append((info[0],int(info[1])))
        for j in sorted(out,key=lambda x:x[1],reverse=flag):
            print(j[0],j[1])
        
        
    except:
        break
```
