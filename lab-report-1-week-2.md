<h1 align="center"> <mark style="background-color: #7fb81d ; color: white; font-size: 30px; font-family:Courier;"> <b>  👩🏾‍💻How To Log Into a Course-Specific Account on ieng6 </b> </mark> </h1>




<h1 align="center"> Installing VScode </h1>

**Go to [Visual Code](https://code.visualstudio.com/)** 
* Click the downward arrow in the blue box and choose the operating system you have:
  * macOS
  * Windows
  * Linux  
  
  <img src="VSC.png" >  
  
  <img src= "VSC1.png">


* Agree with the Licence Terms 

> VScode aloows us to connect to a remote server which we will see below


      


 <h1 align="center"> Remotely Connecting</h1>



> 🎆Extra Step for **Window** users: We will Install Open SSH via the settings within your laptop/computer:
> * Click the windows logo at the bottom left of your screen. 
> * Then click "Settings" it's the second to last button on the sidebar 
>
>   <img src="R1.png">  
>
>  * On the left side click on "Apps"
>
>  <img src="r2.png">
>
>  *  "Apps & Features" pops up. Click "Optional Features" 
>
>   <img src="r3.png">
>
>  * Install OpenSSH Client and openSSH Server
>  * First check if already installed by typing the names in "Installed Featues" 
> * If not found, proceed to "Optional Features" and type in each feature's name one at a time. Click install 

> <img src="r4.png">

<mark> For further information check out [this website](https://docs.microsoft.com/en-us/windows-server/administration/openssh/openssh_install_firstuse) </mark>



**Loook Up course-specific account [here](https://sdacs.ucsd.edu/~icc/index.php)**

* Login with your UCSD info
* You will have to change your password and wait about 15 minutes to let it "Activate" 
* Look under **Additional Accounts** to your corresponding class the grayish block is important and personal to you  

<img src="r9.png">

> ❗❗❗The last **three** letters are for you specifically, don't forget it when typing in terminal @ VSCode ❗❗❗ 

* Open VScode and click terminal-->New Terminal  
* In the terminal enter your course-specific account, which we found two steps ago 

**Note :**   
<mark> If it's your first time login in, it will ask you if you want to continue. In which you say yes </mark> 

* Type your password
  
> It will be invisible for your protection


<img src="r10.png">

<h1 align="center">Trying Some Commands</h1>

* Try the following commands  on **your** computer (non course-specific account) and on the **remote** computer (yes the cse15l--- one)
 > For **remote** computer make sure you start your command with 👉🏾**ssh**👈🏾  
   * ```cd ..  ```
   * ```dir```
   * ```cd <file name> ```
   * ```exit```
   * ```clear```
   

   > These commands help you move from one folder to the sub folder to the sub-sub folders.etc

  
| <mark style="background-color: #7fb81d ; color: white; font-size: 30px; font-family:Courier;"> **Your** Computer </mark>           |<mark style="background-color: #7fb81d ; color: white; font-size: 30px; font-family:Courier;"> **Remote** Computer  </mark>                              |
| ------------------------- | ------------------------------------------------ |
|<img src="regularCPU.png" >| <img src="remote.png" width="100%" height="100%">|

 




<h1 align="center">Moving Files with scp</h1>

> Think of it like when you need access to a picture yout took of your receipt but now you want to access that picture from another device so you email yourselve because you can log in to email anywhere with any device as long as you have the password to that device 💻

* Create a file <NameOfFile.java> with the follOwing content on **your** computer (thus❌ not ieng6, but✅powershell on terminal):  

> **Note:** to create a file you need to first open/create a folder 
 
``` java

class NameOfFile {
  public static void main(String[] args) {
    System.out.println(System.getProperty("os.name"));
    System.out.println(System.getProperty("user.name"));
    System.out.println(System.getProperty("user.home"));
    System.out.println(System.getProperty("user.dir"));
  }
}

 ```



* Run: ```javac``` and ```java```    




<img src="20.png">


* In same terminal type following command:
``` scp NameOfFile.java cs15lwi22zz@ieng6.ucsd.edu:~/```



<img src="scp.png">


> **Note**: the start of the command is scp  s-c-p not ssh s-s-h, but it will give the same step of asking for the password.


> p.s you just copy pasted the file from A to B computer . yay🎉


* Now, go *into* **ssh** 
``` ssh cs15lwi22zzz@ieng6.ucsd.edu```
* type command ``` ls  ```
* and uuuuu there it is, the file you copied 
* *Now* run file on **remote** computer ```javac``` and  ```java```

> This is like accepting it and making it official on the **remote** computer

<img src="run.png" width= "100%">

  




<h1 align="center">Setting an SSH Key</h1>

When trying to get access to our *remote* computer we have to enter the password each time. So we can use ```ssh-keygen``` to make a **public** key (on server *remote* computer) and **private** key (client, *your* computer)

> File with the ending ```.pub``` are public whereas those that don't have that are private 


* On **client** computer type the following command: ```ssh-keygen ssh```

* Then it will ask you to enter file. You can either just type "enter" or can insert the path as in ```/Users/audri/.ssh/id_rsa.pub```

* Enter passphrase of choice
<img src="yay.png">

> 🎆 Extra Step for **Windows** users ```ssh-add``
> * with ```ssh-add``` user private key will be stored 
>
>   * First need to change features in settings follow instruction from [StacOverflow](https://stackoverflow.com/questions/18683092/how-to-run-ssh-add-on-windows) 
>
>   * on terminal type ```ssh-add  <NameOfFileInWhichYouSavedTheKeyInPreviousStepWhenSsh-keygen>```
>
>   ![Image](added.png)


Two new files made: 
1. File ``` id_rsa``` contains the private key 
2. File ```id_rsa.pub``` contains the public key, which is stored in the remote computer



* Now we need *Copy* **public** key to to remote server 

``` java
ssh cse15lwi22zzz@ieng6.ucsd.edu
<Enter Password>
#now on server
$ mkdir .ssh
$ <logout>
# back on client
$ scp /Users/<name>/.ssh/id_rsa.pub cs15lwi22@ieng6.ucsd.edu:~/.ssh/authorized_keys
# You use your username and the path you saw in the command above
```

![Image](FileExists.png)



> $ <Logout> just means type out "exit"

```scp  \Users\audri/.ssh/id_rsa.pub cs15lwi22aja@ieng6.ucsd.edu:~/.ssh/authorized_keys```


``` scp <path> <username of course>:`/ .ssh/authorized_keys```

![image](logout.png)

> **Note:** This is important because previously it is asking you to enter server ssh and then by doing scp you are also trying to login again, so becasue you didn't exit between this steps it causes problems





<h1 align="center"> Optimizing Remote Running</h1>
    

* Because now you can ssh and scp from clinet to server without having to halt each time by inserting password, **remote running** takes less time  

```$ ssh <username> "ls" ```


 ```$ ssh <username> "cd.."```

* First edit a file in the client computer ex: ```NameOfFile.java``` 


> **Maximize Space** 
>  * You can run multiple commnads in a single line🤩
>  * This compiles and runs it and identifies files
> ``` $ cp NameOfFile.java OtherMian.java;```
>  ```javac OtherMain.java;```
>  ```java NameOfFile.java ```



> **Shortcut**
> * The most recent command you run will appear by clicking the Up arrow 
> * To delete it just click the down arrow

![Image](nopass.png)







![gif](dancing.gif)








