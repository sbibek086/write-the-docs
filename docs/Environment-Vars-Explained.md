---
layout: default
title: Windows' Env,Sys,User Vars concept upgraded to 🐧's 
category: WindowsOS
tags: [WindowsOS]
---
Idc windows' shit by now but for archive: 

![image](https://github.com/user-attachments/assets/80783c00-623e-461e-b5ec-4310f3377d8e)

---
LINUX does this by: sudo nano ~/.zshrc where is saved all those variables value mapping as in Windows. 

Mine is now blank since I havent mapped values to variables as COLLEAGUE has done.

Remember, if I add new variable value mapping after sudo nano ~/.zshrc, then I need to do: source ~/.zshrc for updated zshrc to work.

but before that, letme check whether bash or zshrc or what? is activated as Env-Vars-as-I-say by echo $0 in terminal, gives bash in my ubuntu. 

Since zshrc >> bash, I'd want mine to be defaulted to zshrc, for which I'd sudo apt update n then sudo apt install zsh. 

Then, chsh -s $(which zsh) for making zsh default. Remember, this is one-time-setup n NOT everyDayConfiguring.



  



