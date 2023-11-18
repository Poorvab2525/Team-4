## Team-4
Project Title - AUTOMATED BRAKING SYSTEM

## Team Members
<details>

Semester : 3rd Sem B.tech CSE
Section - S2

Member 1. Bhagwat Poorva Milind
   
221CS212

bhagwatpoorvamilind.221cs212@nitk.edu.in 

8275391841 
 
Member 2. Preetha Sarkar
   
221CS236 

preethasarkar.221cs236@nitk.edu.in 

6292253051 
 
Member 3. Reema Murthy
   
221CS240 

reemamurthy.221cs240@nitk.edu.in 

</details>

## Abstract
<details>
An automatic emergency braking system is a safety feature installed in vehicles to mitigate collisions and prevent accidents. Clock pulse from sensor output is generated.
A tracking type ADC is used to convert the analogue output of the proximity sensor to a digital output.
4-bit up down counter is made using 4 JK Flip-Flops. The digital output of the ADC is used as input to the 4-bit counter to either count up or down to represent the changing speed of the vehicle.
The counter is updated based on the changing outputs of the ADC.
The logic for the braking system is implemented when the proximity sensor detects an obstacle.
</details>

## Working of the project
<details>
The proximity sensor detects how far an obstacle by giving an analog output in the voltage range 0-5V. 5V corresponds to obstacle being very near to our vehicle.
An ADC converter is integrated into the circuit which takes the analogue output of the proximity sensor and converts it to a digital signal.
Inside the ADC converter the following circuits are present:
1.Comparator
2.An up-down counter
3.A DAC 
4.S-R Latch
The S-R Latch of the ADC gives the final digital output.
This digital output is stored in memory by another SR Latch, which is connected to a counter.
The counter is used to calculate and modify the speed of the vehicle based on the output shown by the SR Latch. For example: If the proximity sensor gives an output of 5V, the ADC converts it to a binary number and the SR Latch stores this number. If the next output given by the proximity sensor is 4V the SR Latch uses the stored binary number and decides if speed should be increased or decreased.

![DDS_working](https://github.com/Poorvab2525/Team-4/assets/127173860/6cde200b-8a8d-4a91-8d7a-167e78903be5)
</details>

## Functional Table
<details>
![image](https://github.com/Poorvab2525/Team-4/assets/127173860/7313f088-2e32-4212-a327-9c81f49b03e6)
</details>

## Logisim Circuit Diagram
<details>

![DDS_main](https://github.com/Poorvab2525/Team-4/assets/127173860/46612fbf-a397-4e9e-a4c6-e76a43113a73)
</details>

## Verilog Code





