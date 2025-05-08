# NEUB CSE Microprocessor and Interfacing Lab Spring 2025 Lab 2

Start of assembly language lab before hardware are ready.


## Task 1
Basic Structure of 8086 Assembly code and printing characters
```asm
.MODEL small
.STACK 100H
.DATA
.CODE
MAIN PROC    
    MOV AH, 2 
    MOV DL, 041H ;A
    INT 21H         
    ;Printing a new line
    MOV DL, 0AH
    INT 21H
    MOV DL, 0DH
    INT 21H
    
    MOV DL, 042H ;B
    INT 21H        
    ;Printing a new line
    MOV DL, 0AH
    INT 21H
    MOV DL, 0DH
    INT 21H     
     
    MOV DL, 043H ;c
    INT 21H     
    
    ;Printing a new line
    MOV DL, 0AH
    INT 21H
    MOV DL, 0DH
    INT 21H    
    MOV DL, 'a'
    INT 21H        
    
    MOV AH, 4CH
    INT 21H
    
ENDP MAIN
END MAIN
```

## Task 2
Input and output of characters
```asm
.MODEL small
.STACK 100H
.DATA
.CODE
MAIN PROC  
    MOV AH, 1
    INT 21H  
    
    MOV BL, AL     
    
    MOV AH, 2
    MOV DL, 0AH
    INT 21H
    MOV DL, 0DH
    INT 21H
    
    MOV DL, BL
    INT 21H

    
    MOV AH, 4CH
    INT 21H
    
ENDP MAIN
END MAIN
```

## Task 3
Printing a string (`HELLO THERE`) the hard way
```asm
.MODEL small
.STACK 100H
.DATA
.CODE
MAIN PROC  
    MOV AH, 2        
    MOV DL, 'H'
    INT 21H       
    MOV DL, 'E'
    INT 21H     
    MOV DL, 'L'
    INT 21H    
    MOV DL, 'L'
    INT 21H     
    MOV DL, 'O'
    INT 21H     
    MOV DL, ' '
    INT 21H   
    MOV DL, 'T'
    INT 21H    
    MOV DL, 'H'
    INT 21H  
    MOV DL, 'E'
    INT 21H     
    MOV DL, 'R'
    INT 21H     
    MOV DL, 'E'
    INT 21H

    
    MOV AH, 4CH
    INT 21H
    
ENDP MAIN
END MAIN
```


## Task 4
Printing a string the easy way
```asm
.MODEL small
.STACK 100H
.DATA
MSG DB 'HELLO THERE', 0AH, 0DH, '$'   
MSG2 DB 'NORTH EAST UNIVERSITY BANGLADESH', 0AH, 0DH, '$'   
.CODE
MAIN PROC 
    MOV AX, @DATA
    MOV DS, AX        
    
    MOV AH, 9
    LEA DX, MSG
    INT 21H  
    
    ;MOV AH, 9
    LEA DX, MSG2
    INT 21H

    
    MOV AH, 4CH
    INT 21H
    
ENDP MAIN
END MAIN
```


## Task 5
Uppercase to lower case
```asm
.MODEL small
.STACK 100H
.DATA
MSG DB 'Enter a character in uppercase: $'   
MSG2 DB 'In lowercase it is: $'     
NEWL DB 0Ah, 0Dh, '$'
.CODE
MAIN PROC 
    MOV AX, @DATA
    MOV DS, AX        
    
    MOV AH, 9
    LEA DX, MSG
    INT 21H       
    
    MOV AH, 1
    INT 21H
    MOV BL, AL    
    
    MOV AH, 9
    LEA DX, NEWL  
    INT 21H
    
    
    LEA DX, MSG2
    INT 21H   
    
    ADD BL, 20H
    MOV AH, 2
    MOV DL, BL
    INT 21H

    
    MOV AH, 4CH
    INT 21H
    
ENDP MAIN
END MAIN
```


## Task 6
Lowercase to uppercase
```asm
.MODEL small
.STACK 100H
.DATA
MSG DB 'Enter a character in lowercase: $'   
MSG2 DB 'In uppercase it is: $'     
NEWL DB 0Ah, 0Dh, '$'
.CODE
MAIN PROC 
    MOV AX, @DATA
    MOV DS, AX        
    
    MOV AH, 9
    LEA DX, MSG
    INT 21H       
    
    MOV AH, 1
    INT 21H
    MOV BL, AL    
    
    MOV AH, 9
    LEA DX, NEWL  
    INT 21H
    
    
    LEA DX, MSG2
    INT 21H   
    
    SUB BL, 20H
    MOV AH, 2
    MOV DL, BL
    INT 21H

    
    MOV AH, 4CH
    INT 21H
    
ENDP MAIN
END MAIN
```


## Task 7
Take 2 input numbers from 0-4 and print the sum of the numbers in new line
```asm
Solution to be done by students
```
## Tasks to be done by students
1. Task 7: Take 2 input numbers from 0-4 and print the sum of the numbers in new line

## [Watch Class video Here](https://www.youtube.com/watch?v=odbaVipA708)
