# 各branch说明
    backup: 需要备份的文件，以及更新后的必备软件
#include<stdio.h>

#define SIGN_BIT 0x80000000
#define EXP_BIT  0x7f800000
#define TAIL_BIT 0x007fffff

// int main()
// {
//         float *aFloat;//浮点数
//         float asdf = 1.023;
//         int aFix = 0;//定点数容器
//         int tmp = 0;//浮点数容器
//         int exp = 0;//指数大小
//         int tail = 0;//尾数位容器
//         // scanf("%f",aFloat);
//         aFloat = &asdf;
//         printf("%f\n",aFloat);
//         tmp = *((int*)aFloat);//置定点数的符号位 
//         aFix = tmp & SIGN_BIT;
//         printf("%f\n",*((int*)aFloat));
//         //置定点数的整数部分
//         exp = ((tmp & EXP_BIT) >> 23) - 127;//指数值
//         tail = ((tmp & TAIL_BIT) | 0x00800000);//尾数各位 
//         aFix = aFix | ((tail >> (23-exp)) << 16);
//         printf("%x\n",aFix);
//         //置定点数的小数部分
//         aFix = aFix | ((tail & ~(0xffffffff << (23-exp))) >> (7-exp));
//         printf("%x\n",aFix);
// }



int main()
{
    // 1.5707963 0.5708
    
    float a = 0.8345;
    int result = 0;

//  1100100100001111 // 51471
//   110010010000111 // 25735
    for(int i=0; i<14; i++)
    {
        if(a*2>=1)
        {
            a=a*2-1;
            result = ((result << 1) | 1);
        }
        else
        {
            a=a*2;
            result = ((result << 1) | 0);
        }
    }
    printf("%x\n", (result));
    printf("%d\n", (result));
    printf("%x\n", (result&0x1fff));
    return 0;

}
