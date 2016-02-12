##15 minute exercise: slicing and dicing text files using the Vi editor 

##Description
vi is a text editor that has a lot of features.  It is a little weird at first, but the weirdness pay dividends in time-savings later.  This exercise will get you started using vi to create and edit files.

## Commands
  * vi       
  * mkdir
  * cd
  * cat
  * wc -l

## Vi modes:  when you open a file for editing, your intuition is to be able to "get writing". For vi, this is the "insert mode" and in order to get writing, you have to switch to insert mode.  We are getting ahead of ourselves.  There are three modes in vi: 
  1. Normal mode: this is the default mode. When you `vi some.txt` you will load the file in this mode.
  2. Insert mode: use the "i" key to enter insert mode.  Type until your heart is content.  Use the escape key to get back into Normal mode.
  3. Visual mode: use the "v" key to enter visual mode. You can do magical highlighting, copying, and pasting in visual mode. Use the escape key to get back into Normal mode.
 
## Exercise
1. make a directory to have some fun `mkdir devel_demian`
2. change working directory to the one created in step 1, above
3. open a new file in vi. `vi somefile`
4. switch to insert mode and type: "Earlham is heaven on earth."
5. escape insert mode and write the file using `:w`
6. exit the file by typing `:q`
7. use the cat command to see the inside of the file: `cat somefile`
8. open the file again.  in Normal mode type `yy` and then `1846p` and you should see your the line repeated a bunch of times.
9. In normal mode type `:set nu` to see the line numbers.  Still in Normal mode, type `shift G` to go to the end of the file.
10. See that you actually have 1847 lines in the file!
11. use `:wq` to write and quit the file, and then run the command `wc somefile` to count the lines and words.
12. open the file again, type `:s/heaven\ //` to do a substitution on all the lines.
13. type `u` to undo the change.
14. move the cursor to the first letter of "heaven" on the first line using the arrow keys.
15. enter visual mode, hit the down key a couple of times and then the right arrow key to see what happens.
16. type `d` and the highlighted stuff should get pulled as if you did a "cut" in other programs.
17. type some `p` to paste it in.  Have fun as you wish and then you are done.  write quit your file and then clean up after yourself by deleting the working directory.

