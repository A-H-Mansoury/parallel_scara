# Prototype Parallel Scara
This repository contains tools and websites I used to build this robot and fix problems. 

## Components
- 1 bluepill header board
- 1 stlink v2
- 1 breadboard
- 2 stepper motor 200 pulse 
- 2 drv8825
- 4 plastic connect strip 12cm
- 2 plastic connect strip 7cm
- some screws and nuts


## Development Environment
- [CoppeliaSim](https://www.coppeliarobotics.com/)
physical simulation and attest kinematic algorithms.
- [stm32cubemx](https://www.st.com/en/development-tools/stm32cubemx.html)
configure bluepill header board
- [keil](https://www.keil.com)
Programming IDE


## Resources

CoppeliaSim
- (https://youtube.com/playlist?list=PLjzuoBhdtaXOoqkJUqhYQletLLnJP8vjZ&si=S4ka2eGPEegMdhhC)
- (https://manual.coppeliarobotics.com/)

STM32
- (https://sisoog.com/category/microcontroller/stm32/%D8%AA%D9%88%D8%A7%D8%A8%D8%B9-hal/)

## Bugs and Fixs

Keil

- SWDIO no target connected
(https://community.st.com/t5/stm32-mcus-products/keil-swdio-no-target-connected/m-p/341236/highlight/true#M84452)

- Amongst 3 choices for drv8845 step pulse
  * timer PWM and manipulation of duty cycle
  * timer interupt and toggleing GPIO
  * GPIO toggle and delay
  for this project specific need that is precise position rather than accurate speed profile. It seems the latter approach is the best because it simplifys the control algorithm and avoids complicated conditions on timers to accurately send step pulses
- the drv8825 does not work unless pull up the sleep and reset pins
- ac/dc adaptors mmight not be accurate

STM32CubeMx

CoppeliaSim

Electrical
