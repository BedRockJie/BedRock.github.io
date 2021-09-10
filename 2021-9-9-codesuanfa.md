---
layout: post
title:  "2021-9-9 算法 "
date:   2021-09-09 9:05
categories: code
tags: code 
excerpt: 今天的算法练习
---

# 和为S的连续正数序列
三种方法，暴力、前缀和、滑动窗口

```
//前缀和方法  从当前位置向后加  如果满足条件就 遍历 这个区间
    vector<vector<int> > FindContinuousSequence(int sum) {
        vector<vector<int>> result;
        int temp =  0;
        for(int i = 1; i <= sum/2 ; i++){
            for(int j =  i; j < sum ; j++){
                temp += j;
                if(sum == temp){
                    vector<int> ans;
                    for( int k = i; k <= j ;k++) ans.push_back(k);
                    result.push_back(ans);
                }
                else if(temp > sum){
                    temp = 0;
                    break;
                }
            }
        }
        return result;
    }
```

# 和为S的两个数字  
因为题目给定的是有序数列 查找两个可以使用双指针
```
 vector<int> FindNumbersWithSum(vector<int> array,int sum) {
        vector<int> result;
        map<int,int> map;
        pair<int,int> srand;
        int temp;
        int min_temp = INT_MAX;
        for(int i:array){
            temp = sum - i;
            if(map[temp]){ //小于就更新
                if(temp * i < min_temp)
                    //result.push_back(temp);result.push_back(i);
                    srand = {temp,i};
            }
            else map[i]++;
        }
        if(srand.first == srand.second  && srand.first == 0) return vector<int>();
        result.push_back(srand.first);
        result.push_back(srand.second);
        return result;
    }

```

# 左旋字符串
```
string LeftRotateString(string str, int n) {
        if(n>str.size()) return str;
        return str.substr(n) + str.substr(0,n);
    }
```

# 反转单词序列
```
    string ReverseSentence(string str) {
        if(str.empty()) return str;
        int i = 0;  int strlong = str.size();
        while(i < strlong && str[i] == ' ') ++i;
        if(i == strlong) return str;
        string ret = "";
        string tmp = "";
        bool hasstr = false;
        for(int i = strlong - 1 ; i >= 0 ; --i){
            if(str[i] != ' '){g
                tmp = str[i] + tmp;
                hasstr = true;
            }
            else if(str[i] == ' ' && hasstr){
                ret = ret + tmp + " ";
                tmp = "";
                hasstr = false;
            }
        }
        if(tmp != "")
            ret += tmp;
        return ret;
    }
```


# JZ45 扑克牌顺子
```
    bool IsContinuous( vector<int> numbers ) {
        sort(numbers.begin(),numbers.end());
        int zero_num = 0;
        int i = 0;
        int max_min = 0;
        while(numbers[i] == 0) {zero_num ++; i++;}
        for(;i < numbers.size() - 1;i ++){
            if(numbers[i] == numbers[i+1]) return false;
            max_min += numbers[i+1]-numbers[i] - 1 ;
        }
        if(zero_num >= max_min) return true;
        return false;
    }
```


# 孩子们的游戏
```
    int LastRemaining_Solution(int n, int m) {
        if(n == 0) return -1;
        int child = n;
        list<int> child_num;
        for(int i = 0 ; i < n ; i++){  //创建一个链表
            child_num.push_back(i);
        }
        int index = 0;
        while(n > 1){
            index = (index + m - 1) % n ;
            auto it = child_num.begin();
            std::advance(it,index);
            child_num.erase(it);
            --n;
        }
        return child_num.back();
    }

    //递归 解法
    int f(int n, int m )
    {
        if(n == 1)return 0;
        int x = f(n-1 ,m);
        return (x+m) % n;
    }
    int LastRemaining_Solution(int n, int m) {
        if(n <= 0) return -1;
        return f(n,m);
    }
```

# 求和 不用运算符 不用循环 不用 。。

```
    int Sum_Solution(int n) {
        n && (n += Sum_Solution(n-1));
        return n;
    }

```

# 不使用加减乘除 做加法
```
    int Add(int num1, int num2) {
        while(num2 != 0){
            int c = ((unsigned int)(num1 & num2)) << 1;
            num1 ^= num2;
            num2 = c;
        }
        return num1;

    无进位就是安慰异或的结果，有进位就是与 结果左移一位
```


