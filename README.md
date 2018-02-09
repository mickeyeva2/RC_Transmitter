# 这是一个基于ATMEL AVR单片机的Arduino 2.4GHz和红外遥控发射
## 特性:
- 支持乐高红外遥控动力组件和MECCANO遥控火车
- 适用于遥控车及直升机等2.4GHz遥控发射
- 四个模拟输入轴, 两个模式切换开关（玩具摇杆自带按钮）
- 一个电位器开关用于调整MRSC自稳模式
- 四个按钮开关，调整发射模式，车辆模型类型切换，带菜单
- 10个可选的模型编号,可切换遥控不同的模型
- 使用3.3V, 8MHz Pro Mini (不支持Pro Micro)
- STM32 ARM 版本 传送门: https://github.com/TheDIYGuy999/RC_Transmitter_STM32
- 使用2.4GHz NRF24L01 无线模块
- 使用0.96" I2C OLED
- 设定餐单包括: 通道反向, 舵量微调 (每个模型分开保存)
- 设定保存在单片机EEPROM内
- NRF24L01+PA+LNA SMA radio modules with power amplifier are supported from board version 1.1
- 简单易用
- Eagle PCB included
- PONG Game included

## Changelog:

New in V 1.3:
- Infrared codes for "MECCANO" IR controlled motors. Separate library required: https://github.com/TheDIYGuy999/MeccanoIr
- Multichannel transmission

New in V 1.4:
- 10 vehicle addresses instead of 5
- The "BACK" button can now be used (if the menu screen is not displayed on the OLED) as a momentary button, for example for a horn on the vehicle. It is sent as "data.momentary1"
- The "A6" potentiometer connector is now integrated in the code and is sent to the vehicle as "data.pot1"
- SimpleTimer library replaced with my own code, which uses significantly less memory
- EEPROM reset function added: press "Select" and "Back" during power on

New in V 1.41:
- Transmitter battery voltage now monitored correctly on 16MHz / 5V systems

New in V 1.42:
- Vehicle battery state change OLED bug fixed

New in V 1.43:
- Radio module sleep mode active while IR mode is in use

New in V 1.5:
- MECCANO IR support enhanced. Requires MECCANO library update to V 1.1

New in V 1.6:
- Buttons locked, if not required in selected transmission mode. This ensures, that no variables can be changed "in background"
- Automatic joystick zero point calibration after transmitter was switched on. This ensures, that you always have precise zero points, even if your potentiometers are not exacltly linear.

New in V 1.7:
- Support for 2 channel car style transmitters with steering wheel
- The transmitter type can be seletced in the new "transmitterConfig.h" file
- The potentiometers in some transmitters hit the mechanical endstop before the end of the electrical range is reached. This can now be compensated with the "range" variable

New in V 1.8:
- In most car style transmitters, the reverse range of the throttle potentiometer is smaller than the forward range.
- The reverse range is now multiplied by 4, to solve this problem

New in V 1.9:
- The "RC_Tester" functionality (https://github.com/TheDIYGuy999/RC_Tester) is now intergrated
- Useful, if you have more than one transmitter. Allows to visualize all 5 analog channels of your transmitter. The radio connection can be easily tested this way.
- Press "Select" during power on. The splash screen shows "Micro RC Tester" instead of "Micro RC Transmitter" and then a graphical screen, which visualizes all analog channels
- Works fo all 10 vehicle addresses

New in V 2.0:
- You have crashed your RC car? Then just play a little PONG session on your transmitter!
- Press "Back" during power on. The transittter is then activating the game mode :-)
- Press the "Back" button again to restart the game after "Game Over" is displayed

New in V 2.01:
- A serious bug in the mapJoystick() function was found during tests with the upcomming STM32 version
- The inverse and scale functionality did not work anymore since V2.0
- The bug is now solved and you can use the adjustments menu again


## Usage

See pictures
![](https://github.com/TheDIYGuy999/RC_Transmitter/blob/master/1.jpg)

![](https://github.com/TheDIYGuy999/RC_Transmitter/blob/master/Micro_RC_Transmitter.jpg)

(c) 2016 TheDIYGuy999
