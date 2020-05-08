# Instruction<br>
计算机组成原理指令集系统设计<br>
变量说明：<br>
==
1、
--
    原来的操作数寄存器
    static char MDR1[MAX_M];//操作数寄存器
    static char MDR2[MAX_M];//操作数寄存器
    变为
    static char MDR[2][MAX_M];//操作数寄存器
    二维数组的形式，这一点是为了寻址函数中赋值方便
2、
--
    新增数组static int address[2];存放操作数地址的十进制数数值，
    方便完成运算后将结果写入主存，比如直接Memory[address[1]]=结果

函数说明：
====
1、
--
    int Transform_1(char ch[], int length) //二进制串转十进制数值
    参数char ch[]为存放二进制串的数组，length为数组长度，返回值为十进制数值
2、
--
    void Transform_2(int number, char ch[], int length)//十进制数转化为二进制串
    number为要转化的十进制数数值，char ch[]为转化的二进制串要存入的字符数组，length为字符数组char ch[]的长度
3、
--
    void Addressing(int distinguish)//寻址函数
    参数distinguish的说明，若为操作数1寻址，则distinguish=1，若为操作数2寻址，则distinguish=2，这一点是和变量说明1相对应，
    若没有这些操作，计算得到的地址存放到MDR1还是MDR2将无法确定
##斐波那契数列思想：
==
    MOV M1 立即寻址 1 M1=32
    MOV M2 立即寻址 1     M2=33
    MOV X1 M1                  X1=64
    MOV X2 M2                  X2=65
    MOV X3 M3                  X3=66
    MOV X4 0                     X4=67
    ADD 间接寻址 X1 间接寻址 X3
    ADD 间接寻址 X2 间接寻址 X3
    INC X1
    INC X2
    INC X3
    INC X4
    JZ 立即寻址 X4  10 跳回
    OUT
