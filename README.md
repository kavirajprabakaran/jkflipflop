EXP NO:4 Implementation of JKFLIPFLOP
AIM:

To implement JK flipflop using verilog and validating their functionality using their functional tables

SOFTWARE REQUIRED:

Quartus prime

THEORY

JK Flip-Flop

JK flip-flop is the modified version of SR flip-flop. It operates with only positive clock transitions or negative clock transitions. The circuit diagram of JK flip-flop is shown in the following figure.


This circuit has two inputs J & K and two outputs Qtt & Qtt’. The operation of JK flip-flop is similar to SR flip-flop. Here, we considered the inputs of SR flip-flop as S = J Qtt’ and R = KQtt in order to utilize the modified SR flip-flop for 4 combinations of inputs. The following table shows the state table of JK flip-flop.


Here, Qtt & Qt+1t+1 are present state & next state respectively. So, JK flip-flop can be used for one of these four functions such as Hold, Reset, Set & Complement of present state based on the input conditions, when positive transition of clock signal is applied. The following table shows the characteristic table of JK flip-flop. Present Inputs Present State Next State


By using three variable K-Map, we can get the simplified expression for next state, Qt+1t+1. Three variable K-Map for next state, Qt+1t+1 is shown in the following figure.



The maximum possible groupings of adjacent ones are already shown in the figure. Therefore, the simplified expression for next state Qt+1t+1 is Q(t+1)=JQ(t)′+K′Q(t)Q(t+1)=JQ(t)′+K′Q(t)

Procedure
1.Open Quartus II and create a new project wizard.

2.Create a Verilog HDL file and enter the JK Flip-Flop code.

3.Save the file.

4.Click Compile to check for errors and build the design.

5.Go to Tools > Netlist Viewers > RTL Viewer to view and save the RTL schematic.

6.Create a Vector Waveform File (.vwf) via File > New > University Program VWF.

7.Add input/output nodes using Node finder.

8.Apply different input combinations (J, K, Clock) in the waveform.

9.Run Simulation from Processing > Start Simulation.

10.View and save the timing diagram showing the JK flip-flop behavior.

PROGRAM
```
module jk_ff (
    input  wire clk, rst, J, K,
    output reg  Q
);
    always @(posedge clk or posedge rst) begin
        if (rst)
            Q <= 1'b0;        // Reset
        else begin
            case ({J,K})
                2'b00: Q <= Q;        // Hold
                2'b01: Q <= 1'b0;     // Reset
                2'b10: Q <= 1'b1;     // Set
                2'b11: Q <= ~Q;       // Toggle
            endcase
        end
    end
endmodule

```

RTL LOGIC FOR FLIPFLOPS
[rtl.pdf](https://github.com/user-attachments/files/24108638/rtl.pdf)



TIMING DIGRAMS FOR FLIP FLOPS
[wave img.bmp](https://github.com/user-attachments/files/24108652/wave.img.bmp)


RESULT
JK flipflop using verilog and validating their functionality using their functional tables are verified.
