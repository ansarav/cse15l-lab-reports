<h1 align="center"> <mark style="background-color: #7fb81d ; color: white; font-size: 30px; font-family:Courier;"> <b> Change 1: Empty Array showing up us Empty [] </b> </mark> </h1>

## 📸Picture of code change: 
 <img src="r3.png">  
 
## 🔗Link to Test file for *failure-inducing input* 
[Test File: Empty Array](https://github.com/ansarav/markdown-parse/blob/8e4f3b942398ade970ef879c25437bec2c30cc13/Empty-test-file.md)


## 🤪Symptom (*commit history/ terminal* )


## 2-3 Sentences: Relationship between ❤bug💔Symptom💖Failure Induced Input





<h1 align="center"> <mark style="background-color: #7fb81d ; color: white; font-size: 30px; font-family:Courier;"> <b> Change 2: Links Missing Characters ), (, [,] </b> </mark> </h1>


## 📸Picture of code change: 
 <img src="r3.png">  
 
## 🔗Link to Test file for *failure-inducing input* 
[Link](https://www.example.com)


## 🤪Symptom (*commit history/ terminal* )


## 2-3 Sentences: Relationship between ❤bug💔Symptom💖Failure Induced Input



<h1 align="center"> <mark style="background-color: #7fb81d ; color: white; font-size: 30px; font-family:Courier;"> <b> Change 3: Only adding Links that are "valid" </b> </mark> </h1>
## 📸Picture of code change: 
 <img src="c3.png">  
 
## 🔗Link to Test file for *failure-inducing input* 
[Test File: Remove Entry with "NotYet" inside []](https://github.com/ansarav/markdown-parse/blob/ad55c1e455ace2ae06aa713e39992ae7df71728e/MaybeLink.md)


## 🤪Symptom (*commit history/ terminal* )
<img src="c4.png"> 


## 2-3 Sentences: Relationship between ❤bug💔Symptom💖Failure Induced Input

> My fault for coding "==" instead of ".equal" when checking the if condition of the link having "NotYet" inside the bracket, was the bug. This bug was made aware to us by the Symptom of not providing the correct output( the body of the if statement did not work despite meeting the condition). The failure Induced Input was ```[NotYet]( DoNotAddThisLink.com)``` the code failed, we knew th bug was near the most recently edited portions. 