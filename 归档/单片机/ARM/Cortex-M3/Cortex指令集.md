ARM Cortex-M3 不支持全部ARM指令集，支持的指令集包括
- ARMv6的大部分16位Thumb指令集
- ARMv7的Thumb-2指令集

# 数据传送类指令

## 寄存器到寄存器传送
```ARM
;指令
MOV R8,R3; R8 = R3
MVN R8,R3; R8 = -R3

;伪指令
ADR Rd, label; 将PC+label得到的地址写进目标寄存器
```


## 寄存器与存储器间传送数据
- 存储器到寄存器传送：
	- LDRx指令
	- LDMxy指令
- 寄存器到存储器传送：
	- STRx指令
	- STMxy指令

- LDR和STR中x可以是
	- B——Byte
	- H——half word
	- D——double word
	- 略——word
	- 支持前后索引，参看[[ARM寻址方式]]

- LDM和STM中
	- x可以为I或D
	- y可以为A或B
	- .W后缀表示这条指令是32位的Thumb-2指令，否则是16位的指令


## 组合式传送数据

堆栈操作指令
```
POP,PUSH
```

Cortex-M3默认采用==满递减堆栈==方式

*参看[[ARM堆栈操作多地址]]*

```
PUSH{cond} reglist
POP{cond} reglist
```


```
PUSH {R0-R3, LR} 等效于 STMDB SP!, {R0-R3,LR}
POP {R0-R3, PC} 等效于 LTMIA SP!, {R0-R3,PC} 
```

- STMFA 等价于 STMIB
- STMEA 等价于 STMIA

## 立即数的加载

MOV支持8位立即数加载：
```ARM
MOV R0, #0x12
```

MOVW指令将立即数加载到寄存器的低16位，清零高16位；
MOVT指令将立即数加载到寄存器的高16位。


## 特殊功能寄存器只能用MSR/MRS指令访问
```ARM
MRS <gp_reg>,<special_reg>;读特殊功能寄存器的值到通用寄存器
MSR <special_reg>,<gp_reg>;读通用寄存器的值到特殊功能寄存器
```

`大多数的特殊功能寄存器都只能在特权级下访问，非特权级下只能访问APSR`


# 数据处理指令
## 四则运算指令

- ADD
- SUB
- ADC（级联）
- SBC（级联）
- 反向减法指令RSB

- CMP 后面的第一个操作数减去第二个操作数，并影响APSR寄存器

- MUL
- UDIV/SDIV

## 逻辑运算指令
## 字节序反转指令


# 其他计算类指令


# 饱和运算


# 跳转指令
- B Label：跳转到Label处对应的地址，无条件跳转指令；
- BX reg：跳转到由寄存器reg给出的地址，无条件跳转指令;
	- Rm的bit[0]必须是1，但跳转地址在创建时会把bit[0]置为0。
- BL Label：跳转到Label对应的地址，并且把跳转前的下条指令地址保存到LR；
- BLX reg


- 只有B指令可以在IT块内外自由使用条件码；
- 其他分支指令只能在IT块内使用条件码。


# 标志位与条件转移指令
## ![[ASPR]]

# 对内存的互斥访问
![[互斥访问指令]]

