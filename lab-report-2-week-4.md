<h1 align="center"> <mark style="background-color: #7fb81d ; color: white; font-size: 30px; font-family:Courier;"> <b> Change 1: Empty Array showing up us Empty [] </b> </mark> </h1>

## 📸Picture of code change: 
<img src="&.png">  
I forgot to save take a picture of when I commited the change at the beginning but the change was adding 

```

if(nextOpenBracket == -1 && nextCloseBracket == -1 && openParen == -1 && closeParen == -1){
     return toReturn;
}   
```
 
 
## 🔗Link to Test file for *failure-inducing input* 
[Test File: Empty Array](https://github.com/ansarav/markdown-parse/blob/8e4f3b942398ade970ef879c25437bec2c30cc13/Empty-test-file.md)


## 🤪Symptom (*commit history/ terminal* )
<img src="Term.png">  

## 2-3 Sentences: Relationship between ❤bug💔Symptom💖Failure Induced Input
The <mark style="background-color: white ; color: black;"> Symptop </mark>   was that the program had an output IndexOutOfBounds Exception due to a <mark style="background-color: white ; color: black;"> bug </mark>    in the while loop. But because we had nothing at all in the test file (Empty) this <mark style="background-color: white ; color: black;"> Failure Induced Input </mark>   although simple, allows us to see that the test codes are crucial to fill an array. With this information we allow an array to be created even with 0 elements created 


<h1 align="center"> <mark style="background-color: #7fb81d ; color: white; font-size: 30px; font-family:Courier;"> <b> Change 2: Links Missing Characters ), (, [,] </b> </mark> </h1>


## 📸Picture of code change: 
<img src = "or.png">

```
if(nextOpenBracket == -1 || nextCloseBracket == -1 || openParen == -1 || closeParen == -1){
                return toReturn;
            } 
```
 
## 🔗Link to Test file for *failure-inducing input* 
[Test File: MissingChar ")"](https://github.com/ansarav/markdown-parse/blob/9d11a96f9f99001a15a5191b1ca093210a74b74a/MissingChar-test-file.md)


## 🤪Symptom (*commit history/ terminal* )


![image](LeFalta.png)
 

 vs Fixed👇🏾


 <img src= "fixed.png">

## 2-3 Sentences: Relationship between ❤bug💔Symptom💖Failure Induced Input
The <mark style="background-color: white ; color: black;"> Failure Induced Input </mark> `[words](hmmm` points out that in our code, incomplete link syntax are not considered/counted as an element, but there will still have to be an Array [] output at the very least. The IndexOutBoundExeption was a <mark style="background-color: white ; color: black;"> symptop </mark>  of the <mark style="background-color: white ; color: black;"> bug</mark>   found inside the while loop where there was only consideration for complete link syntax.


<h1 align="center"> <mark style="background-color: #7fb81d ; color: white; font-size: 30px; font-family:Courier;"> <b> Change 3: Only adding Links that are "valid" </b> </mark> </h1>
## 📸Picture of code change: 



 ![image](C3.png)
 
## 🔗Link to Test file for *failure-inducing input* 
[Test File: Remove Entry with "NotYet" inside []](https://github.com/ansarav/markdown-parse/blob/9d11a96f9f99001a15a5191b1ca093210a74b74a/MaybeLink.md)


## 🤪Symptom (*commit history/ terminal* )
<img src="C4.png"> 


## 2-3 Sentences: Relationship between ❤bug💔Symptom💖Failure Induced Input

My fault for coding "==" instead of ".equal" when checking if's condition when the link has "NotYet" inside the bracket, was the bug. This <mark style="background-color: white ; color: black;"> bug </mark>led to the<mark style="background-color: white ; color: black;"> symptom </mark>of it not giving the correct output( the body of the if statement did not work despite meeting the condition). The <mark style="background-color: white ; color: black;"> failure Induced Input </mark>   was ```[NotYet]( DoNotAddThisLink.com)``` the code failed, we knew the bug was near the most recently edited portions. 

![gif](Lab2yay.gif)