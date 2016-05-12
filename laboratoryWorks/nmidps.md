---
layout: default
title: MIDPS
---
##Laboratory Work No.3

The task for the third laboratory work was to create a pomodoro like app. In order to perform this laboratory work I had to deal with learnig the basic android concencepts, the life cycle of an application, ect. The hardest part was ingnoring all the facebook, twitter and telegram notifications. But in the end, I did it! Yey!
<br />
The first step in order to create a super fancy pomodoro app, was to learn, to get into what android is, and how to eat it. Here I met Advik Kabir: 

<div class="custom-image"><img src="http://vomzi.com/wp-content/uploads/2016/03/indian-gif-852.gif" /></div> 
No, not this, the other one:
<div class="custom-image"><img src="http://s2.djyimg.com/n3/eet-content/uploads/2014/02/Indian-head-shake.gif" /></div> 

The next step was to choose a fancy bakground for my app. The following images were candidates for my app:

<div class="custom-image"><img src="http://cdn.newsday.com/polopoly_fs/1.3718944.1337353874!/httpImage/image.JPG_gen/derivatives/display_600/image.JPG" /></div> 
<div class="custom-image"><img src="http://bemol.md/wp-content/uploads/2015/08/causeni.jpg" /></div> 
<div class="custom-image"><img src="http://dogr.io/doge.png" /></div> 
 
In fact, none of this photos were used. The background of my app, looks as serious as the name of my app: "SeriousPomodoro".

<div class="custom-image"><img src="https://66.media.tumblr.com/3d95b05a3bd554e5656a5c216b9fe4f4/tumblr_o72zz02b2i1rl36tko2_1280.jpg" /></div> 

As you see, I downloaded 2 different fonts, in order to make the app look better, and to make every user feel excited about the app.

A new intend was created in the second activity, were the actual "focus mode" can be reached.
<div class="custom-image"><img src="https://66.media.tumblr.com/31d8cd9446e5d06315235dd15b44e8bf/tumblr_o72zz02b2i1rl36tko1_1280.jpg" /></div> 

The source code of the laboratory work can be found <a href="https://github.com/dianaartiom/pomodor'">here</a>.


###Conclusion: 
In this laboratory work we developed(or better saying - initialised) our mobile programming skills. It was a great amount of information, for some of us maybe even challenging, but it was worth it. The things I liked the most was the project architecture. You`re splitting your UI with your bussines logic, without even thinking you are doing it, an that`s kinda cool. Another thing I got in touch with was multithreading. The first iteration my code contained multiple threads, but I decided I have to improve my threading experience first, and then present a lab with it inside. But anyway, I spend some days on trying to understand what this is for, how to use it, and I`m ready to try implementing. I still feel motivated to do tasks and to proceed to the next point in my laboratory work journey. =) 
<br />
P.S. Ask me for an demo. :)


##Laboratory Work No.2

In this laboratory work we had to create a travelling in time machine. To perform this laboratory work I used the following equipment:
<ul>
	<li><div class="custom-image"><img src="https://41.media.tumblr.com/6d829fd1563557a0370daee8590c5366/tumblr_o5amuvS6vG1udztn8o1_540.jpg" /></li>
	<li>A tanc
	<div class="custom-image"><img src="https://40.media.tumblr.com/20df6436da8d2c865d198bfdeb226fcb/tumblr_o5ammmdfy21udztn8o1_1280.jpg" /></div> 
	</li>
	<li>and will fill it with the fuel from <a href="https://www.youtube.com/watch?v=3t0VMJdJna0&nohtml5=False">BEMOL</a><div class="custom-image"><img src="https://40.media.tumblr.com/27688078468a0e47037e46b1c5954d41/tumblr_o5amt2dq2M1udztn8o1_1280.jpg" /></div> 
	</li>
</ul>

[![Everything Is AWESOME](https://40.media.tumblr.com/e5f02efc09647d9100c3584e9e454671/tumblr_o5azlt3opU1udztn8o1_540.png)](https://www.youtube.com/watch?v=3t0VMJdJna0&nohtml5=False "Everything Is AWESOME")

Actually,I'm kidding))
We had to make a calculator.
The source code of the laboratory work can be found <a href="https://github.com/dianaartiom/calculator-laboratory">here</a>.

####How does my project look like?
Basically, the UI looks something like this:
<div class="custom-image"><img src="https://41.media.tumblr.com/575207e0eef7058265c874c1cb011641/tumblr_o5anolsljV1udztn8o1_400.png" /></div> 

<<<<<<< HEAD
######This week I made it for the first time. I wrote JAVA!

####Work process
#####Core <br />
A "special" thing I would like to tolk about is the way I parsed the input string. In order to parse it, i worked with regular expressions. Here is an example of code I used:

```
String signRegex = "(\\+|\\-|\\*|\\/|sqrt|\\^)";
String floatingPointNumber = "(([-|+])?[0-9]+\\.?[0-9]*)";
String pattern = floatingPointNumber + signRegex + floatingPointNumber;
```
I created a pattern and used Matcher. 
```
Pattern r = Pattern.compile(pattern);
Matcher m = r.matcher(string)[]
```
I worked with groups. I can explain. :)

But most of all, I would like to talk about the project structure. <br />
I decided to separate the project in two parts. One of the parts consists from "Business Logic", which means the part which is related to the "smart" part of the program. The second part is UI. Here the visual part was implemented. Actually, that was done in the following way: I made an artefact(JAR) of the Logic part and icluded in the newly created project, where I implemented the UI. Moreover, same procedure was done for the lastly created project. Thus, I obtained a JAR file runnable on more platforms.<br />

#####This week I did for the first time! I wrote JAVA!

The project structure looks like this: the Core and the Interface. The core contains the calculator logic. The Interface contains the UI - graphical/visual part of the calculator, with which the user will interract. 
######What about the work flow?
Actually, that was done in the following way: I made an artefact(JAR) of the Logic part and icluded in the newly created project, where I implemented the UI. Moreover, same procedure was done for the lastly created project. Thus, I obtained a JAR file runnable on more platforms.<br />
Don`t forget to visit my github repository to see the code. ;)

####Conclusion:
This laboratory work was really-really interesting. What made it so interesting to me? Of course writing the report and dividing the project in two parts - the gui and the logic tiers. This is my first java trial. I've never tried java, not even to write an app or something like that. At some point, I realized I've done bidlocode. So I decided I'll rewrite it from scratch. It was painfully, but I did it. Of course in the end I still obtained bidlocode, but at least it's less now(lines of code ) :D. It's really nice that what we learn at the course helps us to perform the laboratory work. What's really funny now is that now same task seems a lot more easier than it seemt two weeks ago, and that is, probably, a result. So what's the difference btw now and two weeks ago? Lots of lines of bidlocode were written, some coffee in minus and... my pc probably hates me for so many

```java -jar Core.jar 2^3+((3-4)^2)
```
like-previous terminal commands, project creations and so on. Even stackoverflow must be surprised on frequency I visited their site with, considering the bunch of questions I had.
Now I feel really motivated and challenged to proceed to the next laboratory work, and to do my best. :)


##Laboratory Work No.1
In this laboratory work we had to deal with installing a normal operating system, Ubuntu (Server), in VirtualBox. Basically it was nothing difficult. I installed VirtualBox using 

```$
sudo apt-get install virtual-box
```

The next thing I`ve done was downloading the Ubuntu Server image and installing it in VirtualBox. Having the IP address I connected my machine to the virtual one, by using SSH. The following image describes my actions:

####Basic Level
<ul>
  <li>Connect to a server using SSH</li>

<div class="custom-image"><img src="https://41.media.tumblr.com/899664a9733a7cee10d252a68e3f60df/tumblr_o33y88mR9p1uix9buo2_1280.png" /></div> 
</ul>
<br \>
####The next following 5 tasks describe the same image(addet below the tasks)  .
<ul>
  <li>Run at least 2 sample programs from provided HelloWorldPrograms set</li>
  See the screen attached, to verify the status of this task. 
  <div class="custom-image"><img src="https://41.media.tumblr.com/5518e5d800a977f566654b8de863c744/tumblr_o3bnydRG9U1udztn8o1_400.png" /></div> 
  <li>Initialize and make commit using a VCS, configure it</li>
</ul>
To initialize a repository, I used the following commands:

```$
git init
```

initializes a new repository.

```$
echo "#midps" >> README.md
```
makes the README file.

```$
git commit -m "Initial commit"
```
performs the first commit.

```$
git remote add origin https://someorigin...
```  
####Normal Level
<ul>
  <li>Create two branches.</li>
</ul>
To create a new branch I used the command: 

```$
git branch branch-name
```
<ul>
  <li>Commit two different branches.</li>
</ul>
To commit from a different branch, one should move on dat branch, using the following command: 

```$
git checkout branch-name
```
<br />
After performing the modifications, I used : <br />

```$
git add
git commit -m "Some message"
```
####Advanced Level 
<ul>
  <li>Set a branch to track a remote origin on which you are able to push (ex. Github, Bitbucket or custom server)</li>
  <div class="custom-image"><img src="https://40.media.tumblr.com/35bf62dfcd175242452344052c62591b/tumblr_o3arjnRIeV1udztn8o1_500.png" /></div> 
</ul>

####The next following 4 tasks describe the same image(addet below the tasks), from Advanced.
<ul>
  <li>Set a branch to track a remote origin on which you are able to push.</li>
  Already done before, using the command <br />
</ul>

  ```$
  git remote add origin blah blah...
  ```
<ul>
  <li>Reset a branch to previous commit.</li>
</ul>
  To reset the branch to the previous commit I used the command: <br />
  
  ```$
  git reset --hard  3517831ce1
  ```
  The "number" after the --hard is the commit SHA-1 key.
<ul>
  <li>Merge two branches.</li>
</ul>
  To commit two branches I used 

  ```$ 
  git merge branch-name-to-commit-with
  ``` 
  command. 
<ul>
  <li>Conflict solving between 2 branches</li>
</ul>
   Opened the file, made some changes, saved it. Then used
   
   ```$
   git add 
   git commit -m "...."
   ```
</ul>
<div class="custom-image"><img src="https://40.media.tumblr.com/9703a24e1d368e80b8e6c1906d4b3b04/tumblr_o3arof4qwk1udztn8o1_540.png" /></div> 

####Conclusion
Althought at the beginnig it seemed to be a quite difficult task, because I've never done it before, in the end I felt pretty comfortable to install Ubuntu on a virtual machine, to explore the VirtualBox itself, and to connect through SSH. Moreover, it somehow made me understand how different processes, with different meaning can run on the same machine without interrupting each other, without even knowing about each other. <br \>
The second part of the laboratory work was to play with some VCS. It is a very powerful tool for developers and not only. Version control is a system that records changes to a file or set of files over time so that you can recall specific versions later. It is widely used. Developers may wish to compare today’s version of some software with yesterday’s version or last year’s version. Since version control systems keep track of every version of the software, this becomes a straightforward task. Knowing the what, who, and when of changes will help with comparing the performance of particular versions, working out when bugs were introduced (or fixed), and so on. Any problems that arose from a change can then be followed up by an examination of who made the change and the reasons they gave for making the change.<br \>
######I used git. Git - because I used it before. I thought I kinda look like this...
<div class="custom-image"><img src="http://s.quickmeme.com/img/e0/e0d4afacba74c1b28ae4caad6f98e9d2d1689fe8e43dc1ee680214c75eb24e17.jpg" /></div> 
because I knew how to 

```$
git pull
```

```$
git clone
```

```$
git add .
```

```$
git commit -m "Write somethig, otherwise you`ll enter VIM and you`ll never EXIT!!!!"
```

```$
git push
```

and that`s all.

But... Umm, I then discovered 

```$
git cherry-pick
```

and 

```$
git rebase
```

and even more, 

```$
git hooks
```

#####and basically I got the point:
<div class="custom-image"><img src="https://40.media.tumblr.com/6f6502d41b0f9d7ad730d64a482db9ac/tumblr_o3at2qykMJ1udztn8o1_540.jpg" /></div> 
<div class="custom-image"><img src="https://41.media.tumblr.com/53246bb32ba50abbd457243da1dbbf77/tumblr_o3at27M65m1udztn8o1_540.jpg" /></div> 
Well, so I decided to learn what 
```$
git cherry-pick
``` 
 does. It is a very powerful feature. It allows us to choose a specific commit, to treat it as a cherry and to pick it. =))<br />
So what have I done?<br />
I made a new branch using the command: 

```$
git branch branch1
```

Switched to it. Made some commits and, on master, picked one of the commits I needed unsing the command: 

```$
git cherry-pick ue89fa456
```
For a better understanding, see the screenshots attached.
<div class="custom-image"><img src="https://40.media.tumblr.com/11446e3ed86fe802714619cc692063b6/tumblr_o3bn84qCEX1udztn8o2_1280.png" /></div> 
<div class="custom-image"><img src="https://40.media.tumblr.com/cf37f77445391ab7cac98cc5416e8c97/tumblr_o3bn84qCEX1udztn8o1_1280.png" /></div> 

Screens and images on how I done git rebase will come soon. :)
