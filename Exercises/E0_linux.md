#Messing around with the File System from the shell environment: With power comes responsibility. 

## Exercise Description
In this exercise you will walk around your directory tree, take in the sights, make some mess, and then clean it up.  We will introduce some ideas to help you organize your computational work. This exercise will help you complete the git exercise.  With completion of the git exercise, you should be comfortable, "forking this repository into your own GitHub repository, which you can then edit these files directly and contribute to these exercises!" 

### Assumptions
The main assumption for this exercise is that you can open a terminal window. When you open a terminal, it loads a shell that provides you a bunch of useful commands for messing around with your file system.  For Chem-452, you will typically do this in two ways:

  1. on a macbook open the terminal.app, which is in /Applications/Utilities/ directory. You can navigate the finder and double click the application or you can do a spotlight search (watchglass in the upper right) for "Terminal".

  2. logging into JupyterHub will give you access to a launching window. You can launch a Terminal (or a Notebook) from the button labled "New" in the upper right. 

## List of shell commands you will use in this exercise 

### Basic commands
* man   | Manual description for command
* pwd   | path to working directory
* ls    | list contents
* cd    | change directory
* mkdir | make directory
* touch | create an empty file or adjust the timestamp 
* cp    | copy
* mv    | move a file can be moved to a new name in the same directory
* cat   | dump file(s) contents to screen
* rm    | remove... be careful with this one.  
### Fun stuff
* echo  | print to standard output
* grep  | filter lines of file to those that match; ex. grep Earlham earlham.txt
* curl  | grabs files from the internet.. no webbrowser needed!

## The exercise

  1. Access the documentation (aka "man pages") for each of the above commands, and make a note of what each does. "man" is short for manual. For example, typing 'man man' will display the documentation for the "man" command.     
  2. Where are you on the filesystem by default?  
  3. Change your directory to the Desktop and compare your filesystem location to the default found in 2.
  4. List all of the files on the Desktop.  Does to list look similar to that seen if you look at the Desktop with your eyes using the operating system?
  5. Make a directory named "Foo" on the desktop. Do you see it show up? list the files and directories to see that you have made the directory.  
  6. Change your directory to the Foo directory and list the contents of the directory.
  7. Change back to the default directory.
  8. List the contents of the Desktop directory.
  9. Make a series of directories on the Desktop:  Foo/Bar/Baz
  10. Touch the files Foo/foo.txt  Foo/Bar/bar.txt and Foo/Bar/Baz/baz.txt
  11. remove the baz.txt file and verify that it is gone (rm ~/Desktop/Foo/Bar/Baz/baz.txt)
  12.  

If you change your directory (cd) to the Desktop directory, where are you now.
  2. pwd. where are you   
     

