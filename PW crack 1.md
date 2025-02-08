### **PW Crack 1**    
### **Description**  
Can you crack the password to retrieve the flag?  
Download the password checker [here](./level1.py), and ensure the encrypted [flag](./level1.flag.txt.enc) is in the same directory.  

### **Hints**  
1. To view the file in the webshell, use: `$ nano level1.py`  
2. To exit `nano`, press **Ctrl + X** and follow the prompts.  
3. The `str_xor` function does not need to be reverse-engineered for this challenge.  

### **Approach**  
Examining the script, we see on **[line 19](https://github.com/vivian-dai/PicoMini-2022/blob/main/PW%20Crack%201/level1.py#L19)** that the condition checks if `user_pw == "17ac"`.  
If the correct password `"17ac"` is entered, the program outputs the flag:  

```
Please enter correct password for flag: 17ac  
Welcome back... your flag, user:  
picoCTF{545h_r1ng1ng_7719ae74}
```

### **Flag**  
**picoCTF{545h_r1ng1ng_7719ae74}**
