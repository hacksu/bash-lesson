# Learning Bash 💻🔥

## Quick Links

[General Bash Guide](http://matt.might.net/articles/bash-by-example/)
[Emacs for windows](http://caiorss.github.io/Emacs-Elisp-Programming/Emacs_On_Windows.html)
[Bash Formatting Cheat Sheet](https://misc.flogisoft.com/bash/tip_colors_and_formatting)

## Setup 🐯

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

If you're on a windows machine, you don't have emacs! If you want it, you can download it [here!](http://caiorss.github.io/Emacs-Elisp-Programming/Emacs_On_Windows.html)

Our first bash file, to learn the basics of Bash execution:

```
#!/bin/bash                                                                     
# The above line tells shell how to process this file.
# Basically, if you go to the directory /bin/bash you can see the source code for the bash interpreter.

echo Heres what you said:         # Printing original message
echo $1                           # Printing your argument
foo=3                             # Assigning a new variable
bar=4                             
echo foo: $foo                    # Outputting that variable - note that we preface it with a $
echo foo + bar: $((foo + bar))
```

Now we can save our file and try to execute it! You can save and exit emacs by pressing ctrl-x, ctrl-c and then typing 'y' when asked if you want to save. (Or, ctrl-x ctrl-s to save, and THEN the close command. )

Now, we don't have execution power by default. You'll have to run this command to give yourself access:

```
chmod u+x filename
```

`chmod` is used to modify user permissions. The `u` refers to the current user, and we want to give that user eXecution power - hence the x!

Then, you can run that file by typing:

```
./filename arguments
```

Nice! Below I'll put a few more files we can play with.

## 🤓 Doing some math based on two numbers:
```
#!/bin/bash                                                                     

if [ $# -ge 2 ]
then
    echo $1 plus $2 = $(($1 + $2))
    echo $1 times $2 = $(($1 * $2))
else
    echo We needed two arguments but only got $#
fi
```

## 🔤 Basic text formatting - changing the color of some text:
```
#!/bin/bash                                                                     

RED='\033[0;31m'
NC='\033[0m' # No Color                                                         
printf "I ${RED}love${NC} Hacksu\n"
```

You can read more details about formatting [here](https://misc.flogisoft.com/bash/tip_colors_and_formatting)!

## 🌺 Testing out different formatting options based on that link:
```
#!/bin/bash                                                                     
echo "Changing to display option $1" # Note that $1 is your first argument
echo -e '\033[0;'$1'm'               # It's possible you'll need to use a different 'escape' escape character than 033
``` 

## 🎨 Printing all the colors:
```
#!/bin/bash                                                                     

for fgbg in 38 48 ; do # Foreground / Background                                
    for color in {0..255} ; do # Colors                                         
        # Display the color                                                     
        printf "\e[${fgbg};5;%sm  %3s  \e[0m" $color $color
        # Display 6 colors per lines                                            
        if [ $((($color + 1) % 6)) == 4 ] ; then
            echo # New line                                                     
        fi
    done
    echo # New line                                                             
done

exit 0
```


