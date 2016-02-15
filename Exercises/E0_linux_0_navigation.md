# Navigating the File System within the shell environment.  Look, but don't touch. 

## Exercise Description
In this exercise you will walk around your directory tree and take in the sights. Almost all activities in this exercise will be passive. With on exception (see if you can figure out the source of this "exception"), you will create no new "permanent" information.  You will navigate the file system and interact with files using standard output to the terminal, screen (STDOUT).  STDOUT disappears when you close the terminal window or clear your screen (command-K on OS X). You don't need to do this exercise if you:
  1. fully understand what a file system is.
  2. fully understand what a path is.
  3. are able to navigate the filesystem with ease.
  4. are able to navigate the filesystem of multiple computers using secure shell login (ssh).
  5. are able to interact passively with files and command documentation.
  
### Assumptions
The main assumption for this exercise is that you can open a terminal window. When you open a terminal, it loads a shell 
that provides you a bunch of useful commands for messing around with your file system.  For Chem-452, you will typically 
do this in two ways:

  1. on a macbook open the terminal.app, which is in /Applications/Utilities/ directory. You can navigate the finder and 
  double click the application or you can do a spotlight search (watchglass in the upper right) for "Terminal".

  2. logging into JupyterHub will give you access to a launching window. You can launch a Terminal (or a Notebook) from the 
  button labled "New" in the upper right. 

## List of shell commands you will use in this exercise 

### Basic commands
* `man`    => Manual description for command
* `pwd`    => path to working directory
* `cd`     => change directory  
* `ls`     => list contents
* `less`   => similar to command `more`, allows you to page through the contents of a file in read-only mode. In contrast to `more`, which allows you to page forward from start to finish, `less` allows you to page back and forth.
* `cat`    => dump file(s) contents to screen.  whereas `less` gives you a page by page read, `cat` just dumps everything. I am greedy, I often use `cat` and then page in the terminal with the mouse.
* `env`    => print environment
* `touch`  => no touching! :) you will use touch to adjust the timestamp on a file.
* `ssh`    => login to other computers on the network (as long as you have a username and password)! 

### Some fun commands with STDOUT (standard output)
* `echo`  => print to standard output
* `grep`  => filter lines of file to those that match; ex. grep Earlham earlham.txt
* `sed`   => dump files with substitutions!
* `curl`  => grabs files from the internet.. no webbrowser needed!
* piping STDOUT using the vertical bar "|" 
* some cool perl oneliners that can do grep and sed stuff.


### exercise `[man, cd, pwd]`

  1. Open a terminal window and determine the path to your working directory.  [`pwd`]
  2. Access the documentation (a.k.a. "man pages") for some of the above commands. This is the way to find the details of how each command does. "man" is short for manual. For example, typing `man man` will display the documentation for the "man" command.   Exit documentation with the "q" key. 
  3. Change your working directory to the Desktop and compare your filesystem location to the default found in 1. [`cd Desktop ; pwd`]
  4. Let's play with the `cd` command; use the `pwd` command to see the effect of the following on the path to your working directory: 
     * `cd .`
     * `cd ..`
     * `cd -`
     * `cd ~/Desktop` 
     * `cd ~` 
     * `cd -`
     * `cd ../..`
     * `cd ..` 
     * `cd ~/`  ...  what happens to `~` when you run the cd command with an argument containing it at the beginning?
     * `cd This_is_Heaven_ON_Earth`
     * `cd /This_is_Heaven_ON_Earth`
     * `cd ~/This_is_Heaven_ON_Earth`
     * `cd /`
     * `cd -`
     
Wach time you carried out the above commands, you were able to display the path to the working directory with `pwd`.  You should now be comfortable with `cd`, `pwd`, and you should have some instinct to what the "path" is.  "Your path" is the your location in the file system; a file's "path" is the location of the file on the filesystem.  For example, the path to the Terminal.app on OS X is `/Applications/Utilities/Terminal.app`.   

Quiz. You can chain two commands together on the commandline using the semicolon as a separator. For example `cd ; cd Desktop; cd ..`, will take you to your home directory, then hop you into the Desktop directory, and then back again into your home directory.  Predict the result of pwd for the following commands:  
  * `cd; cd . ; cd .. ; cd .. ; cd -` 
  * `cd ~/..`  

### exercise `["the tab key", ls, and "wildcards *"]`
  1. Open a new terminal window and display the contents of your home directory. [`ls`]
  2. The Tab key autocompletes with items in the your path.  Play around with hitting the tab key:
      * Hitting tab twice on an empty commandline will give you the option of seeing a schmorgesborg of commands.  In this schmorgesborg are the commands that you are using here [e.g. `ls cd pwd .. etc` ].  It should ask to type y or n.  Typing y will allow you to scroll through the commands using the `more` command.
      * type `ls ` but don't hit enter, hit tab two times instead.  Here, tab doesn't display the schmorgesborg of commands because you already chose one (`ls`); instead, it give you a display of all the files and directories.  Find a directory you like from the display and type the first letter.  For example, `ls L<TAB>` should show list you any files/directories that start with the letter `L`.
      * use ls to look around your file system without using cd.
  3. As you look around your file system using `ls` and the tab key, play around with wild cards.
      * `ls L*` lists anything starting in `L`
      * `ls *.txt` lists anything ending in .txt
      * `ls  */*.txt` lists all .txt files within directories in your working directory!
      * `ls */*/*.txt` lists all .txt files within the first directory within all directories in you working directory.
  4.  List all of the files on the Desktop. [`ls`]  Does to list look similar to that seen if you look at the Desktop with your eyes using the operating system? List all of the files again with the -l option (see man pages for description). [`ls -l`] 
  
Quiz. 
  * What is in your path when you open a terminal window?
  * What do you expect for `ls /`?
  * What do you expect for `ls /*`?
  * What do you expect for `ls /*/`

### Exercise: Passive interaction with information contained on the File System and other file systems. `[cat, less, curl, grep, sed, and ssh]`
  1. use `ls` to find a file that you would like to investigate. [`ls some.file`] where some.file is any old file you see.
  2. press the up arrow and convert `ls some.file` to `less some.file` to open it.
  3. press q to escape, and then dump the same file with `cat some.file`.
  4. touch a file with whatever name you would like, `touch some.file`.
  5. use `ls` to see that you touched a file.  Use `cat some.file` to see that it is indeed empty.
  6. use `ls -l some.file` to get more information on the file.
  7. wait 1 minute and the touch the file again, `touch some.file`.  Use `ls -l` and note the change.

Since I don't know what interesting files you may be looking at, let us pull one from the internet and play with it!  
  4. use `curl` to pull a file (Protein Databank file) from the internet and dump it to the terminal screen: `curl http://www.rcsb.org/pdb/files/2CBA.pdb`
  5. use a web browser to go to the same site and see that it matches.

If this weren't a passive exercise, you could save internet bandwidth by saving the file with the following command: `curl http://www.rcsb.org/pdb/files/2CBA.pdb > 2CBA.pdb`. This would redirect the STDOUT you saw in 4 into a file using the `>` for output redirection. Thus, with the file, you could avoid the "expensive" `curl` by using `cat 2CBA.pdb`... simple as that. 
   
  6. Filter the output from `curl` to print only lines containing both ATOM and CA: `curl http://www.rcsb.org/pdb/files/2CBA.pdb  | grep "ATOM" | grep "CA"`.  If you had the file, you could `grep` directly, `grep "ATOM" 2CBA.pdb | grep "CA" 2CBA.pdb` 

## TIPS for mor advanced use... 
  1. using the up arrow will allow you to scroll up through the history at the command line.  This is useful if you want to rerun a command.
  2. use the tab button to autocomplete
  3. you can separate multipe actions with a semicolon `cd $path; cd - ; cd $path; cd -` 
  
