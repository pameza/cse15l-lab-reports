# Week 1 lab blog :)
During the first week's lab we were introduced to remote access through VS Code. 
## Download VS Code
Initially, we were taught to download VS Code and then gather our log-in information. To download VS Code, we accessed the [Link](https://code.visualstudio.com/docs/setup/setup-overview) to download the installer that was appropriate for our operating system and followed the instructions to download the program. 

<img width="768" alt="Screen Shot 2023-04-10 at 10 46 39 PM" src="https://user-images.githubusercontent.com/130017007/231067657-51a29287-eb0c-4133-bf66-1fd35a92d02a.png">

## Run commands locally
Now that VS Code is running, we are able to run some commands such as the following:
- `cd ~` 
- `cd`
> `cd` stands for "Change Directory", changing the current working directory to whatever follows `cd`. This can be checked by running `pwd`. When`~` is added, it referst to the home directory.
- `ls -lat`
- `ls -a`
> `ls` is refered to as "list" since it returns a list of files and directories contained in your curent directory.
- `cat ~/documents/hello.txt`
> `cat` is short for concatenate. Its fuction is to print the contents of a file(or multiple files) to the terminal.

this commands ran on my computer and generated some lines that referred to my current directory and the folders containing it. 
<img width="600" alt="Screen Shot 2023-04-24 at 8 49 07 PM" src="https://user-images.githubusercontent.com/130017007/234170423-9904cb40-b31f-4845-a311-953bb8181128.png">


## Run commands using the server
In order to run these commands on the server, I had to follow several steps to find my log in information. First, I found my username by follwoing the instructions in this [Link](https://sdacs.ucsd.edu/~icc/index.php) and plugging in said username in the blanks of this `ssh _____@ieng6.ucsd.edu` inside of the terminal. To access the terminal, click Terminal - New Terminal in the top bar. I used the password reset tool to get a new password for this assignment and waited a little over 30 minutes to continue. After this, I was asked if I wanted to continue and I typed "yes". Then, I was asked for my password and upon writing my password, I was able to access the remote server where I could once again type the commands mentioned above, yielding a different result this time.
- `cp /home/linux/ieng6/cs15lsp23/public/hello.txt ~/`
> This command creates a copy of the specific path given and places it in the given location. In this case, it grabs `hello.txt` and places it in the user's home directory in the server.
<img width="1085" alt="Screen Shot 2023-04-24 at 8 41 03 PM" src="https://user-images.githubusercontent.com/130017007/234170446-21cfd689-e2e8-4b18-87d2-02e6dbadc99a.png">

<img width="814" alt="Screen Shot 2023-04-10 at 11 14 33 PM" src="https://user-images.githubusercontent.com/130017007/231072140-4f46df2e-920c-431b-92a0-02202acfc938.png">

# Using character `|` for _hiding_ emoticons makes them look like if they are peeping from behind the wall hiding from somebody.
```
- |･д･)ﾉ
- |ω･)ﾉ
- |･ω･)
- ┬┴┬┴┤( ͡° ͜ʖ├┬┴┬┴
```
1. (^◕ᴥ◕^)
2. (^=◕ᴥ◕=^)
3. ฅ(^=◕ᴥ◕=^)ฅ

---
## More cats:
**Cat GPT**
[Link](https://cat-gpt.com/)
