# Learning Bash

To learn the basics of bash, I read [this guide](http://matt.might.net/articles/bash-by-example/).  Rather than trying to rewrite a guide like that, I'll instead just include the project files I decided to build for this lesson, and explain all the steps I used. 

This lesson requires basic knowledge of how to navigate the command line. To start, we'll need to use `cd` to change directories, `ls` to get our bearings in a given directory, and `mkdir` to make a new folder for our projects.

```
cd ~/Desktop    # Moving to the desktop
mkdir bashDemo  # Making a folder on our desktop
ls              # Displaying the files on our desktop
cd bashDemo     # Going into said folder
```

I'll then be using `emacs` to create and edit files. We need a new file with no extension, like this:
```
emacs myFirstBashScript
```

File 1, iteration 1: Learning the basics of Bash execution:

```
#!/bin/bash                                                                     

# Use $1 to get the first argument!                                             
echo Heres what you said:
echo $1
foo=3
bar=4
echo foo: $foo
echo foo + bar: $((foo + bar))
```
