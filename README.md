module multi_12(a,b,pro);
input [11:0]a,b;
output [23:0] pro;

wire [10:0] w1,w2,w3,w4,w5,w6,w7,w8,w9,w10,w11,w12;
wire [10:0] w13,w14,w15,w16,w17,w18,w19,w20,w21,w22,w23,w24;
wire [14:0] csa_sum;
wire [14:0] Carry_select_adder_sum;
wire [5:0] csa_actual_carry;
wire carry_select_adder_carry;
wire csa_carry;


assign w1  = {a[0]&b[1],  a[0]&b[2],  a[0]&b[3],  a[0]&b[4],  a[0]&b[5],  a[0]&b[6],  a[0]&b[7],  a[0]&b[8],  a[0]&b[9],  a[0]&b[10], a[0]&b[11]};
assign w2  = {a[1]&b[0],  a[1]&b[1],  a[1]&b[2],  a[1]&b[3],  a[1]&b[4],  a[1]&b[5],  a[1]&b[6],  a[1]&b[7],  a[1]&b[8],  a[1]&b[9],  a[1]&b[10]};
assign w3  = {a[2]&b[0],  a[2]&b[1],  a[2]&b[2],  a[2]&b[3],  a[2]&b[4],  a[2]&b[5],  a[2]&b[6],  a[2]&b[7],  a[2]&b[8],  a[2]&b[9],  1'b0};
assign w4  = {a[3]&b[0],  a[3]&b[1],  a[3]&b[2],  a[3]&b[3],  a[3]&b[4],  a[3]&b[5],  a[3]&b[6],  a[3]&b[7],  a[3]&b[8],  1'b0,      1'b0};
assign w5  = {a[4]&b[0],  a[4]&b[1],  a[4]&b[2],  a[4]&b[3],  a[4]&b[4],  a[4]&b[5],  a[4]&b[6],  a[4]&b[7],  1'b0,      1'b0,      1'b0};
assign w6  = {a[5]&b[0],  a[5]&b[1],  a[5]&b[2],  a[5]&b[3],  a[5]&b[4],  a[5]&b[5],  a[5]&b[6],  1'b0,      1'b0,      1'b0,      1'b0};
assign w7  = {a[6]&b[0],  a[6]&b[1],  a[6]&b[2],  a[6]&b[3],  a[6]&b[4],  a[6]&b[5],  1'b0,      1'b0,      1'b0,      1'b0,      1'b0};
assign w8  = {a[7]&b[0],  a[7]&b[1],  a[7]&b[2],  a[7]&b[3],  a[7]&b[4],  1'b0,      1'b0,      1'b0,      1'b0,      1'b0,      1'b0};
assign w9  = {a[8]&b[0],  a[8]&b[1],  a[8]&b[2],  a[8]&b[3],  1'b0,      1'b0,      1'b0,      1'b0,      1'b0,      1'b0,      1'b0};
assign w10 = {a[9]&b[0],  a[9]&b[1],  a[9]&b[2],  1'b0,      1'b0,      1'b0,      1'b0,      1'b0,      1'b0,      1'b0,      1'b0};
assign w11 = {a[10]&b[0], a[10]&b[1], 1'b0,      1'b0,      1'b0,      1'b0,      1'b0,      1'b0,      1'b0,      1'b0,      1'b0};
assign w12 = {a[11]&b[0], 1'b0,      1'b0,      1'b0,      1'b0,      1'b0,      1'b0,      1'b0,      1'b0,      1'b0,      1'b0};

assign w13 = {1'b0,1'b0,1'b0,1'b0,1'b0,1'b0,1'b0,1'b0,1'b0,1'b0, a[1]&b[11]};
assign w14 = {1'b0,1'b0,1'b0,1'b0,1'b0,1'b0,1'b0,1'b0,1'b0, a[2]&b[10], a[2]&b[11]};
assign w15 = {1'b0,1'b0,1'b0,1'b0,1'b0,1'b0,1'b0,1'b0, a[3]&b[9], a[3]&b[10], a[3]&b[11]};
assign w16 = {1'b0,1'b0,1'b0,1'b0,1'b0,1'b0,1'b0, a[4]&b[8], a[4]&b[9], a[4]&b[10], a[4]&b[11]};
assign w17 = {1'b0,1'b0,1'b0,1'b0,1'b0,1'b0, a[5]&b[7], a[5]&b[8], a[5]&b[9], a[5]&b[10], a[5]&b[11]};
assign w18 = {1'b0,1'b0,1'b0,1'b0,1'b0, a[6]&b[6], a[6]&b[7], a[6]&b[8], a[6]&b[9], a[6]&b[10], a[6]&b[11]};
assign w19 = {1'b0,1'b0,1'b0,1'b0, a[7]&b[5], a[7]&b[6], a[7]&b[7], a[7]&b[8], a[7]&b[9], a[7]&b[10], a[7]&b[11]};
assign w20 = {1'b0,1'b0,1'b0, a[8]&b[4], a[8]&b[5], a[8]&b[6], a[8]&b[7], a[8]&b[8], a[8]&b[9], a[8]&b[10], a[8]&b[11]};
assign w21 = {1'b0,1'b0, a[9]&b[3], a[9]&b[4], a[9]&b[5], a[9]&b[6], a[9]&b[7], a[9]&b[8], a[9]&b[9], a[9]&b[10], a[9]&b[11]};
assign w22 = {1'b0, a[10]&b[2], a[10]&b[3], a[10]&b[4], a[10]&b[5], a[10]&b[6], a[10]&b[7], a[10]&b[8], a[10]&b[9], a[10]&b[10], a[10]&b[11]};
assign w23 = {a[11]&b[1], a[11]&b[2], a[11]&b[3], a[11]&b[4], a[11]&b[5], a[11]&b[6], a[11]&b[7], a[11]&b[8], a[11]&b[9], a[11]&b[10], a[11]&b[11]};

csa_12 adder1(w1,w2,w3,w4,w5,w6,w7,w8,w9,w10,w11,w12,csa_sum,carry);
assign csa_actual_carry = {csa_carry,csa_sum[14:11]};
assign w24 = { 6'b000000, csa_actual_carry};
carry_select_adder_11bit adder2(w13,w14,w15,w16,w17,w18,w19,w20,w21,w22,w23,w24,1'b0,Carry_select_adder_sum,carry_select_adder_carry);

assign pro = {a[0]&b[0],csa_sum[10:0],Carry_select_adder_sum[10:0],Carry_select_adder_sum[11]};

endmodule

compilation done.
