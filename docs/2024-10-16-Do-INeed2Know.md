---
layout: default
title: Do I need to know all b4 + K's mid-tier??..
category: Cryptography
tags: [Cryptography]
---

We are victims of our own faulty habits and thought patterns. So, I spent most of my 20s in pressure cooker conventional exam conditions, which demand that you need to know all formulas by heart (what rubbish?), all principles like second natured. So, it shaped my preconditioning in such a way that I need to know all parts by heart before I dare to wet my feet in problem solving ocean. 
     But real world or lets be confined to programming challenges does not work like that. We need to have that problem solving methodology - thats it. Lots of knows are learnt while on the flow of problem solving. Tho I breathe it consciously, my subconscious brain masks me - Vivek, you need to know all parts beforehand, you need to know all parts beforehand.
    Below conversation exemplifies this - post-er seems to be know-it-all-before kind of guy and commenter is not.
    
![image](https://github.com/user-attachments/assets/e10752ee-bbde-478a-bc96-397f9880b849)

---

![image](https://github.com/user-attachments/assets/693010cc-33cb-4b31-bb64-36a07355cb1b)

Detailed application:
Sure! Let’s imagine you’re working on a project where you’re developing an API for a machine learning model on Kaggle.

### Project Situation

**Goal**: You need to add a new endpoint to your API that provides predictions from the machine learning model.

### Steps

1. **Set Up Your Development Environment**:
   - You have a **Kaggle mid-tier development environment** already set up on your local machine. This means you have all the necessary tools and libraries ready to go.

2. **Run Kaggle in a Container**:
   - You start a **container** that runs Kaggle. This is like creating a separate workspace where everything related to the project is contained.

3. **Develop Your API**:
   - Inside the container, you create a new endpoint in your API, let's say `/predict`, which will accept input data and return model predictions.

4. **Test Your Code**:
   - You write some Python code to handle requests to this new endpoint. You can now test this code within the container to see if it correctly connects to your model and provides predictions based on the input data.

5. **Avoid Final Releases in the Container**:
   - Once your code is working and tested, you’re ready to prepare a release. However, you remember the warning about `yapf3`. If you try to create a final version of your code while still inside the container, `yapf3` might change more of your code than you intend, potentially introducing bugs or formatting issues.
   - Instead, you exit the container and make your final adjustments and formatting in your regular development environment.

6. **Create the Release**:
   - Finally, you create the release from your regular environment where you have full control over the code changes, ensuring everything is formatted as you expect.

### Summary
- **Develop and test** inside the container to ensure your code works well with the Kaggle setup.
- **Create the final release** outside the container to avoid unwanted changes from the code formatter.

This approach helps you maintain a clean and functional codebase while allowing for effective development and testing.
