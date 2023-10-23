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
