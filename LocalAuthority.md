# Description

Can you get the flag? <br>
Go to this website and see what you can discover.

# Solution

In the page source you can see the login post request is using "login.php" file.

![image](https://user-images.githubusercontent.com/91398631/236641131-c25a1d48-46df-4fc1-9b47-aa0381a7737d.png)

However in the sources tab it is not listed.

![image](https://user-images.githubusercontent.com/91398631/236641149-04d5daea-c0e8-4bf0-b1d1-33266d9069d5.png)

So I just went to ```http://saturn.picoctf.net:64710/login.php``` and now files appeared in the source.

![image](https://user-images.githubusercontent.com/91398631/236641170-f16f2655-12df-43a7-93d5-5bebee028e5c.png)

In the login.php you can see some filtering and a hash but neither of these things help with logging in. But if you look at another file in the sources tab and shown at the top of the login.php code:

![image](https://user-images.githubusercontent.com/91398631/236641220-a7a330a7-bc05-4f0e-bebf-de03b3888156.png)

You can see a file called "secure.js".

![image](https://user-images.githubusercontent.com/91398631/236641230-5bed6648-c150-4dc9-b4fa-ea1b4693398c.png)

This file justs shows that user and password in plaintext. So I now went back to the orginal path of the website with the given credentials. This directed me to ```http://saturn.picoctf.net:64710/admin.php``` where the flag was located.

![image](https://user-images.githubusercontent.com/91398631/236641256-0d86040f-4c94-4845-af5d-a1dd78d99e13.png)

Flag: ```picoCTF{j5_15_7r4n5p4r3n7_b0c...}```
