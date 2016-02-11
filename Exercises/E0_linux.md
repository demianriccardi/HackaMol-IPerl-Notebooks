#Messing around with the File System from the shell environment: With power comes responsibility. 

## Exercise Description
In this exercise you will walk around your directory tree, take in the sights, make some mess, and then clean it up.  We will introduce some ideas to help you organize your computational work. This exercise will help you complete the git exercise.  With completion of the git exercise, you should be comfortable, "forking this repository into your own GitHub repository, which you can then edit these files directly and contribute to these exercises!" 

### Assumptions
The main assumption for this exercise is that you can open a terminal window. When you open a terminal, it loads a shell that provides you a bunch of useful commands for messing around with your file system.  For Chem-452, you will typically do this in two ways:

  1. on a macbook open the terminal.app, which is in /Applications/Utilities/ directory. You can navigate the finder and double click the application or you can do a spotlight search (watchglass in the upper right) for "Terminal".

  2. logging into JupyterHub will give you access to a launching window. You can launch a Terminal (or a Notebook) from the button labled "New" in the upper right. 

## List of shell commands you will use in this exercise 

### Basic commands
* man    | Manual description for command
* pwd    | path to working directory
* ls     | list contents
* cd     | change directory
* mkdir  | make directory
* touch  | create an empty file or adjust the timestamp 
* cp     | copy
* mv     | move a file can be moved to a new name in the same directory
* cat    | dump file(s) contents to screen
* rm     | remove... be careful with this one.
* tar    | creates archives
* gzip   | zips files/archived and makes them smaller
* gunzip |
* scp    | secure copy files between computers!
* ssh    | login to other computers on the network (as long as you have a username and password)! 

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
  12. remove the Baz directory (rm -r ~/Desktop/Foo/Bar/Baz)
  13. remove the Foo directory; what happened the Bar directory, foo.txt, and bar.txt?
  14. repeat 9.  (check out the -p option for the mkdir command) 
  15. Navigate with a browser to this address: http://www.rcsb.org/pdb/files/2CBA.pdb
      use curl to dump that file to the screen!
  16. use curl to dump the file into a file name 2cba.pdb in the ~/Desktop/Foo/Bar/Baz directory (you can use the '>' to redirect output).
  17. filter (grep) all the lines the C-alpha lines (CA) of the 2cba.pdb using the grep command (grep CA ~/Desktop/Foo/Bar/Baz/2cba.pdb)
  18. grep all the lines matching both ATOM and HIS by piping a one grep into another grep (grep ATOM ~/Desktop/Foo/Bar/Baz/2cba.pdb | grep HIS)
  19. use 17 and 18 to create two files 
    * 2cba\_ca.pdb containing only CA atoms
    * 2cba\_HIS.pdb containing only Hist atoms 
  20. grep out the water molecules using the HOH identifier.  cat the files 2cba\_ca.pdb, 2cba\_HIS.pdb, and 2cba\_HOH.pdb into a new file: 2cba\_CA\_HIS\_HOH.pdb
  21. tar up the directory (tar -cvf quick.tar ~/Desktop/Foo)
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
   

