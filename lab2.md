# 20110370, Phùng Huy Hoàng
# Lab 2: Buffer overflow attack
## I.Topic
*Inject code to delete file: file_del.asm is given on github*
 And Conduct attack on ctf.c
- This is the function myfunc 
<img width="726" alt="" src="https://github.com/huyhoangph/labs2/blob/master/assets/img/topic1.png">

- This is the function main 
<img width="726" alt="" src="https://github.com/huyhoangph/labs2/blob/master/assets/img/topic2.png">

- This is file_del.asm which is intended to delete a file in the current directory
<img width="726" alt="" src="https://github.com/huyhoangph/labs2/blob/master/assets/img/topic3.png">

## II. Implementation steps
*Run command to compile file ctf.c*
- gcc -g ctf.c -o ctf.ou -fno-stack-protector  
<img width="726" alt="Screenshot 2023-05-02 165126" src="https://github.com/huyhoangph/labs2/blob/master/assets/img/biendich.png">

*run gdb and execute the command info disassemble to know the location of the myfunc function*
- gdb ./ctf.ou
- disassemble myfunc
<img width="726" alt="" src="https://github.com/huyhoangph/labs2/blob/master/assets/img/Picture4.png">

->then we know the address of the myfunc function is 0x0804851b

*Then execute the following command to overflow the buffer and include the address of the myfunc function*
-  ./ctf.ou $(python -c "print('A' * 112 + '\x1b\x85\x04\x08')")
<img width="726" alt="" src="https://github.com/huyhoangph/labs2/blob/master/assets/img/Picture5.png">

- Buffer overflow performed successfully. The myfunc function was executed but because the flag.txt file was missing, it returned the message "flag1 is missing!". Therefore, we must create file flag1.txt to continue. Then run the command again to see if the "myfunc is reached" message appears
<img width="726" alt="" src="https://github.com/huyhoangph/labs2/blob/master/assets/img/Picture9.png">

-> As a result, the buffer overflow message occurs again







 
