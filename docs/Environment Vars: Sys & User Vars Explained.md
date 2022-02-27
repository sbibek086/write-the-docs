---
layout: default
title: Environment Vars: Sys Vars, User Vars Explained
category: WindowsOS
tags: [WindowsOS]
---
![SysVars](https://user-images.githubusercontent.com/11883023/155871140-ae196401-006d-4d6d-a436-e3a0f41126c4.jpg)

How Environment Vars as shown by red bordered in above sceens is shown there. As can be seen in red bordered dialog box, there are two types of EnvironmentVars: 
i)Sys Vars: These are wide accepted & doesnt vary from user to user (Like in one OS, you can create Admin user, Guest user etc.)

ii)User Vars: (vary from user to user) You can add your variables under your user OS account so that it has got nothing to do with other users.

Both vars work similar to registry in Windows ,and so such vars can be accessed directly with _regedit_ in cmd.
i) are evaluated after ii), which means if we have got same name i) and ii), then it will be considered user vars.
---
Also to notice is: The Path variable is generated in a different way. The effective Path will be the User Path variable appended to the System Path variable.

![SysVars2](https://user-images.githubusercontent.com/11883023/155871796-40564682-ebd3-464a-8ba1-024293be6f22.jpg)
Now, if I double click to add for eg, VScode paths as shown by orange bordered, after that if I want to run open VS code, open up Command Prompt and type in the name of the executable file that was in the folder. You can provide additional arguments if the program supports it. 

The program will run from the command prompt without actually being in the directory from where you executed the command. That is the beauty of the Path variable.