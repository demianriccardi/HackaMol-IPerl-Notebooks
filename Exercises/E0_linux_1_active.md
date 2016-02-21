# Messing around in the File System from the shell environment: With power comes responsibility. 

## Exercise Description
In the previous exercise, you passively interacted with files and directories in your File System. In this exercise you will create files and directories; we will simulate computational work carried out using the terminal, work that needs to be organized, saved, and often transferred between computers.  

### Assumptions (see README.md)

## List of shell commands you will use in this exercise 

### Assumed commands from the first exercise 
* `pwd`    => path to working directory
* `cd`     => change directory  
* `ls`     => list contents
* `cat`    => dump file(s) contents to screen.  
* `touch`  => no touching! :) you will use touch to adjust the timestamp on a file.
* `ssh`    => login to other computers on the network (as long as you have a username and password)! 

### Basic commands 
* `mkdir`  | make directory
* `cp`     | copy
* `mv`     | move a file can be moved to a new name in the same directory
* `cat`    | dump file(s) contents to screen
* `rm`     | remove... be careful with this one.
* `tar`    | creates archives
* `gzip`   | zips files/archived and makes them smaller
* `gunzip` | unzip the zipped archive
* `scp`    | secure copy files between computers!

### Fun stuff
* `grep`  | filter lines of file to those that match; ex. grep Earlham earlham.txt
* `curl`  | grabs files from the internet.. no webbrowser needed!

### Exercise 1.  Make nested directories [`Foo/Bar/Baz`], each with their own files [`foo.txt`, `bar.txt`, `baz.txt`]. 

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

### Exercise 2.  Simulate a project with folders and files for pdbid: 2CBA.  Use `curl` to write the 2CBA protein databank file to a new file name 2CBA.pdb.  Use `grep` or commandline Perl to select the `CA`, `HIS`, `ZN` and `HOH` atoms into a new file.  `[curl, grep, perl]`

Suggested step-by-step:
  1. Create a directory named CAII, which contains a README.md, and a subdirectory named structures. 
  2. Download the structure of carbonic anhydrase II and save it into the structures directory.  There are many ways to do this.  For example, you may download the file and then move it to the structures directory. 
    * `curl http://www.rcsb.org/pdb/files/2CBA.pdb > 2cba.pdb`
    * `mv 2cba.pdb CAII/structures`
  3. That was your first move (`mv`)!  you can move that file anywhere you want (as long as you have permission).  You can also use `mv` to rename to the file.  Rename the file 2CBA.pdb.  [`mv CAII/structures/2cba.pdb CAII/structures/2CBA.pdb`] The `mv` command takes two arguments: 1. target file or directory, with appropriate path, 2. destination, with appropriate path.  If the destination: 
    * leads to an existing directory, the file will be moved there.  
    * leads to an existing file name, the file will be moved there, thus, overwriting the original file.  I do this all the time.
    * leads to a file that doesn't exist, the file will be moved there with a name change.
    * `cp` is very much like `mv`, except the original file doesn't disappear because you've copied it.
  4. Now that we have the 2CBA.pdb crystal structure, we don't need to curl it from the internet!  `grep` all the C-alpha ATOMs from the 2CBA.pdb to STDOUT. First, [`cd  CAII/structures/`] to change working directories to where the 2CBA.pdb file is (it will save commandline typing). Now, [`grep " CA " 2CBA.pdb ; grep ATOM `]
  5. Redirect that STDOUT into a new file: 2cba\_ca.pdb.  [`grep " CA " 2CBA.pdb ; grep ATOM > 2cba_ca.pdb`]
  6. `grep` all the lines matching both ATOM and HIS, without the CA atoms you grepped above! Display STDOUT first and then redirect to a file. [`grep ATOM 2CBA.pdb | grep HIS | grep -v " CA " > 2cba_his.pdb`]
  7. `grep` all the lines matching both HETATM and ZN into file [`grep HETATM 2CBA.pdb | grep "ZN" > 2cba_zn.pdb`] 
  8. `grep` all the lines matching both HETATM and HOH into file [`grep HETATM 2CBA.pdb | grep "HOH" > 2cba_hoh.pdb`]
  9. use the `cat` command to combine all these files into a new file [`cat 2cba_hoh.pdb 2cba_zn.pdb 2cba_ca.pdb 2cba_his.pdb > 2cba_ca_his_zn_hoh.pdb`]
 10. use `less` to page through the file. [`less 2cba_ca_his_zn_hoh.pdb`]  Notice that the order of atoms corresponds to your `cat`.

## Exercise let's have some fun on the `2CBA.pdb` file with Perl!

  1. use `perl` to create the same `2cba_ca_his_zn_hoh.pdb` file, but with a new name, `p5-2cba_ca_his_zn_hoh.pdb`. [`perl -e ' print foreach grep {m/CA|HIS|ZN|HOH/} grep {m/^ATOM|^HETATM/} <>' 2CBA.pdb > p5-2cba_ca_his_zn_hoh.pdb`].  The first `grep` function filters for lines beginning (the `^` character signifies "begins with" in matching expression) with ATOM or HETATM and send them to the left; the second grep filters the lines for the atoms we want. 
  2. Use `less` to page through the file. [`less p5-2cba_ca_his_zn_hoh.pdb`]
  3. It will look different than that generated above because the order of lines is maintained.  How convenient!! Do you understand why the order is maintained?

### Exercise 3. Create an archive from your work in Exercise 2 and transfer it to another computer!If this were important work, you would add descriptions to the README file for future reference.  You will learn how to edit files in the vim exercise.  Let's pretend that this directory now has really useful information in it.

Suggested step-by-step:
  1. use `tar` to create an archive [`tar -cvf caii.tar CAII`]  the `-c` option is for compress, `-v` is for visualize, and `-f` is for force.  
  2. you can now move that archive where ever you want... You can even email it!  let's move it to the cluster using a secure shell copy. [`scp caii.tar youruser@cluster.earlham.edu:`] Notice the : at the end.  This gives `scp` the clue that it needs to help you login and copy the file.  If you call scp without the : at the end, scp will copy your `caii.tar` into a file named `youruser@cluster.earlham.edu`!
  3. scp the archive again, but with a new name. [`scp caii.tar youruser@cluster.earlham.edu:newname.tar`] Thus, scp acts very much like copy. In addition to copying across the filesystem using paths, it can do so across different computers, still with paths.
  4. use the `-l` option of `ls` to look at the size of `caii.tar`. [`ls -l caii.tar`] 
  5. let's compress it to something smaller.  [`gzip caii.tar`]  use ls -l again to see the size.  It should be smaller. `gzip` will speed up your transfers using `scp` because, as you know, smaller files are transferred faster.
  6. Use scp to transfer the zipped directory to the cluster. [`scp caii.tar.gz youruser@cluster.earlham.edu:`]
  7. rename your CAII directory using `mv`. [`mv CAII CAII_backup`] use ls to see that you have no `CAII` directory.  
  8. remove the caii.tar.gz and verify that it is gone. [`rm caii.tar.gz ; ls -l caii.tar.gz`] 
  9. Ahh... now your working directory should now have only the CAII_backup directory.  Use scp to copy the zipped archive from the cluster back into your working directory and use tar to expand the archive. 1. [`scp youruser@cluster.earlham.edu:caii.tar.gz .` ] Where that final dot says "copy to my current working directory". 2. [`tar -xvf caii.tar.gz`]  

If you can verify that the directory that you have expanded contains all the same information as the CAII_backup, you are done!

## Exercise 4. Clean-up your mess!
Suggested step-by-step:
  1. use `ls` and `rm` to remove every file that you have created in this exercise.  You don't need to save any of it.  You should be able to recreate all of it very quickly as your skills improve.
  2. use `ssh` to log on to the cluster and clean up your files there as well.  Optionally, you can create a directory on the cluster where you can save the `history` output from this exercise. [`history > 2016_02-18_history.txt ; gzip 2016_02-18_history.txt; scp 2016_02-18_history.txt.gz youruser@cluster.earlham.edu: `]  clearly, the `history` on your local machine is different than that on the cluster.

