## Team-4
Project Title - AUTOMATED BRAKING SYSTEM

## Team Details
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

 Functional Table
<details>
   
![image](https://github.com/Poorvab2525/Team-4/assets/127173860/7313f088-2e32-4212-a327-9c81f49b03e6)

</details>

## Logisim Circuit Diagram

<details>
   
![DDS_main](https://github.com/Poorvab2525/Team-4/assets/127173860/46612fbf-a397-4e9e-a4c6-e76a43113a73)

</details>

## Verilog Code

<details>

module 4-bit_up_down_counter (
    input wire clk,
    input wire rst,
    input wire up,
    input wire down,
    output reg [3:0] count
);
    always @(posedge clk or posedge rst) begin
        if (rst)
            count <= 4'b0000;
        else if (up)
            count <= (count == 4'b1111) ? 4'b0000 : count + 1;
        else if (down)
            count <= (count == 4'b0000) ? 4'b1111 : count - 1;
    end
 
endmodule

module 4-bit_tb_up_down_counter;
    reg clk, rst, up, down;
    wire [3:0] count;
 
    up_down_counter uut (
        .clk(clk),
        .rst(rst),
        .up(up),
        .down(down),
        .count(count)
    );
 
    initial begin
        clk = 0;
        rst = 1;
        up = 0;
        down = 0;
        #10 rst = 0;
    end
 
    always begin
        #5 clk = ~clk;
    end
 
    initial begin
        $monitor("Time=%t, Count=%b", $time, count);
        #20 up = 1;
        #40 down = 1;
        #60 up = 0;
        #80 down = 0;
        #100 $finish;
    end
 
endmodule

module up_down_counter (
    input wire clk,
    input wire rst,
    input wire up,
    input wire down,
    output reg [3:0] count
);
    always @(posedge clk or posedge rst) begin
        if (rst)
            count <= 4'b0000;
        else if (up)
            count <= (count == 4'b1111) ? 4'b0000 : count + 1;
        else if (down)
            count <= (count == 4'b0000) ? 4'b1111 : count - 1;
    end

endmodule

module updowncounter_testbench();
  reg clk, reset, up_down;
  wire [3:0] counter;
 
  up_down_counter dut (
    .clk(clk),
    .reset(reset),
    .up_down(up_down),
    .counter(counter)
  );
 
  initial begin 
    clk = 0;
    forever #5 clk = ~clk;
  end
 
  initial begin
    reset = 1;
    up_down = 0;
    #20;
    reset = 0;
    #200;
    up_down = 1;
  end
endmodule      

</details>


