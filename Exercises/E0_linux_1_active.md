# Messing around in the File System from the shell environment: With power comes responsibility. 

## Exercise Description
In the previous exercise, you passively interacted with files and directories in your File System. In this exercise you will create files and directories; we will simulate computational work carried out using the terminal, work that needs to be organized and saved.  However, you will mostly make some mess and then clean it up.   

### Assumptions
The main assumption for this exercise is that you can open a terminal window. When you open a terminal, it loads a shell that provides you a bunch of useful commands for messing around with your file system.  For Chem-452, you will typically do this in two ways:

  1. on a macbook open the terminal.app, which is in /Applications/Utilities/ directory. You can navigate the finder and double click the application or you can do a spotlight search (watchglass in the upper right) for "Terminal".

  2. logging into JupyterHub will give you access to a launching window. You can launch a Terminal (or a Notebook) from the button labled "New" in the upper right. 

## List of shell commands you will use in this exercise 

### Assumed commands from the first exercise 
* `pwd`    => path to working directory
* `cd`     => change directory  
* `ls`     => list contents
* `cat`    => dump file(s) contents to screen.  
* `touch`  => no touching! :) you will use touch to adjust the timestamp on a file.
* `ssh`    => login to other computers on the network (as long as you have a username and password)! 

### Basic commands 
* mkdir  | make directory
* cp     | copy
* mv     | move a file can be moved to a new name in the same directory
* cat    | dump file(s) contents to screen
* rm     | remove... be careful with this one.
* tar    | creates archives
* gzip   | zips files/archived and makes them smaller
* gunzip | unzip the zipped archive
* scp    | secure copy files between computers!

### Fun stuff
* echo  | print to standard output
* grep  | filter lines of file to those that match; ex. grep Earlham earlham.txt
* curl  | grabs files from the internet.. no webbrowser needed!

## Exercise.  Make nested directories [`Foo/Bar/Baz`], each with their own files [`foo.txt`, `bar.txt`, `baz.txt`]. 

  1. Change your directory to the Desktop and list all of the files on the Desktop. [`cd Desktop; ls`]  Does the list look similar to that seen if you look at the Desktop with your eyes using the operating system?
  2. Make a directory named "Foo" on the desktop. [`mkdir Foo`] You should now see Foo on the Desktop. [`pwd; ls | grep Foo` or just `ls`] 
  3. Remove the Foo directory. [`rm -ir Foo`] The `-r` option allows `rm` to remove directories and anything inside of them. The `-i` option will trigger an inquiry from the shell, `examine files in directory Foo?`. Type `y` and then the `return key`,  and then it will ask, `remove Foo?`. Type `y ` and then the `return key`.  Create another Foo directory and then remove it without the -i [`rm -r Foo`] and now image that the Foo directory had all of your life's work. oops.  Your life's work is gone.  Be careful with `rm`; use `rm -i` until you are more comfortable.

  4. Make a series of directories on the Desktop:  Foo/Bar/Baz  
  5. Touch the files Foo/foo.txt  Foo/Bar/bar.txt and Foo/Bar/Baz/baz.txt
  6. use `ls` and the Finder to verify that you have created the expected Directory Tree and contained files.
  7. remove the baz.txt file and verify that it is gone [`rm Foo/Bar/Baz/baz.txt`]
  8. remove the Bar directory [`rm -r Foo/Bar`]
  9. What is in the Foo directory?
  10. Remove the Foo directory.

Quiz. Repeat 4-10 as quickly as you can.  See if you can get the creation of folders and files on one line.  Then `rm -r Foo` on the other.

## Exercise. Simulate a project. 

Create a new directory for work, pull down the 2cba structure, and then use grep to extract all the CA, HIS, and Water atoms into a new file.

  1. Create a directory named CAII, which contains a README.md, and a subdirectory named structures. 
  2. Download the structure of carbonic anhydrase II and save it into the structures directory.  There are many ways to do this.  For example, you may download the file and then move it to the structures directory. 
    * `curl http://www.rcsb.org/pdb/files/2CBA.pdb > 2cba.pdb`
    * `mv 2cba.pdb CAII/structures`
  3. That was your first move (`mv`)!  you can move that file anywhere you want (as long as you have permission).  You can also use `mv` to rename to the file.  Rename the file 2CBA.pdb.  [`mv CAII/structures/2cba.pdb CAII/structures/2CBA.pdb`] The `mv` command takes two arguments: 1. target file or directory, with appropriate path, 2. destination, with appropriate path.  If the destination: 
    * leads to an existing directory, the file will be moved there.  
    * leads to an existing file name, the file will be moved there, thus, overwriting the original file.  I do this all the time.
    * leads to a file that doesn't exist, the file will be moved there with a name change.
    * `cp` is very much like `mv`, except the original file doesn't disappear because you've copied it.
  4. Now that we have the 2CBA.pdb crystal structure, we don't need to curl it from the internet!  `grep` all the C-alpha ATOMs from the 2cba.pdb to STDOUT. 
  5. Redirect that STDOUT into a new file: 2cba_ca.pdb.  [`grep " CA " 2CBA.pdb ; grep ATOM > 2cba\_ca.pdb`]
  6. `grep` all the lines matching both ATOM and HIS, without the CA atoms you grepped above! Display STDOUT first and then redirect to a file. [`grep ATOM ~/Desktop/Foo/Bar/Baz/2cba.pdb | grep HIS | grep -v " CA " > 2cba\_his.pdb`]
  7. use the `cat` command to combine the two files into a new file `2cba\_ca\_his.pdb`.
  8. grep out the water molecules using the HOH identifier into a file, and merge that file with the `2cba\_ca_\his.pdb` created in 7.

## Exercise. Create an archive and transfer it to another computer! 

If this were important work, you would add descriptions to the README file for future reference.  You will learn how to edit files in the vim exercise.  Let's pretend that this directory now has really useful information in it.

  1. use `tar` to create an archive [`tar -cvf caii.tar CAII`]  the `-c` option is for compress, `-v` is for visualize, and `-f` is for force.  
  2. you can now move that archive whereever you want!  let's move it to the cluster using a secure shell copy. [`scp caii.tar youruser@cluster.earlham.edu:`] Notice the : at the end.  This gives `scp` the clue that it needs to help you login and copy the file.  If you call scp without the : at the end, scp will copy your `caii.tar` into a file named `youruser@cluster.earlham.edu`!
  22. ls -l quick.tar and notice the size of the tarred archive
  23. zip it up!  gzip quick.tar
  24. ls -l quick.tar.gz and notice the size.  (size of files and directories can be measured using the du command)
  25. scp quick.tar.gz your\_username@cluster.earlham.edu:
  26. cp quick.tar.gz back.gz
  27. rm quick.tar.gz
  27. ls quick.tar.gz
  28. scp your\_username@cluster.earlham.edu:quick.tar.gz .
  29. remove the ~/Desktop/Foo directory
  30. tar -xvf quick.tar
  31. find the path to the VMD 1.9.2 application 
  32. /Applications/VMD\ 1.9.2.app/Contents/vmd/vmd\_MACOSXX86 Desktop/Foo/Bar/Baz/2cba\_CA\_HIS\_HOH.pdb
  33. rm -r ~/Desktop/Foo
  34. rm quick.tar
  35. rm back.gz
  36. Have you cleaned up everything?
  37. use the history command to dump all the shell history to screen.  Save if you want.
  
## BEEF TIPS... 
  1. using the up arrow will allow you to scroll up through the history at the command line.  This is useful if you want to rerun a command.
  2. use the tab button to autocomplete 
