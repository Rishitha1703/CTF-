**Repetitions**  
**Overview**  
Points: 100  

**Category:** General Skills  
**Tags:** #base64  

---

**Description**  
Can you decipher the contents of this file?  

---

**Approach**  
The `enc_flag` file contains a base64-encoded string. Inspecting the file:  

```bash
$ cat enc_flag  
VmpGU1EyRXlUWGxTYmxKVVYwZFNWbGxyV21GV1JteDBUbFpPYWxKdFVsaFpWVlUxWVZaS1ZWWnVh  
RmRXZWtab1dWWmtSMk5yTlZWWApiVVpUVm10d1VWZFdVa2RpYlZaWFZtNVdVZ3BpU0VKeldWUkNk  
MlZXVlhoWGJYQk9VbFJXU0ZkcVRuTldaM0JZVWpGS2VWWkdaSGRXCk1sWnpWV3hhVm1KRk5XOVVW  
VkpEVGxaYVdFMVhSbFZrTTBKVVZXMTRWMDVHV2toalJYUlhDazFyV25sVVZXaHpWakpHZEdWRlZs  
aGkKYlRrelZERldUMkpzUWxWTlJYTkxDZz09Cg==  
```  

Using a base64 decoder:  

```bash
$ base64 -d enc_flag  
VjFSQ2EyTXlSblJUV0dSVllrWmFWRmx0TlZOalJtUlhZVVU1YVZKVVZuaFdWekZoWVZkR2NrNVVX  
bUZTVmtwUVdWUkdibVZXVm5WUgpiSEJzWVRCd2VWVXhXbXBOUlRWSFdqTnNWZ3BYUjFKeVZGZHdW  
MlZzVWxaVmJFNW9UVVJDTlZaWE1XRlVkM0JUVW14V05GWkhjRXRXCk1rWnlUVWhzVjJGdGVFVlhi  
bTkzVDFWT2JsQlVNRXNLCg==  
```  

The result is still encoded in base64, though it is slightly shorter. Considering the challenge title "Repetitions," it's evident the encoding is repeated multiple times.  

---

**Solution**  
During the CTF event, I decoded the file manually using chained `base64` commands. This approach works when the number of repetitions is manageable (six in this case):  

```bash
$ base64 -d enc_flag | base64 -d | base64 -d | base64 -d | base64 -d | base64 -d  
picoCTF{........redacted........}  
```  

For situations with a higher number of repetitions, automating the process with a simple Bash script is more efficient.  

---

**Automated Solution**  

Below is a Bash script to repeatedly decode the file until it either succeeds completely or fails:  

```bash
#!/bin/bash

file="enc_flag"  # Specify the input file
content=$(cat $file)

while true; do
    decoded=$(echo "$content" | base64 -d 2>/dev/null)
    if [ $? -ne 0 ]; then
        echo "Decoding complete. Result:"
        echo "$content"
        break
    fi
    content="$decoded"
done
```  

**How to Use:**  
1. Save the script as `decode.sh`.  
2. Make it executable with `chmod +x decode.sh`.  
3. Run the script: `./decode.sh`.  

The script decodes the file repeatedly until the final plaintext is revealed. In this challenge, the flag will appear as:  

```
picoCTF{....redacted....}  
```  

This script ensures efficient handling of higher repetition counts.
