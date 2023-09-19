# zhiwen_suo
宿舍自制指纹锁【开源】V1.0 <br>
V2.1 增加了蓝牙，看门狗，提高系统稳定性<br>
## 原理图：<br>
![这是图片](/image/1.jpg "yaunlitu")
![这是图片](/image/2.jpg "yaunlitu")
![这是图片](/image/3.jpg "yaunlitu")
1. AS608指纹 <br>之前一开始看到B站一个UP主用到Hlink家的指纹模块性价比高又LED灯比较炫酷，但是相比较这个不太好上手，所以只能后续升级
   
2. 舵机MG995：带得动门
3. HC-05蓝牙模块
4. 18650电池
5. 0.91寸oled屏幕
### IO口 分配
~~~
/******************* 按键 *******************/
PB 15    KEY 1                                                                      
PA 8      KEY 2                     
PB 5      KEY 3
PB 4      KEY 4
/******************* oled屏幕 *******************/ 
PB6     SCL
PB7     SDA
/******************* 蜂鸣器 *******************/ 
PA4     BEEP
/******************* 蓝牙 *******************/ 
PA9     USART1_Tx --> BlueTooth_Rx
PA10   USART1_Rx --> BlueTooth_Tx
/******************* 指纹 *******************/ 
PB10  USART3_Tx    --> Rx
PB11  USART3_Rx    --> Tx
PA1    读入指纹模块的高电平		WAKE
PB9 V_finger_control   ---- control指纹模块供电

/******************* 舵机 *******************/

PB0 --- TIM3_CH3 --- PWM
PA7 --- V servo in    --- control 开关
/******************* 电池电量 *******************/ 

PA5 ---ADC12_IN5

DMA初始化 要在ADC 之前
~~~


