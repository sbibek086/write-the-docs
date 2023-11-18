---
layout: default
title: How F-E communicates w B-E & vversa
category: SoftwareDev
tags: [SoftwareDev]
---

![image](https://github.com/sbibek086/write-the-docs/assets/11883023/beb2beb7-e2b4-4fb7-b6b6-06e5f75a1adf)

![image](https://github.com/sbibek086/write-the-docs/assets/11883023/3cf6a54b-c284-4508-a95e-5a64e3c1d2be)

---
![image](https://user-images.githubusercontent.com/11883023/204149982-9e96a0fd-e659-4d83-adcb-b93332af2aff.png)

```
HTTP HEAD method is also there but not used day to day. So dont bother about it too much. Anyway, HEAD method requests the headers that would be returned if the HEAD request's URL was instead requested with the HTTP GET method. For example, if a URL might produce a large download, a HEAD request could read its Content-Length header to check the filesize without actually downloading the file.
```
![image](https://github.com/sbibek086/write-the-docs/assets/11883023/440543e3-a898-4afe-bbb8-3005eb0169e0)

In above double-arrows req-resp image, I thought: REQ is always in search params, apikeys AND RESPONSE is always in json. But json and other content types are just body in RESPONSE. RESPONSE also has its header.

In REST APIs, request or response message has method, URL endpoint, authentication in different formats like basic, saml, encrypted aka salted aka hashed, aws keys etc (in header) & data content-type(in Body).

Insomnia, Postman helps see all this under hood process. Kibana Client further facilitates us by condensing so many primitive steps directly in gui. For eg, to pass read write superuser previleges to some endpoint may take lots of steps in say insomnia, but kibana condenses it in few steps.

But its much more: [[PostmanTuts](https://www.youtube.com/watch?v=LafF2-k45v0)

---
![1672472687948](https://user-images.githubusercontent.com/11883023/235312765-84dc496e-1eea-4642-8a4a-53d9f1f1f0b9.jpg)
in console, Network is where we can see which url is requested when we click Action button. So, as we can see in blue color, when we click 'Forgot Pw' button, that url is triggered as seen in RHS network tab. 

and in LHS, we can see what to response with when {certain URL is called} aka {API endpoint}. So, LHS here is backend API docs built in Django by Backend-ers

---
Pow-It's-enof-for-daily-job-notes of What different status codes mean?

![image](https://user-images.githubusercontent.com/109033173/230772640-9839acaf-09ca-4bcf-9596-3aa68777275f.png)

---
.env folder lets you default-ize what path we want our tail URL to append with base path URL. That base path url is menioned in .env folder.
.env may have more things than just base path urls. 

Not only this, .env folder has other purposes too, as clarified from below

![image](https://github.com/sbibek086/write-the-docs/assets/11883023/68a02270-1710-4ddd-abf6-41778fe16ed4)

_Also, we have to do git pull everytime after we do git checkout branchNewlyDevelopedFeature because I remember that one day, I couldnt deploy correctly because my to-go-and-deploy 
branchNewlyDevelopedFeature should have had .env updated._

---
.gitignore - whatever we put in it, is ignored by git. They are not put in burden to git by git. Such folders we want to put in .gitignore could be packages, which are installed on press of npm install etc.

.eslint.config.json - whatever stds we set for linting has to be followed as protocol in order to be valid. eg. if 'feat' is in eslint.config.json, then our git cmd should obey that language protocol like _git commit  -m "feat: feature of drop down menu fixed in this Pull Req"_ otherwise, compiler wont compile this git

.prettier.config.json - same context as .eslint but here it's to standardize beauty aesthetics of code, that coder should follow - like how much spaces betn two codeblocks.

dyk that Fe developers that among breakpoints like that of tablet, mobile, computer screen, React's minimum query only mentions css and flex specifics for <= minimum pixel width. Above pixel width has default css and flex design. this para deserves another post soon on Fe which I had been preparing

dyk that git fetch --all fetches or pulls updates not only from current branch but from all branches in that repo. - as far as I remember, but have to confirm edit on next version of writing here.


