## <center>TCL Workshop</center> 
In this workshop using Yosys and OpenTimer tools with TCL (for initial interface shell used) based programming.
Analyzed Timing reports in the dashboard after Synthesis and Timing checks on given design.


### Introduction
TCL (Tool Command Language) is a high-level, interpreted scripting language known for its simplicity and flexibility. It is widely used for rapid application development, automation, GUI creation (often with Tk), and embedding into C-based programs. Tcl is platform-independent and supports dynamic typing, making it easy to prototype and extend. It is especially popular in domains like electronic design automation (EDA) for scripting tasks in tools like Synopsys and Cadence. With a straightforward syntax and powerful string handling, Tcl enables quick development of control scripts and testing frameworks, making it a valuable tool for developers and engineers in various technical fields.

## Module 1: Creating global unix file using shell scripting and to call TCL file

- Starting Info: If no argv is there, it shoud provide info to use
![image](https://github.com/user-attachments/assets/86f6226f-6654-4815-a151-ba6203c8b1fc)

- Providing nonexisting csv file and expecting error message
![image](https://github.com/user-attachments/assets/c7cdddee-6acf-472f-af85-b35a19688ce8)

- -help info message
![image](https://github.com/user-attachments/assets/1cb3de86-8f2e-4282-8e17-06908724061a)

- Checking for existence of collaterals
![image](https://github.com/user-attachments/assets/3fe7f6b2-53e1-435e-a209-06c59899d3e4)

- Printing Collaterals and Variable values info
![image](https://github.com/user-attachments/assets/330d6fb3-4117-4318-bf61-8061e5b9288d)

- Collaterals and paths existence check
![image](https://github.com/user-attachments/assets/33bdb8c2-c9b2-4235-adde-931bb1f4e19c)

- Analysing input constraints CSV/.xls file.
  - This will help to understand where clocks, inputs, outputs sections are starting and their starting location (Getting Row & Column info properly)
![image](https://github.com/user-attachments/assets/60ad5241-c611-40d8-9816-dacf50984083)

## Module 2: ********* SDC Formatting started ***********

 ### Clocks Section
 #### Main theme: Creation of SDC cons for all clocks in the design
- Strategy used for grepping clock info, uniquifying ports, duty cycle forming and printing info:
![image](https://github.com/user-attachments/assets/d69bf7be-057a-4acc-9a6d-3125a10173fe)

- Clocks SDC formatting info:
![image](https://github.com/user-attachments/assets/d837c81d-fd7a-4f73-a451-018a79cd6a53)

### Input ports section 
#### Main theme: Segregation of bussed and non-bussed ports of the design, uniquifying ports and broadcasting respective input port values in SDC cons 

- Input ports formatting code: (Did mistake my reopening output file and faced missing of few lines and debugged later based on observation)
![image](https://github.com/user-attachments/assets/5b45a046-ec74-4a69-bbc8-f1f3e459430f)

- **Issue faced** - SDC some lines are missing: (both for input and output ports)
![image](https://github.com/user-attachments/assets/d241a8d8-b24b-44d4-911d-a5108354eea4)

- Opened sdc file again for writing in input and output sdc formating code, so faced above error.
![image](https://github.com/user-attachments/assets/0fbca738-6de9-4034-b6fa-3db441a1c812)

- **After fixing the code** : (Input ports)
![image](https://github.com/user-attachments/assets/1f61cd67-6209-415a-95d7-da2b9613bec7)

### Output ports section 
#### Main theme: Segregation of bussed and non-bussed ports of the design, uniquifying ports and broadcasting respective Output port values in SDC cons

- Output ports bussed and non-bussed identification as like input ports 
![image](https://github.com/user-attachments/assets/73e9ccd4-63f2-48bf-907f-76b32f00a26a)

- Output ports sdc formatting:
![image](https://github.com/user-attachments/assets/c9c5cf97-697c-4ae5-a736-670d5f1e54b7)

###             ********* SDC Formatting Completed ***********


## Module 3: ********* Design Hierarchy check using Yosys Tool ***********

- Yosys Tool Hierarchy Identification code:
![image](https://github.com/user-attachments/assets/643dd02e-7d0c-4fac-bb4e-8eb9659975f5)

- Yosys Hierarchy check status:
![image](https://github.com/user-attachments/assets/caaf79bd-b8ee-40fa-b0f1-d99c3c8bb711)

### ********* Design Hierarchy check using Yosys Tool completed ***********

## Module 4: ********* YOSYS: Main Synthesis starts **********

- Yosys Synthesis commands for given verilog code 
![image](https://github.com/user-attachments/assets/942f2861-211a-4390-94c0-9ccc4641e27b)

- Hacking code for Output NETLIST manipulation for Opentimer tool compatability:
![image](https://github.com/user-attachments/assets/41881b39-da4c-41b1-9f51-0026640df679)

- Synthesis Running:
![image](https://github.com/user-attachments/assets/3b69be68-ff9c-4b56-822d-e951f8ff666b)

### Synthesis completed successfully
![image](https://github.com/user-attachments/assets/82a4b8e9-2f14-4a39-85ce-0d6ed874013c)

###  ********* YOSYS: Main Synthesis Completed **********

## Module 5: ********* OpenTimer: Timing starts **********

- Calling multiple procs for usage:
![image](https://github.com/user-attachments/assets/5ea37d3a-56c9-4547-a786-9a470c57afcb)

- Faced output ports open timing format issue creation, so updated proc to pick proper values 
  - **Reason for this failure:** I have dumped sdc in different order so based on that I created proc to pic proper values)
![image](https://github.com/user-attachments/assets/00b3688a-1ca2-4f68-a10d-77b5e7b758af)

- After proc update, sdc to .timing is proper
![image](https://github.com/user-attachments/assets/6dbd6e00-de88-4abf-9c5c-1d55504a2071)

- Creation of .conf file for Timnig run and sourcing it
![image](https://github.com/user-attachments/assets/6035f09e-ed2c-44a3-9d52-214530177daa)

- Timing analysis started and results info:
![image](https://github.com/user-attachments/assets/7cef9860-c0a1-4c74-933a-2cff0bd12e55)
![image](https://github.com/user-attachments/assets/b3851398-65af-4413-b32d-74805bc2c6df)

### ********* Timnig analysis completed *********

## Module 6: ********* QOR Dash board creation *********

- Grepping different info like WNS, Wost_slack (hold, setup), instance count from Open-Timer STA reports
![image](https://github.com/user-attachments/assets/49f9e064-7243-4d27-b509-e7183ae25b3f)

- Code for Dashboard creation:
![image](https://github.com/user-attachments/assets/81c9f94c-e6d7-4bb3-8d08-1d2ff864df07)

### ********* QOR Dash board creation completed *********


                                     ********** QOR PRELAYOUT STA RESULT SUMMARY ****************
![image](https://github.com/user-attachments/assets/13fa140c-6402-4657-ba0e-0979024f834c)




