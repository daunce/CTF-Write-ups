pwn/flip-out

237 solves / 14 points

My friend made this app with a flag in it...

nc tjc.tf 31601

Downloads: chall

Running `chall` locally:
```bash
$ ./chall
Input: 2
thing to see here... Nothing to see here...  
```

Loading it into Ghidra, it looks to read in flag.txt and check if the input is less than 0x81 (129).

```bash
└─$ echo "Test flag" >flag.txt
```


```c
    if ((int)uVar1 < 0x81) {
      printf("%s",(long)&local_b8 + (long)(int)(uVar1 & 0xff));
```

Indeed if I put in values of 130, it provides no output. Trial and error, putting in 128 it prints out my test flag.

Remembering that there's a remote server to send it to:

```bash
─$ nc tjc.tf 31601
Input: 128
tjctf{chop-c4st-7bndbji}  
```

Flag: tjctf{chop-c4st-7bndbji}  


