<h1 align="center"> <mark style="background-color: #7fb81d ; color: white; font-size: 30px; font-family:Courier;"> <b>  Identifying differences in output</b> </mark> </h1>



> I found the tests that showed diff results by using txt files ana ```diff``` just like how we learned in week 9 lab

This command is inserted within the remote server

```diff ansaravi/results.txt ~/markdown-parse/results.txt.```

<br>
<br>


<h1 align="center"> <mark style="background-color: white ; color: lime; font-size: 30px; font-family:Courier;"> <b> Test 1:   201.md </b> </mark> </h1>


## The 201.md file contains: 

> ```[foo]: <bar>(baz) ``` <br>
>
> ```[foo]```

## By looking at actual output vs expected output, which one or are neither implentations correct ?

* My implemenation's output: ```[]```
* 🤔(Incorrect) Professor's output: ```[baz]```
* Correct output: ```[]```

## For the ❌incorrect❌ implementation describe bug 

The following code updates the current index pointer to reset the code to look for a next potential link. But this "restarting" for the search of the components that makeup a valid link wll only be possible is there is a finished valid link already with just a space in the front ```  ``` and not a whole line break ```/n``` after the potential link. The bug will be located in this if statment because unless we take into account that newline and modify the code that if statement will not run and rather it would be skipped and thus the search for a possible link will be unrealiable. In the professors case, the code saw a following  openBracket closeBracket and assumed that the previous word ```baz``` was an official link

``` java 
String potentialLink = markdown.substring(openParen + 1, closeParen).trim();
if(potentialLink.indexOf(" ") == -1 && potentialLink.indexOf("\n") == -1) {
toReturn.add(potentialLink);
currentIndex = closeParen + 1;
}
```

<h1 align="center"> <mark style="background-color: white ; color: lime; font-size: 30px; font-family:Courier;"> <b> Test 2:   342.md </b> </mark> </h1>

## The 342.md file contains:
> ```[not a `link](/foo`)```


## Comparison and which one is accurate? 

* My implemenation's output: ```[]``` <br>
* 🤔(Incorrect) Professor's output: ```[/foo`]``` <br>
* Correct output: ```[]```

## For the ❌incorrect❌ implementation describe bug 
The following code keeps track of the structure of how the code will recognize  a codeblock. This is the only place file where  backtick are utilized so perhaps if we take a closer look at what exactly the code does and doesn't do witht hte precesnce and abscense of backticks we can try to figure out how to fix the bug. As we see, the end of the code block is indicated by having a space **and** triple backticks. Thus we can see why it limits the testing file 342.md and it's because the code doesn't take into account single or double or anything but triple backticks. A possible manner of going about solving this bug is to  maybe set any back ticks within codeBlocks as null or we can make helper method that counts the number of backticks or a boolean by name ```HasBacktick``` and we can pair it up or concatenate it with the  `` \n `` within ```.indexOf```. That way we keep the number of backticks general when telling the code how to recognize the bacticks.

```java
int nextCodeBlock = markdown.indexOf("\n```");
    if(nextCodeBlock < nextOpenBracket && nextCodeBlock != -1) {
        int endOfCodeBlock = markdown.indexOf("\n```");
        currentIndex = endOfCodeBlock + 1;
        continue;     
    }
```