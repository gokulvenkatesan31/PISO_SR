# PISO_SR
# The shift register, which allows parallel input (data is given separately to each flip flop and in a simultaneous manner) and produces a serial output is known as a Parallel-In Serial-Out shift register. The logic circuit given below shows a parallel-in-serial-out shift register. The circuit consists of four D flip-flops which are connected. The clock input is directly connected to all the flip-flops but the input data is connected individually to each flip-flop through a multiplexer at the input of every flip-flop. The output of the previous flip-flop and parallel data input are connected to the input of the MUX and the output of MUX is connected to the next flip-flop. All these flip-flops are synchronous with each other since the same clock signal is applied to each flip-flop. 
![image](https://github.com/RESMIRNAIR/PISO_SR/assets/154305926/f0f2d979-b298-4693-b5c8-8eea850936d4)
# verilog code
```
module piso_shift_register( input wire clk, // Clock input input wire reset, // Reset input input wire parallel_in, // Parallel input output reg serial_out // Serial output );

// Initialize shift register reg [7:0] shift_reg = 8'b00000000;

always @(posedge clk or posedge reset) begin if (reset) begin // Reset shift register shift_reg <= 8'b00000000; serial_out <= 1'b0; end else begin // Shift data in if (parallel_in) begin shift_reg <= {shift_reg[6:0], parallel_in}; // Shift in parallel data end

// Serial output
serial_out <= shift_reg[7];
end end

endmodule
```
# output
![329463893-2595183e-81d3-4434-8f9e-8a2eb0852223](https://github.com/gokulvenkatesan31/PISO_SR/assets/123715763/45437133-fcad-460c-92fa-e8a41bf7fba3)
