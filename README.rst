#include <iostream>
#include <bitset>
#include <cstdlib>
#include <stdint.h>

using namespace std;

uint16_t u[]={
0b0000000000100010,
0b1111110100011000,
0b1101101001001000,
0b0101010001100001
};

void decode(uint16_t data)
{
int i;
bitset<16> x(data);
bitset<6> opcode;
int op1=0,op2=0;
int mul = 1; 
  
for(i = 0 ; i<6;i++)
{
opcode[i] = x[i];
}
    
for(i=6;i<=10;i++)
{
op1 += x[i]*mul; 
mul = mul*2;
}
  
mul = 1; 
  
for(i=11;i<=15;i++){
op2 += x[i]*mul;
mul = mul*2;
}
  
cout<<"opcode: "<<opcode<<" op1: "<<"r"<<op1<<" op2: "<<"R"<<op2<<endl;
  
}

int main()
{
for(int i=0;i<sizeof(u)/sizeof(u[0]);i++){
  
decode(u[i]);
  
  
}
return 0;
}