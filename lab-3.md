# NEUB CSE Microprocessor and Interfacing Lab Spring 2025 Lab 3



## Task 1
Write a program to (a) prompt the user, (b) read first, middle, and last initials of a person's name, and (c) display them down the left margin.

Sample execution:
```
ENTER THREE INITIALS: JFK
J
F
K
```
```asm
.MODEL small
.STACK 100H
.DATA    
MSG db 'ENTER THREE INITIALS: $'
NEWL db 0Ah, 0Dh, '$'
.CODE
MAIN PROC 
    MOV AX, @DATA
    MOV DS, AX    
    
    ;Print initial message
    MOV AH, 9
    LEA DX, MSG
    INT 21h               
    
    ;Take input
    MOV AH, 1
    INT 21h     
    MOV BL, AL
          
    INT 21h
    MOV BH, AL
    
    INT 21h
    MOV CH, AL      
    
    ;Print Output 
    MOV AH, 9
    LEA DX, NEWL
    INT 21h
     
    MOV AH, 2
    MOV DL, BL
    INT 21h   
    
    MOV AH, 9
    LEA DX, NEWL
    INT 21h
    MOV AH, 2  
    MOV DL, BH
    INT 21h    
    
    MOV AH, 9
    LEA DX, NEWL
    INT 21h
    MOV AH, 2 
    MOV DL, CH
    INT 21h
    

    
    MOV AH, 4CH
    INT 21H
    
ENDP MAIN
END MAIN
```

## Task 2
Take 6 characters as input and print them in new lines.
```asm
.MODEL small
.STACK 100H
.DATA    
MSG db 'ENTER SIX INITIALS: $'
NEWL db 0Ah, 0Dh, '$'     
a db ?,'$'
b db ?,'$'
c db ?,'$'
d db ?,'$'
e db ?,'$'
f db ?,'$'
.CODE
MAIN PROC 
    MOV AX, @DATA
    MOV DS, AX    
    
    ;Print initial message
    MOV AH, 9
    LEA DX, MSG
    INT 21h               
    
    ;Take input    
    MOV AH, 1
    INT 21h
    MOV a, AL
    INT 21h
    MOV b, AL  
    INT 21h
    MOV c, AL
    INT 21h
    MOV d, AL
    INT 21h
    MOV e, AL
    INT 21h
    MOV f, AL     
             
    ;Print the characters            
    MOV AH, 2            
    MOV DL, 0Dh
    INT 21h
    MOV DL, 0Ah
    INT 21h  
    MOV DL, a
    INT 21h
                   
    MOV DL, 0Dh
    INT 21h
    MOV DL, 0Ah
    INT 21h  
    MOV DL, b
    INT 21h
           
    MOV DL, 0Dh
    INT 21h
    MOV DL, 0Ah
    INT 21h  
    MOV DL, c
    INT 21h
           
    MOV DL, 0Dh
    INT 21h
    MOV DL, 0Ah
    INT 21h  
    MOV DL, d
    INT 21h
           
    MOV DL, 0Dh
    INT 21h
    MOV DL, 0Ah
    INT 21h  
    MOV DL, e
    INT 21h
           
    MOV DL, 0Dh
    INT 21h
    MOV DL, 0Ah
    INT 21h  
    MOV DL, f
    INT 21h
    

    
    MOV AH, 4CH
    INT 21H
    
ENDP MAIN
END MAIN
```

## Task 3
Write a program to draw a 10*10 solid box of star.

Sample Execution
```
**********
**********
**********
**********
**********
**********
**********
**********
**********
**********
```
```asm
.MODEL small
.STACK 100H
.DATA    
MSG db '**********', 0dh, 0ah,'$'
.CODE
MAIN PROC 
    MOV AX, @DATA
    MOV DS, AX  
    
    mov ah, 9
    lea dx, msg
    int 21h     
    int 21h  
    int 21h  
    int 21h  
    int 21h  
    int 21h  
    int 21h   
    int 21h  
    int 21h      
    int 21h    
    

    
    MOV AH, 4CH
    INT 21H
    
ENDP MAIN
END MAIN
```


## Task 4
Write a program to draw a 10*10 hollow box of stars

Sample Execution
```
**********
*        *
*        *
*        *
*        *
*        *
*        *
*        *
*        *
**********
```
```asm
.MODEL small
.STACK 100H
.DATA    
MSG db '**********', 0dh, 0ah,'$'   
MSG2 db '*        *', 0dh, 0ah,'$'
.CODE
MAIN PROC 
    MOV AX, @DATA
    MOV DS, AX  
    
    mov ah,9
    lea dx, msg  
    int 21h 
    lea dx, msg2 
    int 21h 
    int 21h 
    int 21h 
    int 21h 
    int 21h 
    int 21h 
    int 21h 
    int 21h 
    lea dx, msg 
    int 21h 
             
             
    
    MOV AH, 4CH
    INT 21H
    
ENDP MAIN
END MAIN
```


## Task 5
Write a count-controlled loop to display a row of 80 stars
```asm
.MODEL small
.STACK 100H
.DATA    
.CODE
MAIN PROC 
    MOV AX, @DATA
    MOV DS, AX  
    
    mov cx, 80  
    mov ah, 2
    mov dl, '*'

label1:  
    int 21h
    loop label1  
             
             
    
    MOV AH, 4CH
    INT 21H
    
ENDP MAIN
END MAIN
```


## Task 6
Write a program to draw a 10*10 solid box of star using loop.
```asm
.MODEL small
.STACK 100H
.DATA    
MSG db '**********', 0dh, 0ah,'$'
.CODE
MAIN PROC 
    MOV AX, @DATA
    MOV DS, AX  
    
    mov cx, 10
    mov ah, 9
    lea dx, msg
label:
    int 21h
    loop label    
    

    
    MOV AH, 4CH
    INT 21H
    
ENDP MAIN
END MAIN
```

## Task 7
A basic while (1) loop
```asm
.MODEL small
.STACK 100H
.DATA    
MSG db '**********', 0dh, 0ah,'$'
.CODE
MAIN PROC 
    MOV AX, @DATA
    MOV DS, AX  

label:    
    mov ah, 1
    int 21h
    mov dl, al 
    sub dl, 20h
    mov ah, 2
    int 21h
    mov dl, 0dh
    int 21h
    mov dl, 0ah
    int 21h  
    
    jmp label
  
    

    
    MOV AH, 4CH
    INT 21H
    
ENDP MAIN
END MAIN
```

## Task 8
Loop without use of loop instructions.
```asm
.MODEL small
.STACK 100H
.DATA    
MSG db '**********', 0dh, 0ah,'$'
.CODE
MAIN PROC 
    MOV AX, @DATA
    MOV DS, AX  

    mov bl, 5
    mov ah, 2
    mov dl, '*'   
 label1:   
    int 21h
    sub bl, 1
    jnz label1       

    
    MOV AH, 4CH
    INT 21H
    
ENDP MAIN
END MAIN
```

## Task 9
Write a program to take a hexadecimal, A-F as input and print its equivalent decimal in the next line.

Sample Execution
```
A-10
B-11
C-12
E-13
F-14
```
```asm
.MODEL small
.STACK 100H
.DATA    
MSG db '**********', 0dh, 0ah,'$'
.CODE
MAIN PROC 
    MOV AX, @DATA
    MOV DS, AX  

label1:      
    mov ah, 1
    int 21h 
    mov bl, al
    
    mov ah, 2
    mov dl, '-'
    int 21h
    mov dl, '1'
    int 21h
    mov dl, bl 
    
    ;sub dl, 11h
    sub dl, 'A'
    add dl, '0' 
    
    int 21h
    
    mov dl, 0dh
    int 21h
    mov dl, 0ah
    int 21h

    jmp label1       

    
    MOV AH, 4CH
    INT 21H
    
ENDP MAIN
END MAIN
```

## Task 10 (Example 6.1) [If-else structure]
Suppose AX and BX contain signed numbers. Write some code to put the biggest one in cx.
```asm
.MODEL small
.STACK 100H
.DATA    
MSG db '**********', 0dh, 0ah,'$'
.CODE
MAIN PROC 
    MOV AX, @DATA
    MOV DS, AX  

    
    mov ax, 100h
    mov bx, 99h       
    
    cmp ax, bx
    jge l1
    jl l2

l1: 
    mov cx, ax
    jmp l3
l2:          
    mov cx, bx
l3:                    

    
    MOV AH, 4CH
    INT 21H
    
ENDP MAIN
END MAIN
```

## Task 11 (Example 6.2) [If-then structure]
Replace the number in BX by its absolute value.
```asm
.MODEL small
.STACK 100H
.DATA    
MSG db '**********', 0dh, 0ah,'$'
.CODE
MAIN PROC 
    MOV AX, @DATA
    MOV DS, AX  

    mov bx, -10
    cmp bx, 0
    jg l1     
    neg bx
l1:
    
    
    MOV AH, 4CH
    INT 21H
    
ENDP MAIN
END MAIN 
```

## Task 12 
Write a program to (a) display "?", (b) read three initials,(c) display them in the middle of an 11 x 11 box of asterisks.
Sample Execution
``` 
?ABC
***********
***********
***********
***********
*****A*****
*****B*****
*****C*****
***********
***********
***********
***********
```

```asm
Solution to be done by students
```

## Task 13 
Draw a 10*10 box of stars without using any string. Use only flow control instructions and loop to draw the box.
Sample Execution
``` 
**********
**********
**********
**********
**********
**********
**********
**********
**********
**********
```

```asm
Solution to be done by students
```

## Tasks to be done by students
1. Task 12: Write a program to (a) display "?", (b) read three initials,(c) display them in the middle of an 11 x 11 box of asterisks.
2. Task 13: Draw a 10*10 box of stars without using any string. Use only flow control instructions and loop to draw the box.

## [Watch Class video Here](https://www.youtube.com/watch?v=fuDa-me44AQ)
