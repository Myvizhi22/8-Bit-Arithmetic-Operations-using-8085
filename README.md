# 8-Bit-Arithmetic-Operations-using-8085
## Aim:
To perform 8-bit arithmetic operations such as addition, subtraction, multiplication, and division using the 8085 microprocessor.

## Apparatus Required:
•	Laptop with internet connection

## Algorithm:

### For Addition (With Carry Consideration):
1.	Load the first number from memory location 4200H into register A.
2.	Load the second number from memory location 4201H into register B.
3.	Add the contents of registers A and B.
4.	If carry is generated, store carry in 4301H.
5.	Store the sum in memory location 4300H.
   
### Program:
```
LDA 4200H
MOV B,A
LDA 4201H
ADD B
STA 4300H
JC STORE_CARRY
HLT
STORE_CARRY: MVI A,01H
STA 4301H
HLT
```

### Output:
<img width="778" height="445" alt="MPMC ADD (2)" src="https://github.com/user-attachments/assets/c5c6f5df-3151-4350-8757-46c73ba5107b" />
<img width="671" height="433" alt="MPMC ADD" src="https://github.com/user-attachments/assets/3f88c87d-371b-4dd1-9818-db6c97815401" />
<img width="1600" height="920" alt="image" src="https://github.com/user-attachments/assets/a998de3e-3a82-48ce-9b27-a7aa189f6eae" />


### For Subtraction (Considering Greater Number):
1.	Load the first number from memory location 4200H into register A.
2.	Load the second number from memory location 4201H into register B.
3.	Compare A and B.
4.	If A < B, swap the values of A and B to ensure positive result.
5.	Subtract the content of B from A.
6.	Store the result in memory location 4300H.

### Program:
```
LDA 4200H
MOV C,A
LDA 4201H
CMP C
JC SWAP
SWAP:
MOV B,A
MOV A,C
SUB B
STA 4300H
HLT
```
### Output:
<img width="807" height="485" alt="MPMC SUB (2)" src="https://github.com/user-attachments/assets/87f42a7c-fbb1-44a6-9fa9-a786e645e2b3" />
<img width="793" height="441" alt="MPMC SUB" src="https://github.com/user-attachments/assets/969339e4-2f18-4525-847a-7c95fb730f11" />
<img width="1323" height="1600" alt="image" src="https://github.com/user-attachments/assets/4e5d7984-a7dd-4eb5-84bb-5678c5adaff1" />


### For Multiplication:
1.	Load the first number from memory location 4200H into register A.
2.	Load the second number from memory location 4201H into register B.
3.	Multiply A and B using repeated addition.
4.	Store the result in memory locations 4300H and 4301H (if required for higher bits).

### Program:
```
LDA 4200H
MOV C,A
LDA 4201H
MOV B,A
MVI A,00H
LOOP:ADD C
DCR B
JNZ LOOP
STA 4300H
HLT
```

### Output:
<img width="707" height="468" alt="MPMC MUL (2)" src="https://github.com/user-attachments/assets/b1534623-bb73-4989-8750-0a30684b9763" />

<img width="685" height="424" alt="MPMC MUL" src="https://github.com/user-attachments/assets/4e516281-cb94-4866-84e5-1dd0490f1a59" />
<img width="1599" height="865" alt="image" src="https://github.com/user-attachments/assets/b4a71cd5-fd34-4c7e-853f-db2e03bdb952" />
<img width="1600" height="639" alt="image" src="https://github.com/user-attachments/assets/1e30e9bb-db50-42bd-8847-2cf5f53fddb1" />


### For Division:
1.	Load the dividend from memory location 4200H into register A.
2.	Load the divisor from memory location 4201H into register B.
3.	Perform division using repeated subtraction.
4.	Store the quotient in 4300H and remainder in 4301H.

### Program:
```
LDA 4200H
MOV C,A
LDA 4201H
MOV B,A
MVI A,00H
LOOP: MOV A, C
CMP B
JC END
SUB B
MOV C, A
INR D
JMP LOOP
END:MOV A, D
STA 4300H
MOV A,C
STA 4301H
HLT
```
### Output:
<img width="697" height="483" alt="Screenshot 2026-02-02 220952" src="https://github.com/user-attachments/assets/0102e720-0146-4c4d-b4dc-e91c15df8509" />
<img width="783" height="474" alt="Screenshot 2026-02-02 220959" src="https://github.com/user-attachments/assets/59e8716e-458e-4586-95bf-a46c17cd2634" />
<img width="1200" height="1600" alt="image" src="https://github.com/user-attachments/assets/d4ca9d10-17c9-45b3-b305-26c0ff74ac74" />


## Result:
The 8-bit arithmetic operations using the 8085 microprocessor have been successfully executed and verified using memory access for input and output.

