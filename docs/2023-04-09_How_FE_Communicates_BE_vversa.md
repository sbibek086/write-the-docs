---
layout: default
title: client ↔ server
category: SoftwareDev
tags: [SoftwareDev]
---

![image](https://github.com/sbibek086/write-the-docs/assets/11883023/3cf6a54b-c284-4508-a95e-5a64e3c1d2be)

---
![image](https://user-images.githubusercontent.com/11883023/204149982-9e96a0fd-e659-4d83-adcb-b93332af2aff.png)

![image](https://github.com/user-attachments/assets/acb5519d-adbe-4c76-b1a0-9311a5596d35)

![image](https://github.com/sbibek086/write-the-docs/assets/11883023/f538f281-a4e0-4e47-b72f-d68191ddfdb5)

But its much more: [PostmanTuts](https://www.youtube.com/watch?v=LafF2-k45v0)

---
![1672472687948](https://user-images.githubusercontent.com/11883023/235312765-84dc496e-1eea-4642-8a4a-53d9f1f1f0b9.jpg)
in console, Network is where we can see which url is requested when we click Action button. So, as we can see in blue color, when we click 'Forgot Pw' button, that url is triggered as seen in RHS network tab. 

and in LHS, we can see what to response with when {certain URL is called} aka {API endpoint}. So, LHS here is backend API docs built in Django by Backend-ers

---
.env folder lets you default-ize what path we want our tail URL to append with base path URL. That base path url is menioned in .env folder.
.env may have more things than just base path urls. 

Not only this, .env folder has other purposes too, as clarified from below

![image](https://github.com/sbibek086/write-the-docs/assets/11883023/68a02270-1710-4ddd-abf6-41778fe16ed4)

_Also, we have to do git pull everytime after we do git checkout branchNewlyDevelopedFeature because I remember that one day, I couldnt deploy correctly because my to-go-and-deploy 
branchNewlyDevelopedFeature should have had .env updated._

```
dyk that .gitignore - whatever we put in it, is ignored by git. 
They are not put in burden to git by git. 
Such folders we want to put in .gitignore could be packages, 
which are installed on press of npm install etc.

git fetch --all fetches or pulls updates not only from current branch 
but from all branches in that repo.
```
---
.eslint.config.json - whatever stds we set for linting has to be followed as protocol in order to be valid. eg. if 'feat' is in eslint.config.json, then our git cmd should obey that language protocol like _git commit  -m "feat: feature of drop down menu fixed in this Pull Req"_ otherwise, compiler wont compile this git

.prettier.config.json - same context as .eslint but here it's to standardize beauty aesthetics of code, that coder should follow - like how much spaces betn two codeblocks.

dyk that Fe developers that among breakpoints like that of tablet, mobile, computer screen, React's minimum query only mentions css and flex specifics for <= minimum pixel width. Above pixel width has default css and flex design. this para deserves another post soon on Fe which I had been preparing

---
Its implementation in Elastic-Search I did;

![Untitledddddddddd](https://user-images.githubusercontent.com/11883023/265220150-7a64d2ea-75b5-4dc4-9d05-5c247750e63c.png)
