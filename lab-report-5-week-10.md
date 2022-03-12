<h1 align="center"> <mark style="background-color: #7fb81d ; color: white; font-size: 30px; font-family:Courier;"> <b>  Identifying differences in output</b> </mark> </h1>

## Two testsfrom 652 tsts wher group had diff answers than lab 9   
<br>  

## diff ans = diff bugs 


>  How to find tst with diff results ( diff with bash???) I used bash 




# Test 1:  **201.md*** 

The 201.md file contains: 

```[foo]: <bar>(baz) ``` <br>


```[foo]```

## By looking at actual output vs expected output, which or is neither implentation is correct ?

My implemenation's output: ```[]```
Professor's output: ```[baz]```
Correct output: ```[]```

## For the ❌incorrect❌ implementation describe bug 

The following code updates the current index pointer to reset the code to look for a next potential link. But this "restarting" for the search of the components that makeup a valid link wll only be possible is there is a finished valid link already with just a space in the fornt `` `` and not a whole line break ```/n``` after the potential link. The bug will be located in this if statment because unless we take into account that newline and modify the code that if statement will not run and rather it would be skipped and thus the search for a possible link will be unrealiable. In the professors case, the code saw a following  openBracket closeBracket and assumed that the previous word ```baz``` was an official link

``` java 
String potentialLink = markdown.substring(openParen + 1, closeParen).trim();
if(potentialLink.indexOf(" ") == -1 && potentialLink.indexOf("\n") == -1) {
toReturn.add(potentialLink);
currentIndex = closeParen + 1;
}
```
# Test 2: **342.md**   


The 342.md file contains:
```[not a `link](/foo`)```

## By looking at actual output vs expected output, which or is neither implentation is correct ?

My implemenation's output: ```[]```
Professor's output: ```[/foo`]```
Correct output: ```[]```

## For the ❌incorrect❌ implementation describe bug 
The follwing code keeps track of the structure of how the code will recognize  a codeblock. This is the only place file where  backtick are utilized so perhaps if we take a closer look at what exactly the code does and doesn't do witht hte precesnce and abscense of backticks we might can try to figure out how to fix the bug. As we see, the end of the code block is indicated by having a space **and** tripe backticks. Thus we can see why it lmits the testing file 342 and it's becuase the code doesn't take into account single or double or anything but triple backticks. A possible manner of going about solving this bug is to  maybe set anyback ticks within codeBlocks as null or 
```java
int nextCodeBlock = markdown.indexOf("\n```");
    if(nextCodeBlock < nextOpenBracket && nextCodeBlock != -1) {
        int endOfCodeBlock = markdown.indexOf("\n```");
        currentIndex = endOfCodeBlock + 1;
        continue;     
    }
```