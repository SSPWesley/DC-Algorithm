2021-8 CSG-TEST Online Judge 1050： A*B高精度乘法 - 解题报告（钟承文）
# 内容 #
## 题目大意 ##
计算A*B的值并输出。
## 解题思路 ##
由于A和B的位数不超过2000位。因此选用string类型来输入该字符串,将其从个位开始乘起即可，注意一下进位就可以了。
## 代码 ##
```C++
#define _CRT_SECURE_NO_WARNINGS
#include<iostream>
#include<cstring>
using namespace std;
int a[2010];
int b[2010];
int c[10000];

int main()
{
    string s1, s2;
    cin >> s1 >> s2;//输入两个字符串
    for (int i = 0; i < s1.size(); i++)
        a[i + 1] = s1[s1.size() - 1 - i] - '0';
    for (int i = 0; i < s2.size(); i++)
        b[i + 1] = s2[s2.size() - 1 - i] - '0';
    for (int i = 1; i <= s1.size(); i++)
    {
        for (int j = 1; j <= s2.size(); j++)
        {
            //进行乘法，并进行进位操作
            c[i + j - 1] += a[i] * b[j];
            c[i + j] += c[i + j - 1] / 10;
            c[i + j - 1] %= 10;
        }
    }
    int len = s1.size() + s2.size();
    //判断有几位
    while (c[len] == 0 && len > 1)
        len--;
    for (int i = len; i >= 1; i--)
    {
        cout << c[i];
    }
    return 0;
}
```




