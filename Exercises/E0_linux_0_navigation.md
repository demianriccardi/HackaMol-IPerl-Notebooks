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
* `env`    => print environment
* `touch`  => no touching! :) you will use touch to adjust the timestamp on a file.
* `cat`    => dump file(s) contents to screen
* `ssh`    => login to other computers on the network (as long as you have a username and password)! 

### Some fun commands with STDOUT (standard output)
* `echo`  => print to standard output
* `grep`  => filter lines of file to those that match; ex. grep Earlham earlham.txt
* `sed`   => dump files with substitutions!
* `curl`  => grabs files from the internet.. no webbrowser needed!
* piping STDOUT using the vertical bar "|" 
* some cool perl oneliners that can do grep and sed stuff.


## The exercise

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
  5. Each time you carried out the above commands, you were able to display the path to the working directory with `pwd`.  You should now be comfortable with `cd`, `pwd`, and you should have some instinct to what the "path" is. 
  6. What is in your path when you open a terminal window?   
  6. List all of the files on the Desktop. [`ls`]  Does to list look similar to that seen if you look at the Desktop with your eyes using the operating system? List all of the files again with the -l option (see man pages for description). [`ls -l`]
  5. Change back to your default working directory. [`cd -`, or `cd ..`, or `cd`]
 ...
  15. Navigate with a browser to this address: http://www.rcsb.org/pdb/files/2CBA.pdb
      use curl to dump that file to the screen!
  17. pipe the curl STDOUT into grep and filter all the lines the C-alpha lines (CA) of the 2cba.pdb (`curl http://www.rcsb.org/pdb/files/2CBA.pdb` | grep "ATOM" 
   grep "CA") play around with multiple greps to get some practice filtering.
  18. grep all the lines matching both ATOM and HIS by piping a one grep into another grep (grep ATOM ~/Desktop/Foo/Bar/Baz/2cba.pdb | grep HIS)
  ...
  37. use the history command to dump all the shell history to screen.  Save if you want.
  
## TIPS for mor advanced use... 
  1. using the up arrow will allow you to scroll up through the history at the command line.  This is useful if you want to rerun a command.
  2. use the tab button to autocomplete
  3. you can separate multipe actions with a semicolon `cd $path; cd - ; cd $path; cd -` 
  
