# SSSIHL_Roadshow
This repository documents my experience in RISC-V and VLSI Chip Design Roadshow   &amp; Upskilling Workshop at SSSIHL

# Workshop Overview
In this one-day workshop, my fellow Physics enthusiast and I were introduced to VLSI and RISC-V and got to understand the process of making a chip. This workshop also helped us understand various kinds of chips and microprocessors. This workshop was very useful as it helped us delve more into the field of VLSI and chip designing, giving us more career options in the future.

# Process 
We first installed all the software as shown below

![Screenshot 2024-12-14 094402](https://github.com/user-attachments/assets/bf5f1750-9096-48b0-a24a-40817bcfc72d)

* Slack is a platform on which we received our codes. On it, we could share our personal progress with other designers and interact with them.

* Oracle virtual box helped us use an external OS where we designed our code(The OS used was  Ubuntu 18.04 LTS(Bionic Beaver)

* vsd squadron was exported to the virtual box where we used to open the OS.

# The follow-up steps

Now after setting up our necessary tools, we processed to open the Virtual Box and we were encountered with a preface of this kind.

![Screenshot 2024-12-13 100427](https://github.com/user-attachments/assets/bf79f6ec-f9d8-42f1-93e0-e1d75e039661)


* After opening Virtual Box we opened a new terminal where we wrote our new commands to install gedit

* We use the command ### Example Commands to clone a Git repository and install gedit:

  ` sudo apt install gedit`

  * The password provided by the host was used to install gedit
 
    

![image](https://github.com/user-attachments/assets/71b143fe-f6fa-4af0-9dfa-ccf4a05caf32)

* The new white interface was used to write our code and save it.

  ### Code ###
```
  #include<stdio.h>
int main(){
    int sum = 0, i, n;
    printf("Enter the value of n = ");
    scanf("%d",&n);
    for(i = 1;i <= n;i++){
       sum = sum + i;
    }
    printf("The Sum of numbers from 1 to %d is %d\n",n,sum);
    return 0;
}
```

![Screenshot 2024-12-13 102355](https://github.com/user-attachments/assets/0e820091-265e-4e54-8be5-2390e52462ba)

This was a simple code which adds the number from 1 to n where 'n' is the number provided by us.

* After saving the file we opened the previous terminal where we executed the code

* we used two commands here

  ` gcc {file name}.c`
  
  `./a.out`

  * After running the code we provided the number and it gave the sum of 1 to n.

    ![Screenshot 2024-12-13 103044](https://github.com/user-attachments/assets/0ef6bb24-0c17-40a3-b68f-5c72ada8965b)

## Then as we are using RISC-V architecture we will use the following command to do so :##
  
    `riscv64-unknown-elf-gcc -O1 -mabi=lp64 -march=rv64i -o {filename}.o {filename}.c`
* Then we disassemble the file for the RISC-V architecture using the following command :
  
    ```
  iscv64-unknown-elf-objdump -d {filename}.o
    ```
  After we ran the code we get the output as:

  
  ![Screenshot 2024-12-13 105239](https://github.com/user-attachments/assets/80df8510-006d-4a23-9940-ad9679d0d4e1)


  ## We then changed the directory of the openlane ##

  ```
  cd Desktop/work/tools/openlane_working_dir/openlane
  ```




![Screenshot 2024-12-13 121217](https://github.com/user-attachments/assets/86383699-9c15-4372-8c92-d1909a9598de)

* Then we specify the version to 0.9 by the following command
    ```
    package require openlane 0.9
    ```
* Then we prepare the design workspace for a specific project which in our case is picorv32a using the following command
     ```
     prep -design picorv32a
     ```

We then get

![Screenshot 2024-12-13 121815](https://github.com/user-attachments/assets/f05f1394-3ff7-472d-a84b-b3ca9c0aeca5)

* Then we trigger the synthesis stage of the digital IC design flow by using the following command
  ```
   run_synthesis
  ```

  Then we get

 
  
![image (2)](https://github.com/user-attachments/assets/b9282a2c-2ac0-4f67-bf1f-681c45baee95)


* Then we execute the floorplanning state of the IC design flow .It is a crucial step in translating the synthesized gate-level netlist into a physical design by defining the chip's layout structure and preparing it for placement and routing. This was done by executing the following command

  ```
      run_floorplan
  ```

  
![Screenshot 2024-12-13 123744](https://github.com/user-attachments/assets/1ee2bf44-60c3-4b9b-bc8c-ccde32e63684)


* Then we open a new terminal and type the following command to display the floorplan image(some changes in command is required) :

  ```
   eog designs/picorv32a/runs/{press tab as it varies from device to device}/results/floorplan/picorv32a.floorplan.def.png
  ```

  Then a png file is opened
  


![Screenshot 2024-12-13 124030](https://github.com/user-attachments/assets/3647bf81-ce39-4dca-8ad9-01cec93a49a4)


* For the placement stage of the digital ASIC design flow we use the following command
  ```
  run_placement
  ```

![Screenshot 2024-12-14 131827](https://github.com/user-attachments/assets/9eb469b6-051e-4120-89b4-fe8aaa4f9b5a)

* Then we open a new terminal and type the following command to display the placement image(some changes in command is required)
  
```
eog designs/picorv32a/runs/{press tab as it varies from device to device}/results/placement/picorv32a.placement.def.png
```

![Screenshot 2024-12-13 140936](https://github.com/user-attachments/assets/832ca6d5-0f79-4a77-833c-555b77785c14)



# Zoomed in image #


![Screenshot 2024-12-13 141058](https://github.com/user-attachments/assets/aebd8bc5-816f-40e3-b9f9-e3189461a062)


* Then we run the command n the OpenLane flow stands for Clock Tree Synthesis (CTS), and its purpose is to create a clock distribution network for your design.
    ```
      run_cts
    ```


    ![Screenshot 2024-12-13 141933](https://github.com/user-attachments/assets/b71adc0e-cf6d-4436-83ab-c18b580add44)


* Once CTS is complete, the next step is routing. This is where the tool connects all the cells using metal layers, creating the physical interconnections that make up the logic and clock paths of the design.We do this by running the following code:
 ```
run_routing
```

                  
![Screenshot 2024-12-13 143036](https://github.com/user-attachments/assets/72883670-6852-4e64-b703-dd68262e6c4f)

### This was the final step in designing a chip which is now ready for production ###

# Working a code on the VSD squadron #

After all the designing part we finally got the boards, now it was time to run a code on this board.

* We opened VS code where we used the Platform IO extension to run the code which was given to us on Slack.
* We then connected the board to to our laptop
* Then a little but of changes were made to the code
* We changed 1NVIC_PriorityGroup_2` to `NVIC_PriorityGroup_1`

  
![Screenshot 2024-12-14 133311](https://github.com/user-attachments/assets/8fe7f659-aa81-4350-bc70-71c448a19f47)


  
* Then the `Delay_Ms()` was changed from 1000 to 100 so that the LED blinks faster


![Screenshot 2024-12-14 133435](https://github.com/user-attachments/assets/b42f1fee-d2ea-4a27-8e23-63cf9c3af7ed)

# This was what was noticed on the board



https://github.com/user-attachments/assets/dea11e52-6198-4c74-8ecf-fcc5cf3f497d

# The code we used 

```
#include <ch32v00x.h>
#include <debug.h>

#define BLINKY_GPIO_PORT GPIOD
#define BLINKY_GPIO_PIN GPIO_Pin_6
#define BLINKY_CLOCK_ENABLE RCC_APB2PeriphClockCmd(RCC_APB2Periph_GPIOD, ENABLE)

void NMI_Handler(void) __attribute__((interrupt("WCH-Interrupt-fast")));
void HardFault_Handler(void) __attribute__((interrupt("WCH-Interrupt-fast")));
void Delay_Init(void);
void Delay_Ms(uint32_t n);

int main(void)
{
	NVIC_PriorityGroupConfig(NVIC_PriorityGroup_1);
	SystemCoreClockUpdate();
	Delay_Init();

	GPIO_InitTypeDef GPIO_InitStructure = {0};

	BLINKY_CLOCK_ENABLE;
	GPIO_InitStructure.GPIO_Pin = BLINKY_GPIO_PIN;
	GPIO_InitStructure.GPIO_Mode = GPIO_Mode_Out_PP;
	GPIO_InitStructure.GPIO_Speed = GPIO_Speed_50MHz;
	GPIO_Init(BLINKY_GPIO_PORT, &GPIO_InitStructure);

	uint8_t ledState = 0;
	while (1)
	{
		GPIO_WriteBit(BLINKY_GPIO_PORT, BLINKY_GPIO_PIN, ledState);
		ledState ^= 1; // invert for the next run
		Delay_Ms(100);
	}
}

void NMI_Handler(void) {}
void HardFault_Handler(void)
{
	while (1)
	{
	}
}
```


# We then used another code on the same platform to now cause the LED to fade slowly fade out

# Code

```
#include "debug.h"
#define TIME_PERIOD 1000
#define PRESC       0
#define PULSE       632
#define STEP_SIZE   10
volatile u16 val;
volatile u8 dir;
void TIM1_PWMOut_Init(void){
    GPIO_InitTypeDef GPIO_InitStructure={0};
    TIM_OCInitTypeDef TIM_OCInitStructure={0};
    TIM_TimeBaseInitTypeDef TIM_TimeBaseInitStructure={0};
    //RCC_APB2PeriphClockCmd( RCC_APB2Periph_GPIOC | RCC_APB2Periph_TIM1, ENABLE );
    RCC_APB2PeriphClockCmd( RCC_APB2Periph_GPIOD | RCC_APB2Periph_AFIO, ENABLE );
    RCC_APB1PeriphClockCmd( RCC_APB1Periph_TIM2, ENABLE );
    GPIO_PinRemapConfig(GPIO_FullRemap_TIM2, ENABLE);
    GPIO_InitStructure.GPIO_Pin = GPIO_Pin_6;
    GPIO_InitStructure.GPIO_Mode = GPIO_Mode_AF_PP;
    GPIO_InitStructure.GPIO_Speed = GPIO_Speed_50MHz;
    GPIO_Init( GPIOD, &GPIO_InitStructure);
    TIM_TimeBaseInitStructure.TIM_Period = TIME_PERIOD;
    TIM_TimeBaseInitStructure.TIM_Prescaler = PRESC;
    TIM_TimeBaseInitStructure.TIM_ClockDivision = TIM_CKD_DIV1;
    TIM_TimeBaseInitStructure.TIM_CounterMode = TIM_CounterMode_Up;
    TIM_TimeBaseInit( TIM2, &TIM_TimeBaseInitStructure);
    TIM_OCInitStructure.TIM_OCMode = TIM_OCMode_PWM2;
    TIM_OCInitStructure.TIM_OutputState = TIM_OutputState_Enable;
    TIM_OCInitStructure.TIM_Pulse = PULSE;
    TIM_OCInitStructure.TIM_OCPolarity = TIM_OCPolarity_High;
    TIM_OC3Init( TIM2, &TIM_OCInitStructure );
    TIM_CtrlPWMOutputs(TIM2, ENABLE );
    //TIM_OC3PreloadConfig( TIM1, TIM_OCPreload_Disable );
    //TIM_ARRPreloadConfig( TIM1, ENABLE );
    TIM_Cmd( TIM2, ENABLE );
}
int main(void)
{
    NVIC_PriorityGroupConfig(NVIC_PriorityGroup_1);
    SystemCoreClockUpdate();
    Delay_Init();
    TIM1_PWMOut_Init();
    val = 0;
    dir = 0;
    // Loop
    while(1){
        val += (dir) ? -STEP_SIZE : STEP_SIZE;
        TIM_SetCompare3(TIM2, val);
        dir ^= (val == 1000 || val == 0) ? 1 : 0;
        Delay_Ms(15);
    }
}

```

# The was what we observed with the new code





https://github.com/user-attachments/assets/0180ab39-7298-4396-ab3c-ab6c3eda7b57




### This was about the workshop that we as a department attended. It was really helpful for us and we got a lot of insights about VSLI and chip designing. ###
### I  would like to thank Mr. Kunal Gosh and his team for teaching and providing us with the equipment required for this workshop. I would also like to thank our Institute and our department for providing us with this opportunity ###
