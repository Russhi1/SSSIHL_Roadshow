# SSSIHL_Roadshow
This repository documents my experience in RISC-V and VLSI Chip Design Roadshow   &amp; Upskilling Workshop at SSSIHL

# Workshop Overview
In this one day workshop me and my fellow Physics enthusiast we were introduced to VLSI and RISC-V and got to understand the process of making a chip. This workshop also helped us understand about various kinds of chips and microprocessors, this workshop was very useful as it helped us to delve more into the field of VLSI and chip designing with more career options in the future.

# Process 
We first installed all the softwares as shown below

![Screenshot 2024-12-14 094402](https://github.com/user-attachments/assets/bf5f1750-9096-48b0-a24a-40817bcfc72d)

* Slack is platform where we recieved our codes and where we could share our personal progress with other designers in the channel and also interact with them.

* Oracle virtual box helped us use and external OS where we worked our code for designing.(The OS used was  Ubuntu 18.04 LTS(Bionic Beaver)

* vsd squadron was exported to the virtual box where we used to open the OS.

# The follow up steps

Now after setting up our necessary tools required we processed to open the Virtual Box and we were encountered with a preface of this kind

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

## Then as we are using RISC-V architechture we will use the following command to do so :##
  
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


* Then we execute the floorplanning state of the IC design flow .It is a crucial step in translating the synthesized gate-level netlist into a physical design by defining the chip's layout structure and preparing it for placement and routing.This was done by executing the following command

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

