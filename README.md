# 2024090914022-赖伊卡-cs-05
### 任务一
1.因为浮点数在计算机内部被转换为二进制制而0.1和0.2转化为二进制后都是无限小数。而代码里面用的是float，只有23位来表示位数，显然会出现误差。

2.关于如何获取精确值，首先可以用后面问题里面提到的定点数来解决，在合适的条件下，定点数能够做到比单精度浮点数更精确。当然我也去了解了gmp.h头文件。该头文件提供了一系列用于高精度运算的函数，比如mpf_t,mpf_add,等等。通过调用该头文件下的库函数也可以实现更加准确的计算。

3.
```c
#include <stdio.h>
#include <stdlib.h>
#include <string.h>

int change(char *number) 
{
    int D = 0;
    int length = strlen(number);
    for (int i = 0; i < length - 1; i++) 
    { 
        D = D * 2 + (number[i] - '0');
    }
    return D;
}

void CHANGE(int Input, char *B) 
{
    int x= 0;
    while (Input > 0) 
    {
        B[x] = (Input % 2) + '0';
        Input = Input / 2; 
        x++;
    }
    B[x] = '\0';

    int len = strlen(B);
    for (int i = 0; i < len / 2; i++)
    {
        char x = B[i];
        B[i] = B[len - i - 1];
        B[len - i - 1] = x;
    }
}

int main() 
{
    char input[10];
    scanf("%s", input); 

    if (input[strlen(input) - 1] == 'B') 
    {
        int D = change(input);
        printf("%dD\n", D);
    } 
    else if (input[strlen(input) - 1] == 'D') 
    {
        int Input = atoi(input); 
        char B[11]; 
        CHANGE(Input, B);
        printf("%sB\n", B);
    } 
    else 
    {
        printf("错误\n");
    }

    return 0;
}
```
这里只包含了整数的进制转化，关于小数的实在没有时间了qwq。
