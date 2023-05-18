# 剑指offer05. 替换空格

Created: February 18, 2023 9:44 AM
Tags: 双指针法, 字符串, 简单

请实现一个函数，把字符串 `s` 中的每个空格替换成"%20"。

链接：

[力扣](https://leetcode.cn/problems/ti-huan-kong-ge-lcof/)

解题思路：

1. 遍历字符串统计空格长度
2. 首先扩充数组到每个空格替换成"%20"之后的大小。
3. 然后从后向前替换空格，也就是双指针法，过程如下：i指向新长度的末尾，j指向旧长度的末尾。

```cpp
string replaceSpace(string s) {
        int count = 0; // 统计空格的个数
        int sOldSize = s.size();
        for (int i = 0; i < s.size(); i++) {
            if (s[i] == ' ') {
                count++;
            }
        }
        // 扩充字符串s的大小，也就是每个空格替换成"%20"之后的大小
        s.resize(s.size() + count * 2);
        int sNewSize = s.size();
        // 从后先前将空格替换为"%20"
        for (int i = sNewSize - 1, j = sOldSize - 1; j < i; i--, j--) {
            if (s[j] != ' ') {
                s[i] = s[j];
            } else {
                s[i] = '0';
                s[i - 1] = '2';
                s[i - 2] = '%';
                i -= 2;
            }
        }
        return s;
    }
```