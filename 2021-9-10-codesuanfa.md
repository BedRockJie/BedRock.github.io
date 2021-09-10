





# 字符串转换成整数
```C++

int StrToInt(string str) {
        int num = 0;int j = 0;
        for(int i = str.size() - 1; i >= 0 ;i--){
            if(str[i] > '0' && str[i] < '9'){
                int c = (str[i] - '0');
                num += (c *  pow(10,j));   //此次使用 次方而不是乘法
                j++;
            }
            else if(str[i] == '+'){
                num = num;
            }
            else if(str[i] == '-'){
                num = -num;
            }
            else
                return 0;
        }
        return num;
    }

```