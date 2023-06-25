// BIST switch


`timescale 1ns / 1ps
module switch( input clk, [3:0] switch,  
output [3:0] led

    );
    
    integer count=0;
    reg sclk;
    always@(posedge clk)
    begin
        if(count < 10)
        count<=count+1;
        
        else
            begin
            count<=0;
            sclk=~sclk;
            end
    end
    
    reg flag =1'b0;
    
    always@(posedge clk)
    begin
        if(switch == 4'b0000)
        flag <= 1'b0;
        
        else
            flag<=1'b1;
    end
    ////////////
    integer i=0;
    reg [3:0] temp=0;
    
    always@(posedge clk)
    begin
    if(flag == 1'b0)
    begin
        if(i<4)
        begin
            temp <= {1'b1, temp[3:1]};
            i<= i+1;
        end
        
        else if(i<8)
        begin
            temp <= {temp[2:0], 1'b0};
            i<= i+1;
        end 
        
        else 
        begin
            i<=0;
            temp<= 4'b000;
        end
    end
    
else
begin
   temp <= switch;
end

end
 
assign led = temp;

endmodule
