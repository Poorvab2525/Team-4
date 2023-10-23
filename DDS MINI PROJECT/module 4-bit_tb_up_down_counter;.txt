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
