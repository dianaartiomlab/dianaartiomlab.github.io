---
layout: default
title: MIDPS
---

##Laboratory Work No.1
In this laboratory work we had to deal with installing a normal operating system, Ubuntu (Server), in VirtualBox. Basically it was nothing difficult. I installed VirtualBox using <br \>
```$
sudo apt-get install virtual-box
```
<br \>
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
  <li>Initialize and make commit using a VCS, configure it</li>
</ul>

####Normal Level
<ul>
  <li>Create two branches.</li>
  <li>Commit two different branches.</li>
</ul>
####Advanced Level 
<ul>
  <li>Set a branch to track a remote origin on which you are able to push (ex. Github, Bitbucket or custom server)</li>
  <div class="custom-image"><img src="https://40.media.tumblr.com/35bf62dfcd175242452344052c62591b/tumblr_o3arjnRIeV1udztn8o1_500.png" /></div> 
</ul>

####The next following 4 tasks describe the same image(addet below the tasks), from Advanced.
<ul>
  <li>Set a branch to track a remote origin on which you are able to push.</li>
  <li>Reset a branch to previous commit.</li>
  <li>Merge two branches.</li>
  <li>Conflict solving between 2 branches</li>
</ul>
<div class="custom-image"><img src="https://40.media.tumblr.com/9703a24e1d368e80b8e6c1906d4b3b04/tumblr_o3arof4qwk1udztn8o1_540.png" /></div> 

####Conclusion
Althought at the beginnig it seemed to be a quite difficult task, because I've never done it before, in the end I felt pretty comfortable to install Ubuntu on a virtual machine, to explore the VirtualBox itself, and to connect through SSH. Moreover, it somehow made me understand how different processes, with different meaning can run on the same machine without interrupting each other, without even knowing about each other. <br \>
The second part of the laboratory work was to play with some VCS. It is a very powerful tool for developers and not only. Version control is a system that records changes to a file or set of files over time so that you can recall specific versions later. For the examples in this book you will use software source code as the files being version controlled, though in reality you can do this with nearly any type of file on a computer. It is widely used. Developers may wish to compare today’s version of some software with yesterday’s version or last year’s version. Since version control systems keep track of every version of the software, this becomes a straightforward task. Knowing the what, who, and when of changes will help with comparing the performance of particular versions, working out when bugs were introduced (or fixed), and so on. Any problems that arose from a change can then be followed up by an examination of who made the change and the reasons they gave for making the change.<br \>
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
git add push
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
git hoocks
```
<br \>
#####and basically I got the point:
<div class="custom-image"><img src="https://40.media.tumblr.com/6f6502d41b0f9d7ad730d64a482db9ac/tumblr_o3at2qykMJ1udztn8o1_540.jpg" /></div> 
<div class="custom-image"><img src="https://41.media.tumblr.com/53246bb32ba50abbd457243da1dbbf77/tumblr_o3at27M65m1udztn8o1_540.jpg" /></div> 


