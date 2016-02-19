# Navigating the File System within the shell environment.  Look, but don't touch. 

## Exercise Description
In this exercise you will walk around your directory tree and take in the sights. Almost all activities in this exercise will be passive. With two exceptions (see if you can figure out the source of these two "exception"), you will create no new "permanent" information.  You will navigate the file system and interact with files using standard output to the terminal, screen (STDOUT).  STDOUT disappears when you close the terminal window or clear your screen (command-K on OS X). You don't need to do this exercise if you:
  1. fully understand what a file system is.
  2. fully understand what a path is.
  3. are able to navigate the filesystem with ease.
  4. are able to navigate the filesystem of multiple computers using secure shell login (ssh).
  5. are able to interact passively with files and command documentation.

### Assumptions (see README.md) 

## List of shell commands you will use in this exercise 

### Basic commands
* `man`    => Manual description for command
* `pwd`    => path to working directory
* `cd`     => change directory  
* `ls`     => list contents
* `less`   => similar to command `more`, allows you to page through the contents of a file in read-only mode. In contrast to `more`, which allows you to page forward from start to finish, `less` allows you to page back and forth.
* `cat`    => dump file(s) contents to screen.  whereas `less` gives you a page by page read, `cat` just dumps everything. I am greedy, I often use `cat` and then page in the terminal with the mouse.
* `env`    => prints your environment!  this information helps you know where all your commands are coming and some other stuff.  Currently not used in this exercise.
* `alias`  => create new commands for your commandline!
* `touch`  => no touching! :) you will use touch to adjust the timestamp on a file.
* `ssh`    => login to other computers on the network (as long as you have a username and password)! 

### Some fun commands with STDOUT (standard output)
* `echo`  => print to standard output
* `grep`  => filter lines of file to those that match; ex. grep Earlham earlham.txt
* `curl`  => grabs files from the internet.. no webbrowser needed!
* piping STDOUT using the vertical bar "|" 
* `perl`  => an entire dynamic programming language for your commandline delights

### Exercise 1.  Use the commands `[man, cd, pwd]` to explore the commands in your path and to navigate your file system.

Suggested step-by-step: 
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
     
Each time you carried out the above commands, you were able to display the path to the working directory with `pwd`.  You should now be comfortable with `cd`, `pwd`, and you should have some instinct to what the "path" is.  "Your path" is the your location in the file system; a file's "path" is the location of the file on the filesystem.  For example, the path to the Terminal.app on OS X is `/Applications/Utilities/Terminal.app`.   

Quiz. You can chain two commands together on the commandline using the semicolon as a separator. For example `cd ; cd Desktop; cd ..`, will take you to your home directory, then hop you into the Desktop directory, and then back again into your home directory.  Predict the result of pwd for the following commands:  
  * `cd; cd . ; cd .. ; cd .. ; cd -` 
  * `cd ~/..`  
Now do them and see if the results are expected.

### Exercise 2. Add the `ls` command to improve your file system activities.  As you navigate your system and list files and directories, make heave use of the <tab> key and wildcards `*`. `[ ls, ls -l *.*]`.

Suggested step-by-step: 
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
  * What do you expect for `ls /*/`?
  * What would be returned with `ls *.*`?

Hint. you can put wildcards anywhere you want!

## Passive interaction with information contained on the File System and other file systems.
### Exercise 3: Use `less` and `cat` to investigate the contents of files on your system. `[cat, less]`

Suggested step-by-step.
  1. use `ls` to find a file that you would like to investigate. [`ls some.file`] where some.file is any old file you see.
  2. press the up arrow and convert `ls some.file` to `less some.file` to open it.
  3. press q to escape, and then dump the same file with `cat some.file`.
  4. touch a file with whatever name you would like, `touch some.file`.
  5. use `ls` to see that you touched a file.  Use `cat some.file` to see that it is indeed empty.
  6. use `ls -l some.file` to get more information on the file.
  7. wait 1 minute and the touch the file again, `touch some.file`.  Use `ls -l` and note the change.

### Exercise 4. Since I don't know what interesting files you may be looking at, let us pull one from the internet and play with it!  Use `curl` display the 2CBA protein databank file on STDOUT.  Next, pipe that STDOUT into a series of `grep` commands to select the `CA`, `HIS`, `ZN` and `HOH` atoms.  `[curl, grep, perl, and ssh]`

Suggested step-by-step
  1. use `curl` to pull a file (Protein Databank file) from the internet and dump it to the terminal screen: `curl http://www.rcsb.org/pdb/files/2CBA.pdb`
  2. use a web browser to go to the same site and see that it matches.
  3. use alias to make a command that runs the command in 4. and verify that it works. `alias 2cbacurl="curl http://www.rcsb.org/pdb/files/2CBA.pdb"; 2cbacurl`
  
If this weren't a passive exercise, you could save internet bandwidth by saving the file with the following command: `curl http://www.rcsb.org/pdb/files/2CBA.pdb > 2CBA.pdb`. This would redirect the STDOUT you saw in 4 into a file using the `>` for output redirection. Thus, with the file, you could avoid the "expensive" `curl` by using `cat 2CBA.pdb`... simple as that. You will do exactly this in the next exercise.
   
  4. Filter the output from your `2cbacurl` alias to print only lines containing CA: `2cbacurl  | grep "CA"`.  If you had the file, you could `grep` directly, `grep "CA" 2CBA.pdb` 

## Exercise 5. Repeat the last exercise, but use commandline `perl` in place of `grep`.  `[curl, perl -e]`

Suggested step-by-step
  0. verify that you have the `perl` command in your path. [`perl -v`] this print out the version of `perl` that you have installed.
  1. create the classic program "Hello world!" program and execute it all without making a file.  The "Hello world!" program prints the string "Hello world!" with a newline (`\n`) to STDOUT.  [`perl -e 'print "Hello world\n"'`] If you haven't written Perl programs before, Congratulations!  You have now written and executed your first Perl program... all on the commandline with no file to show for it.  You'll write another "Hello World!" program in a file in the next exercise. 
  2. use `perl` to grep out the CA atoms from 2CBA.pdb. [`2cbacurl | perl -e 'grep {m/CA/} <>'`] This command runs the Perl interpretor `perl` in execute mode (`-e`) on the stuff that follows:  the program is `'grep {m/CA/} <>'`, which acts on the output of your `2cbacurl` command (now input for the perl program) using the `<>` operator. The `<>` operator slurps up the input (which can be passed as a file) and passes them, line by line, to the `grep {m/CA/}` function. Perl has it's own `grep`!  Perl's `grep` is not the same as the commandline `grep` you ran above, but they fill similar roles. 
  3. The command you ran in 2. generated no output.  How boring.  Let's try it again, but this time we will print to the screen. [`2cbacurl | perl -e 'print foreach grep {m/CA/} <>'`] Now, you should see the same output as running `2cbacurl | grep CA 2CBA.pdb` using the system `grep`. The `<>` passes the input, line by line, left to the `grep {m/CA/}` that passes all the lines matching CA (`m/CA/`) left to the `foreach` function that passes each of the filtered lines to the `print` function. 

You may be thinking, "why would I ever want to use `perl` to do this?".  You can do way more within that perl commandline program than you can with grep. For example, the Perl match operator `m//` is powerful enough that we filter against several different matches in one pass (with "regular expressions" that we will not cover here). Furthermore you can chain multiple `grep` functions out to the left within the function.
  4. Use the Perl `grep` to pull the Zinc atom, all Histidine residues, water molecules, and CA atoms. [`2cbacurl | perl -e 'print foreach grep {m/ZN|HIS|HOH|CA/} <>'`] Isn't that nice?  We'll leave the commandline here for now.

### Exercise 6. Use `ssh` to log into another computer, on which you have an account. Use your knowledge from above to look around on this nonlocal computer. `[ssh]`

Suggested step-by-step:
As long as you have a username and password on another accessible machine (e.g. cluster.earlham.edu), you can use a secure shell login to get into that computer!!  
  1. Find your username and password and then login to cluster.earlham.edu from your terminal: `ssh username@cluster.earlham.edu` 
  2. Use `ls` and `cd` to walk around the File System on this machine; you should notice that it is different... it is a different computer!! There will likely be a different name on your commandline to remind you that this is a different computer. In fact, you may see a different version of Perl!  `perl -v`
  3. Use a web-browser to log into the [Earlham JupyterHub] (https://jupyter.cluster.earlham.edu).  Use the "new" button toward the upper right to open a terminal.  You now have a terminal through the JupyterHub!  Are you on the same computer as you logged in via step 1? ... (hint. NO!).
  
