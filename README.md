# virtualFPGA_PS22_BMS
//FPGA led as binary counter
\SV
   m4_include_lib(['https://raw.githubusercontent.com/BalaDhinesh/Digital-Design-on-FPGA--Phaseshift22/main/src/fpga_includes.tlv'])
   m4_makerchip_module   // (Expanded in Nav-TLV pane.)
   reg [7:0] led;
    always @(posedge clk)
       begin 
          if(reset) 
             led<=0;
          else
             led<=led+1;
          end
\TLV
   m4_define(M4_BOARD, 1)  
   m4+fpga_init()
   m4+fpga_led(*led)
\SV
   endmodule
   \SV
   m4_include_lib(['https://raw.githubusercontent.com/BalaDhinesh/Digital-Design-on-FPGA--Phaseshift22/main/src/fpga_includes.tlv'])
   m4_makerchip_module   // (Expanded in Nav-TLV pane.)
   wire [3:0] digit;
   wire [6:0] segment;
   wire dp;
                   
     assign   digit = 4'b1000;
      assign  segment =7'b0000000;
                   assign dp=0;
        
                   
\TLV
   m4_define(M4_BOARD, 2)  
   m4+fpga_init()
   m4+fpga_sseg(*digit, *segment, *dp)
\SV
   endmodule
