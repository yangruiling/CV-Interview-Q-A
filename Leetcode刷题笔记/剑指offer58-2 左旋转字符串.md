# 剑指offer58-2. 左旋转字符串

Created: February 18, 2023 9:44 AM
Tags: 字符串, 简单

字符串的左旋转操作是把字符串前面的若干个字符转移到字符串的尾部。请定义一个函数实现字符串左旋转操作的功能。比如，输入字符串"abcdefg"和数字2，该函数将返回左旋转两位得到的结果"cdefgab"。
链接：[https://leetcode.cn/problems/zuo-xuan-zhuan-zi-fu-chuan-lcof](https://leetcode.cn/problems/zuo-xuan-zhuan-zi-fu-chuan-lcof)

解题思路1-开辟额外的空间：

1. 创建一个长度为n的vector存储待转移的n个字符
2. 前移尾部的所有字符
3. 将待转移的字符移动到尾部

```cpp
string reverseLeftWords(string s, int n) {
        //创建一个长度为n的辅助数组用于存储
        vector<char> temp(n);
        int i = 0;
        for(; i<s.size(); i++){
            if(i < n){
                temp[i] = s[i];
            }else{
                s[i-n] = s[i];
            }
        }
        i = i-n;
        for(int j =0; j < temp.size(); j++){
            s[i] = temp[j];
            i++;
        }
        return s;
    }
```

解题思路2-在原字符串上操作，采用局部反转+整体反转的思路：

1. 反转区间为前n的子串
2. 反转区间为n到末尾的子串
3. 反转整个字符串

```cpp
string reverseLeftWords(string s, int n) {
        reverse(s.begin(), s.begin() + n);
        reverse(s.begin() + n, s.end());
        reverse(s.begin(), s.end());
        return s;
}
```