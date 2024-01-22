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

## Development proccess
###Inverse kinematics
I used the solution proposed in  for inverse kinematics.
Then, I created a simulation of robot to attest forward kinmatics and choose motors base on the needed torque.
To attest inverse kinematic, I use python script to generate inverse kinematic and connect the python script to CoppeliaSim.
the inverse kinematics is borrowed from [A method for optimal kinematic design of five-bar planar parallel
manipulators](https://www.researchgate.net/publication/271456154_A_method_for_optimal_kinematic_design_of_five-bar_planar_parallel_manipulators?enrichId=rgreq-e05d64d5ab9bd540445867751f7cc126-XXX&enrichSource=Y292ZXJQYWdlOzI3MTQ1NjE1NDtBUzo1MTY5NjUyMDAxNDIzMzdAMTUwMDI2NTUxNjk0Mw%3D%3D&el=1_x_3&_esc=publicationCoverPdf) just in the impelementation atan2 is used to avoid zero division error.

## Resources

CoppeliaSim
- [Complete CoppeliaSim Tutorial](https://youtube.com/playlist?list=PLjzuoBhdtaXOoqkJUqhYQletLLnJP8vjZ&si=S4ka2eGPEegMdhhC)
- [CoppeliaSim Documentaion](https://manual.coppeliarobotics.com/)
- [Connect python to CoppeliaSim](https://www.youtube.com/watch?v=TGT7KbP7Dfs) 

STM32
- [Complete STM32 programming with HAL tutorial](https://sisoog.com/category/microcontroller/stm32/%D8%AA%D9%88%D8%A7%D8%A8%D8%B9-hal/)

## Bugs and Fixs

Keil

- SWDIO no target connected
(https://community.st.com/t5/stm32-mcus-products/keil-swdio-no-target-connected/m-p/341236/highlight/true#M84452)

- Amongst 3 choices for drv8845 step pulse
  * timer PWM and manipulation of duty cycle
  * timer interupt and toggleing GPIO
  * GPIO toggle and delay

for this project specific need that is precise position rather than accurate speed profile. It seems the latter approach is the best because it simplifys the control algorithm and avoids complicated conditions on timers to accurately send step pulses.

- the drv8825 does not work unless pull up the sleep and reset pins
- ac/dc adaptors mmight not be accurate

STM32CubeMx

CoppeliaSim

Electrical
