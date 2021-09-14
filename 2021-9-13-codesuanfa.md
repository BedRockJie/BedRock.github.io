# 验证IP地址 
可能出现的错误有：
IPV6：
- 多了0
- 出现了 ::
- 字符不在 0-9 a-f A-F 之间
IPV4：
- 首位多了0
- 超过0-255范围
- 出现 ..



 无法解决 ipv6 0000 的问题 

```C++
class Solution {
public:
string solve(string IP) {
  // 根据标识符确定此IP的类型
  bool isIPv4 = false;
  bool isIPv6 = false;

  for (auto & ch : IP) {
      if(ch == '.') isIPv4 = true;
      if(ch == ':') isIPv6 = true;
  }

  if(isIPv4 == isIPv6) return "Neither";
  else if(isIPv4) return checkIPv4(IP);
  return checkIPv6(IP);
}

// 检查IPv4地址的正确性
string checkIPv4(string& IP) {
  int n = IP.size(), count = 0;
  // 首先确保每个'.'前后都是数字且点的个数必须为3个
  for (int i = 0; i < n; i++) {
      // 检查是否有字母
      if (isalpha(IP[i])) return "Neither";
      if (IP[i] == '.') {
          count++;
          // 位于边界
          if (i == 0 || i == n - 1) return "Neither";

          // 前后有非数字
          if (!isdigit(IP[i - 1]) || !isdigit(IP[i + 1])) return "Neither"; 
      }
      else {
          // 前导零
          if(i + 1 < n && IP[i] == '0' && isdigit(IP[i + 1])) return "Neither";

          // 取出十进制数
          int j = i, digit = 0;    
          while (j < n && isdigit(IP[j])) {
              digit = digit * 10 + (IP[j] - '0');
              j++;
          }
          if(digit < 0 || digit > 255) return "Neither";
          i = j - 1;
      }
  }
  return count == 3 ? "IPv4" : "Neither";
}

// 检查IPv6地址的正确性
string checkIPv6(string& IP) {
  int n = IP.size(), count = 0;
  // 同样确保每个':'前后都有字母且个数为7个
  for (int i = 0; i < n; i++) {
      if (IP[i] == ':') {
          count++;
          // 位于边界
          if (i == 0 || i == n - 1) return "Neither";
          // 前后都无':'
          if (IP[i - 1] == ':' || IP[i + 1] == ':') return "Neither";
      }
      else {
          // 检查位数和字符串合法性
          int j = i, cnt = 0;
          while(j < n && IP[j] != ':') {
              cnt++;    // 位数加一
              if(!isdigit(IP[j]) && tolower(IP[j]) > 'f') return "Neither";
              j++;
          }
          if (cnt > 4) return "Neither";
          i = j - 1;
      }
  }
  return count == 7 ? "IPv6" : "Neither";
}
};

```

### 参考别人的代码
```C++
class Solution {
public:
string solve(string IP) {
  // 根据标识符确定此IP的类型
  bool isIPv4 = false;
  bool isIPv6 = false;

  for (auto & ch : IP) {
      if(ch == '.') isIPv4 = true;
      if(ch == ':') isIPv6 = true;
  }

  if(isIPv4 == isIPv6) return "Neither";
  else if(isIPv4) return checkIPv4(IP);
  return checkIPv6(IP);
}

// 检查IPv4地址的正确性
string checkIPv4(string& IP) {
  int n = IP.size(), count = 0;
  // 首先确保每个'.'前后都是数字且点的个数必须为3个
  for (int i = 0; i < n; i++) {
      // 检查是否有字母
      if (isalpha(IP[i])) return "Neither";
      if (IP[i] == '.') {
          count++;
          // 位于边界
          if (i == 0 || i == n - 1) return "Neither";

          // 前后有非数字
          if (!isdigit(IP[i - 1]) || !isdigit(IP[i + 1])) return "Neither"; 
      }
      else {
          // 前导零
          if(i + 1 < n && IP[i] == '0' && isdigit(IP[i + 1])) return "Neither";

          // 取出十进制数
          int j = i, digit = 0;    
          while (j < n && isdigit(IP[j])) {
              digit = digit * 10 + (IP[j] - '0');
              j++;
          }
          if(digit < 0 || digit > 255) return "Neither";
          i = j - 1;
      }
  }
  return count == 3 ? "IPv4" : "Neither";
}

// 检查IPv6地址的正确性
string checkIPv6(string& IP) {
  int n = IP.size(), count = 0;
  // 同样确保每个':'前后都有字母且个数为7个
  for (int i = 0; i < n; i++) {
      if (IP[i] == ':') {
          count++;
          // 位于边界
          if (i == 0 || i == n - 1) return "Neither";
          // 前后都无':'
          if (IP[i - 1] == ':' || IP[i + 1] == ':') return "Neither";
      }
      else {
          // 检查位数和字符串合法性
          int j = i, cnt = 0;
          while(j < n && IP[j] != ':') {
              cnt++;    // 位数加一
              if(!isdigit(IP[j]) && tolower(IP[j]) > 'f') return "Neither";
              j++;
          }
          if (cnt > 4) return "Neither";
          i = j - 1;
      }
  }
  return count == 7 ? "IPv6" : "Neither";
}
};
```
