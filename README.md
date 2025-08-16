# functions

1. Thought Process:


<img width="471" height="191" alt="functions" src="https://github.com/user-attachments/assets/0a125644-f4bd-40bf-9d2d-a4aa95e2bd23" />





2. Challenges:

  
 
  Remembering to set up the stack frame using push ebp / mov ebp, esp.

  Avoid corrupting the return address or overwriting registers.
  
  Preserving values across the call and keeping track of what’s pushed and popped.




3. Working Code:



[even_odd.txt](https://github.com/user-attachments/files/21811113/even_odd.txt)
section .data
    even_msg db 'even', 0xA
    even_len equ $ - even_msg
    odd_msg db 'odd', 0xA
    odd_len equ $ - odd_msg

section .text
    global _start

_start:
    mov eax, 15
    push eax
    call check_even_odd
    mov eax, 1
    xor ebx, ebx
    int 0x80

check_even_odd:
    push ebp
    mov ebp, esp
    mov eax, [ebp+8]
    and eax, 1
    cmp eax, 0
    je print_even

print_odd:
    mov eax, 4
    mov ebx, 1
    mov ecx, odd_msg
    mov edx, odd_len
    int 0x80
    jmp done

print_even:
    mov eax, 4
    mov ebx, 1
    mov ecx, even_msg
    mov edx, even_len
    int 0x80

done:
    leave
    ret
  
   
   ![funct](https://github.com/user-attachments/assets/a6159d1c-04dd-4f6e-9532-6a8834192c9d)
   
   
   ![functi](https://github.com/user-attachments/assets/85911b70-4571-4397-90e3-193639a6d2e9)
