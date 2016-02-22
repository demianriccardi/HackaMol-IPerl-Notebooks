#Beginning using git and GitHub to maintain and share your work. 

##Exercise Description
Git and GitHub are different things.  

Git is a commandline program that you can use to keep control of your computational projects.  You make a directory, you initiate git in that directory to keep track of things, and then as you carry out your work, you make commits to your project repository.  It's incredibly powerful.  For example, if you make a disasterous mistake, you can just rewind you repository to a place where things were working as expected.  This exercise will not teach you how to do this.  In this exercise, you will use the git command to clone repositories from GitHub so that you can mess around locally on your computer.  

GitHub is a place up in the cloud that you can push work to and pull your work from.  It is free as long as you make your projects publicly accessable (i.e. open source).  It is a giant space containing tons of cool things that you can play around with and start work from.  In fact you are reading this description on GitHub.  In this exercise, you will use the tools you have learned in the linux exercise to interact with this repository locally on your machine.  

####Warning: Once you learn and are thus hooked on using GitHub, be sure that it is ok to share your work publicly on GitHub before doing so.  
For example, if you are a grad student working on a hot research topic under the guidance of your famous R1 professor, you will probably want to use Git and some more private form of GitHub (there is a private option for GitHub that your R1 professor can probably afford!).  Once you get used to working in public view, the paranoia of such things tends to subside; however, your GitHub philosophy needs to agree with that of your coworkers.

## Commands
 * git 
 * cd
 * ls
 * cat

####Exercise 1. Clone this repository (the one you are reading) into a working directory.
Suggested step-by-step:
  1. open a terminal window and run `man git` to check out the man pages.
  2. run `git help -a` to see all the possible commands.  It is a massive list.  Don't be scared.
  3. clone this repository, which you are reading right now! [`git clone https://github.com/demianriccardi/EC-Chem452.git`]
  4. change your working directory to EC-Chem452 and look around.  Try to find these words: "Earlham is heaven on earth"
using a grep command with a wildcard.  [`grep "Earlham is heaven on earth" */*`]
  5. you now have your own local version of this repository.  

####Exercise 2. Log into [Earlham's JupyterHub](https://jupyter.cluster.earlham.edu), open a terminal, and clone this repository (the one you are reading) into your home directory.
   1. open a terminal window using the "new" dropdown menu in the upper right of the screen. 
   2. use git to clone it into your home directory [`git clone https://github.com/demianriccardi/EC-Chem452.git`]
   3. look around!
   4. you can now use the JuperHub launch page to load notebooks from the class!
  
####Optional Exercise 3.  Clone the HackaMol repository into the same working directory! 
Suggested step-by-step:
  1. [`git clone https://github.com/demianriccardi/HackaMol.git`] and then look around.  There is a directory of examples that you will be able to play with once you have more tools.

####Exercise 3. Once you are ready to take the plunge, create a GitHub account!
  1. Login to GitHub, open a web-browser and navigate to [this repository](https://github.com/demianriccardi/EC-Chem452).  Find these words: "Earlham is on earth" and change them to whatever you want using the edit feature on GitHub (a little pencil... I'm using the edit feature right now to write this!).  If you figure out how to do this, a fork of this repository will be created in your github user space.  A fork is basically a copy, your copy, that you can change with abandon!  Thus, at this stage, you can take these exercises and write in your own solutions.   

####Exercise 4. Clean up!
Assuming you didn't do anything useful in the directory you created.  Change your working directory and [`rm -r path/devel_demian`] 
