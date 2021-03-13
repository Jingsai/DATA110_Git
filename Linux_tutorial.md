# Linux Tutorial


## 1. Introduction

An operating system (OS) is software that manages computer hardware and system resources and provides the tools that applications need to operate.<sup>[1](https://www.whoishostingthis.com/resources/os-development/)</sup>

Linux is a free open source operating system created in 1991 by Linus Torvalds. It's based on a much older operating system called UNIX that was one of the first modern operating systems created. Like other operating systems like Windows or MacOS, Linux is the interface between you (the user) and the sophisticated hardware inside your machine.

Much of this information is adapted from the very helpful tutorial at Ryan's Tutorials.<sup>[2](https://ryanstutorials.net/linuxtutorial/)</sup>

### Open a terminal

To get started using Linux, click on the "Files" tab above and open the file called:

`Linux_terminal.term`

This will open a Linux terminal. Your should see a "command line" that says

`~/Linux/Linux_tutorial_S20$`

Unlike on Windows or Mac, you can't just point and click on things to take actions. All you have is a blank line and a cursor waiting for you to type something.

Many versions of Linux have fancy point-and-click graphical interfaces that make them look more like using Windows or Mac. But it's valuable to learn how to use Linux from the command line to understand what's happening at a deeper level.

As you go through this tutorial, be sure to type anything that is formatted like this:

```
type commands that appear in boxes like this
```

In addition to the commands I show you, there will also be some exercises that you'll have to complete on your own! They will be denoted like this:

#### <span style='color:#0000ff'>Exercise</span>

Here is some task you're supposed to complete on your own.

**Before working on this lab, please type the following commands to clear previous command history!** You need to hit the keyboard Enter after typing each line of the commands.

```
rm ~/.bash_history

exit
```

**Do not run above two commands again once you start working on the lab.**

*****


## 2. Navigation

### Directories

What is a directory? It's like a folder. Although it's not obvious, we are sitting inside of a folder. When you open up a terminal, you're automatically dropped into your "default directory".

We can get a little more information about our default directory. Type

```
pwd
```

This stands for "**p**rint **w**orking **d**irectory"&mdash;in other words, this prints your current directory. The result is the following:

`/home/user/Linux/Linux_tutorial_S20`

Notice that your command line has some of this information in it, except  the first part (`/home/user`) has been replaced with the tilde symbol (~). Therefore, the ~ must be equivalent to

`/home/user`.

That tilde represents your "home" directory, which confusingly is not just `/home`, but rather `/home/user`.

Be clear about the difference between your "home directory" and your "default directory". Your home directory (represented by ~) is

`/home/user`.

Your default directory is nested several levels inside of this home directory:

`/home/user/Linux/Linux_tutorial_S20`

or, in shortcut form,

`~/Linux/Linux_tutorial_S20`.

The command line also has a dollar sign at the end. This is not part of the directory name. It just tells you where you can type commands. It's the "command prompt".

###  Listing files

In the terminal, try typing:

```
ls
```

That's the lowercase letter "l" not the number one "1". They look very similar on the screen, so be careful!

(On your screen, it will actually look like

```
~/Linux/Linux_tutorial_S20$ls
```
but you'll only type the `ls` part.)

Be sure to hit Enter. Whenever you're instructed to type something, you'll always hit Enter. I won't remind you every time to hit Enter.

You will see a list that looks something like this:

`Documents  Linux_terminal.term  Tutorial.md`

The `ls` command is short for "**l**i**s**t". It lists any files or directories that are located in our current directory. It tells us that there are a number of objects sitting in this directory. `Documents` is another directory and it presumably contains other files and/or directories. `Linux_terminal.term` is a special kind of file that opens up a terminal when you run it. (Remember, you clicked on it in CoCalc.) And `Tutorial.md` is the file you're looking at right now.

### Moving between directories

Let's try moving around between directories. Since we saw that there was a `Documents` directory in our default directory, type

```
cd Documents
```

`cd` stands for "**c**hange **d**irectory".

Now your command prompt changes to

`~/Linux/Linux_tutorial_S20/Documents$`

This helpfully informs use that we're now inside a directory called `Documents` that is nested inside our default directory. We can confirm that by using `pwd` again.

```
pwd
```

#### <span style='color:#0000ff'>Exercise</span>

Is there anything in this directory? How do we list the contents of this directory to find out?

*****

Sure enough, there's a bunch of stuff in here.

What if we want to go back to our default directory. One way to do it is to type

```
cd ..
```

The two dots are a shortcut syntax for "up one directory", which takes you to the "parent directory".

### Paths

The text that shows a nested sequence of directories and subdirectories is called the "path". So the full path to our default directory is

`/home/user/Linux/Linux_tutorial_S20`.

One way to look at this is that there is a directory called `Linux_tutorial_S20` sitting inside of another directory called `Linux`, which itself lies within a directory called `user` inside a directory called `home`.

The path to the Documents subdirectory is

`/home/user/Linux/Linux_tutorial_S20/Documents`.

When we use `cd`, we can always use the full path to get where we want. These full paths are called "absolute paths". For example, let's wander into a new, scary, foreign place:

```
cd /var/log
```

We've never seen this directory before. Typing

```
ls
```

we see a bunch of unfamiliar directories and files. So how do we get back? We can always type

```
cd /home/user/Linux/Linux_tutorial_S20
```

Or even quicker:

```
cd ~/Linux/Linux_tutorial_S20
```

For a really, really quick shortcut, start typing `cd ~/L` and before finishing to type the rest, hit the Tab key. It should automatically add the rest of the word `Linux` to the line. Don't hit Enter yet! Keep going, typing `L` again and pressing the Tab key. This time, Linux auto-completes the rest of the name `Linux_tutorial_S20`. Once the whole path is up on the screen, now you can hit Enter. This "tab completion" is real time saver!

In case it didn't work, or you want to review the steps again, type the following:

```
cd ~/L[hit the tab key]L[hit the tab key]
```

Here's another handy shortcut. While in the terminal, hit the up arrow on your keyboard. Hit it a couple more times. Now hit the down arrow a few times. This scrolls back through your command history. This is especially convenient when you need to re-type a command you know you used recently. Or if you want to modify a recent command, you can hit the up arrow until you find it and then use the left/right arrows to go to the spot you need to change and change it.

Earlier we typed `cd Documents`. This uses a "relative path" (as opposed to an "absolute path"). The word `Documents` clearly does not represent an absolute path. The absolute path would be `/home/user/Linux/Linux_tutorial_S20/Documents`. But since we're already in the directory `/home/user/Linux/Linux_tutorial_S20`, Linus knows just to look for a directory `Documents` within our current directory.

So as long as we're in the default directory, this should work:

```
cd Documents
```

But this will also work:

```
cd /home/user/Linux/Linux_tutorial_S20/Documents
```

And they will both put us in the same place. The former is a "relative" path and the latter is an "absolute path".

Try this:

```
cd /home/user/Linux/
```

Now you're in the `Linux` directory that is one level higher than your default directory. What do you think will happen if we try the following?

```
cd Documents
```

You should get an error that says

`bash: cd: Document: No such file or directory`

(`bash` is the name of the "shell" which is just the program that allows you to open up the terminal and type commands.) There is no directory called `Documents`, at least not in the `Linux` directory. Type

```
ls
```

You can see that the only directory here is called `Linux_tutorial_S20`. This does mean that you can type the following. Don't forget the tab completion trick: after you type the `L`, just hit Tab to auto-complete the rest.

```
cd Linux_tutorial_S20
```

The double-dot `..` is also a relative path. Given the current directory, `..` represents the parent directory.

So if we're in the directory `/var/log` and we type `cd ..`, we should end up in the `/var` directory.

#### <span style='color:#0000ff'>Exercise</span>

Try it yourself. Navigate to the (absolute) path `/var/log` using `cd` and then type `cd ..` and then `pwd` to check to see that you are, indeed, in the `/var` directory.

*****

When you're done with the exercise, get back into the default directory:

```
cd ~/Linux/Linux_tutorial_S20
```

One nice trick is that we can often run commands in a different directory from the one we're currently in. For example, try this:

```
ls /var/log
```

This listed the contents of `/var/log` but we didn't have to navigate to that directory to do it. We're still in our default directory. Nice!

#### <span style='color:#0000ff'>Exercise</span>

What happens if you type

```
cd
```

without specifying a path (either absolute or relative)? Try it!

What will this do?

```
cd ~
```

*****

#### <span style='color:#0000ff'>Exercise</span>

Get back to your default directory by hitting the up arrow a few times until you see the following at the command prompt and then hitting Enter to execute the command:

```
cd ~/Linux/Linux_tutorial_S20
```

*****

How far back in the directory structure can we go? In other words, what is the top-most or highest directory in the hierarchy? It's called the "root" directory and it's indicated with a single forward slash `/`:

```
cd /
```

Let's look around here:

```
ls
```

All Linux systems are set up in roughly the same way, so the directories you see here are pretty common.

#### <span style='color:#0000ff'>Exercise</span>

Read up on the purpose for each of these directories here:

https://en.wikipedia.org/wiki/Unix_filesystem#Conventional_directory_layout

*****

Confusingly, there is a directory called `root` inside the root directory.  But when we say "root", we'll always mean the highest-level directory with a path that consists of only the forward slash `/`.

You'll also note that we've explored a little bit inside the `var` directory (more specifically, the `log` directory within the `var` directory).

#### <span style='color:#0000ff'>Exercise</span>

You can see that the `home` directory is listed as one of the main directories in the root directory. Start with

```
cd home
```

Then `ls` to see what's in there.

Continue alternating between `cd` and `ls` until you have found your way back to our default directory.

*****

If you have Linux installed on your own machine, these files will all be located on your hard drive somewhere. However, we are using the CoCalc service in the cloud. So where are all these files we're seeing? Well, they belong to CoCalc servers. The CoCalc administrators are kind enough to let you look at the filesystem that is located on their servers (wherever those are). Everything up to the `home` directory is common to all CoCalc users. The `/home/user` directory and everything inside of it is specific to you. So, for example, if you placed a file in `/home/user`, you would have access to it, but no other CoCalc user would see it. The only reason you have a `Linux/Linux_tutorial_S20` directory is because I copied it into your projects for you to give you something to work with. But those copies belong only to you and so any modifications you make will not be reflected in similar directories located in other students' accounts.

### Options

When running a command in Linux, you can specify optional parameters&mdash;often called "flags"&mdash;to make the command behave differently.

For example, try this:

```
ls -l
```

This produces somewhat more output:

<code>
drwxr-x--- 4 user user&nbsp;&nbsp;&nbsp;&nbsp;8 Feb 20 00:21 Documents<br />
-rw-r--r-- 1 user user&nbsp;&nbsp;&nbsp;36 Feb 20 02:23 Linux_terminal.term<br />
-rw-r--r-- 1 user user 9378 Feb 20 02:47 Tutorial.md<br />
</code><br/ >

(If you don't see that output, it means you're not in your default directory where you should be. Use `cd` to get to your default directory!)

This "**l**onger" output has several parts:

* The first character indicates whether it is a normal file (`-`) or directory (`d`).
* The next nine characters are permissions for the file or directory. (Don't worry too much about this.)
* The next field is the number of blocks. (Don't worry too much about this).
* The next field is the owner of the file or directory (`user` in this case).
* The next field is the group the file or directory belongs to (`user` in this case).
* Following this is the file size (in bytes by default).
* Next up is the file modification time.
* Finally we have the actual name of the file or directory.

For the next demonstration, do to the `Documents` directory:

```
cd Documents
```

Type

```
ls
```

to review what's here.

Now try:

```
ls -a
```

Do you notice anything different? The `-a` option shows **a**ll of the files, including hidden files. In Linux, files are hidden when they begin with a period, for example, the file `.hidden_file` in this directory.

Some options use only one letter, like `-l`. Other options use more than one character, and when they do, they are preceeded by two hyphens `--` instead of just one hyphen `-`:

```
ls --group-directories-first
```

Some options are available both ways. For example, the following are equivalent:

```
ls -a
```

```
ls --all
```

More than one option can be used at a time:

```
ls -a -l
```

In fact, if all the options you want use one letter, you can combine them:

```
ls -al
```


## 3. More about files

### Everything is a file

A common phrase you'll hear about Linux is that "everything is a file". What this means is that Linux keeps track of every part of your computer system by representing it internally as a file. So in addition to actual files, we also have directories, but they are just treated like files. The Linux terminal you opened was a file with a `.term` extension. Even hardware like your keyboard and monitor are represented as files by Linux. Your mouse is a file. Your hard drive is a file. That USB drive you mi<div align='right'></div>ght insert&mdash;yup, it's a file.

### File types

Navigate to the `Documents` directory:

```
cd ~/Linux/Linux_tutorial_S20/Documents
```

(Don't forget tricks like using the up arrow, or tab completion, or using relative paths like `cd Documents` if you are already in your default directory.)

Check out all the contents:

```
ls -al
```
<code>
drwxr-x--- 4 user user &nbsp;&nbsp;8 Feb 20 00:21  .<br />
drwxr-xr-x 3 user user &nbsp;&nbsp;7 Feb 20 00:21  ..<br />
-rw-r----- 1 user user &nbsp;49 Mar 28  2017  .hidden_file<br />
drwxr-x--- 2 user user &nbsp;&nbsp;2 Mar 28  2017 'Folder with spaces'<br />
-rw-r----- 1 user user &nbsp;37 Mar 27  2017  file1.txt<br />
-rw-r----- 1 user user &nbsp;&nbsp;0 Mar 27  2017  file2.txt<br />
drwxr-xr-x 2 user user &nbsp;&nbsp;3 Feb 22  2018  my_dir<br />
-rw-r----- 1 user user 197 Mar 28  2017  mysampledata.txt<br />
</code><br/ >

Although some files have file extensions like `.txt` to indicate a text file, it turns out that Linux doesn't actually care about the extension. Unlike Windows and Mac, the file extension tells Linux nothing about what's in the file. A file like `file1.txt` could be called `file1.jpg` instead and Linux would not be confused about how to open it.

How can we find out what type of file Linux thinks something is? Try this:

```
file file1.txt
```

`file1.txt: ASCII text`

So this is a text file. (ASCII is  standard system for encoding text characters in a file.)

#### <span style='color:#0000ff'>Exercise</span>

Try running the `file` command on the `my_dir` directory.

*****

Linux files are case-sensitive. That means that you can't mix uppercase and lowercase letters. Try this:

```
file File1.txt
```

Can you see why you got an error?

Now there appears to be a folder in our `Documents` directory called `Folder with spaces`

This won't work:

```
cd Folder with spaces
```

As soon as the `cd` command sees the space, it thinks its job is done and tries to change to a directory called `Folder`.

This, however, will work:

```
cd 'Folder with spaces'
```

Type

```
cd ..
```

to get to the `Documents` folder so you can also try this:

```
cd Folder\ with\ spaces
```

The "backslash" (don't confuse this with the "forward" slashes that are part of file paths) is a way to "escape" characters. The backslash tells Linux to treat the following character&mdash;in this case, a space&mdash;as a literal text character, and not a break in the command.

As a general rule, you should try very hard never to use spaces in filenames. Even though Linux can handle them, it takes some care and it's easy to make mistakes. I follow the convention of using underscores (`_`) whenever I want to put a "space" in something. For example, one of the other directories is called `my_dir`.

#### <span style='color:#0000ff'>Exercise</span>

Go to the `/dev` folder and list the contents of that directory. Try the `file` command on a bunch of stuff in there.

*****

You've probably noticed that the shell color-codes directory entries according to their file type.


## 4. Manual pages

The `man` command gives you access to **man**ual pages (i.e., help files) for commands in Linux.

Try

```
man ls
```

The first part of the output looks like this:

<code>
NAME<br />
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;ls - list directory contents

SYNOPSIS<br />
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;ls [OPTION]... [FILE]...

DESCRIPTION<br />
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;List information about the FILEs (the current directory by default).  Sort entries alphabetically if none of -cftuvSUX nor --sort is specified.
</code>

The `NAME` part gives the name of the command and a very brief description of its function.

The `SYNOPSIS` part shows the "form" of the command. The `[OPTION]` part is where you can place one or more options (like `-a` or `--all`) and the `[FILE]` part is where you can specify a directory whose contents you want to list. (Why does it say `FILE` and not `DIRECTORY`? Remember, everything is a file!) The brackets around `[OPTION]` and `[FILE]` indicate that these arguments are optional. In other words, you don't have to include options or a directory name; `ls` works fine by itself and defaults to the current directory.

The `DESCRIPTION` part gives a more detailed description.

Underneath the stuff at the top of the `man` page is a huge list of all the possible options. You can scroll one page at a time with the space bar, or one line at a time with Enter. When you scroll all the way to the end, at the bottom is some additional information about the command.

When you're doing perusing, `q` will "quit" the man page and take you back to your command line.

#### <span style='color:#0000ff'>Exercise</span>

Check out the man pages for a few of the commands you've learned in Linux thus far. Just for giggles, check out the man page for the `man` command. (You know, for when you need help finding help!)

*****


## 5. File manipulation

### Making directories

You can **m**a**k**e a new **dir**ectory with the `mkdir` command.

Let's get back to our default directory:

```
cd ~/Linux/Linux_tutorial_S20
```

Now make a new directory called `new_dir`:

```
mkdir new_dir
```

Check that it's there:

```
ls
```

That used a relative path. We can, of course, make directories using absolute paths as well:

```
mkdir ~/Linux/Linux_tutorial_S20/Documents/new_dir/new_sub_dir
```

Check that it's there, also using an absolute path:

```
ls ~/Linux/Linux_tutorial_S20/Documents/new_dir
```

### Copying files

This will be easier if we start in the Documents directory:

```
cd ~/Linux/Linux_tutorial_S20/Documents
ls
```

To **c**o**p**y a file, use `cp`. Here we'll copy the file `file1.txt` from this `Documents` directory to our newly created `new_dir` directory:

```
cp file1.txt new_dir
```

#### <span style='color:#0000ff'>Exercise</span>

Check that a copy of `file1.txt` is really sitting inside the `new_dir` directory.

*****

Here we used relative paths for both the origin file (`file1.txt`) and the destination directory (`new_dir`), which was easy because both the file and the directory to which we wanted to move the file are both located in our current directory. You'll need more elaborate paths if you want to copy one file in a completely different location to another random directory also located somewhere else.

We can use the `-r` option (which stands for "**r**ecursive") to copy whole directories. Let's say we wanted to make a backup of our Documents folder. We could do this (and I'll use absolute paths so that it won't matter where we are when we run this command):

```
cp -r ~/Linux/Linux_tutorial_S20/Documents ~/Linux/Linux_tutorial_S20/backup
```

#### <span style='color:#0000ff'>Exercise</span>

Check that a copy of everything from the `Documents` folder is now backed up in a folder called `backup` in the default directory.

*****

Note that even though the `backup` folder didn't already exist, `cp` created it for us.

### Moving and renaming files

The `mv` command will **m**o**v**e files. Get into the `Documents` folder and list its contents:

```
cd ~/Linux/Linux_tutorial_S20/Documents
ls
```

Now try this:

```
mv file2.txt my_dir
```

#### <span style='color:#0000ff'>Exercise</span>

Check that the `file2.txt` file is no longer in `Documents` but it is now in the `my_dir` directory.

*****

Now let's move `file2.txt` back to where it was before. Let's move to the  `my_dir` directory

```
cd ~/Linux/Linux_tutorial_S20/Documents/my_dir
```

Now this will work:

```
mv file2.txt ..
```

Think about why that works. Where is `file2.txt` being sent? The two dots&mdash;if you recall from earlier&mdash;represent the next directory up in the hierarchy. What is the parent directory of `my_dir`? It's the `Documents` directory!

Okay, let's try something else. We'll move the file once again and start over, but this time in the `Documents` directory:

```
cp ~/Linux/Linux_tutorial_S20/Documents/file2.txt ~/Linux/Linux_tutorial_S20/Documents/my_dir
cd ~/Linux/Linux_tutorial_S20/Documents
ls
```

Now try this:

```
mv my_dir/file2.txt .
ls
```

What happened here? And what's up with that single dot at the end? Well, this command told Linux to move `file2.txt` (which was in the `my_dir` directory). And it's destination should be...here in the `Documents` folder. Yes, the single dot represents your current directory. We didn't mention it earlier because it was kind of useless before. After all,

```
cd .
```

just says to change directories to right here. In other words, it doesn't change anything. Likewise,

```
ls .
```

just lists the contents of the current directory, but that is more easily accomplished with `ls` alone. But now that we want to move a file located somewhere else to here, well now it's convenient to have a representation of "here" using relative paths.

You can move whole directories using `mv`, and unlike `cp`, you don't have to use the recursive option `-r`.

Renaming files is accomplished with a clever trick. Get back to the `Documents` directory and try this:

```
mv file2.txt renamed_file.txt
ls
```

So we "moved" the file `file2.txt` to a file called `renamed_file.txt`. In other words, we renamed it.

#### <span style='color:#0000ff'>Exercise</span>

Change the name back to `file2.txt`

*****

### Removing files and directories

First, before we start deleting stuff, you want to be a little careful here. Linux isn't like Windows or Mac in that there is no "Trash" folder or "Recycling Bin" into which deleted files go and, therefore, are easily recoverable. No, in Linux, deletion is more or less permanent. There is also no "Undo". So check twice before executing a command that will permanently delete something.

The command to **r**e**m**ove a file is `rm`. The command to **r**e**m**ove a **dir**ectory is `rmdir`. (Or another option is to use `rm` with option `-d`.)

```
rmdir ~/Linux/Linux_tutorial_S20/Documents/new_dir/new_sub_dir
```

#### <span style='color:#0000ff'>Exercise</span>

Check that `new_sub_dir` is really gone.

*****

Let's also get rid of the backup directory we created earlier. (That was just to show that `cp` could copy whole directories.)

```
rmdir ~/Linux/Linux_tutorial_S20/backup
```

Uh oh, that didn't work. (Why not?)

The trouble here is that `rmdir` will only remove an empty directory. In a way, it's comforting to know that because it means you can't accidentally delete a directory that might have stuff in it. However, it's inconvenient when you really want to delete a whole directory with all the stuff inside.

Instead, we'll use the `rm` command with the **r**ecursive `-r` option to delete the directory and anything inside. Use this command with extreme caution.

```
rm -r ~/Linux/Linux_tutorial_S20/backup
```

#### <span style='color:#0000ff'>Exercise</span>

Check that the `backup` directory is really gone from the default directory.

*****

### Viewing files

One of the simplest ways to view a file is by using the `cat` command. This one is a bit of a hack, to be honest. The `cat` command stands for "con**cat**enate", which means to join together, and would normally splice two or more files together and then print them to the screen. But if we specify only one file, then it will just print that one file to the screen.

```
cd ~/Linux/Linux_tutorial_S20/Documents
cat file1.txt
```

The contents of `file1.txt` are just

`This is a file with some text in it.`

Something interesting happens if you just type `cat`:

```
cat
```

The command line disappears. Try typing something...anything...and hit Enter.

The screen just repeats back what you just typed. And it keeps doing this no matter what you type! It seems like we broke Linux!

Well, crap, how do we get back to the command prompt so we can keep going with our tutorial? Never fear...when you get stuck in Linux, you can always hit Ctrl-C on the keyboard. That is a universal set of keystrokes that means "Cancel".

And now we're back.

#### <span style='color:#0000ff'>Exercise</span>

View the contents of `mysampledata.txt`.

*****

#### <span style='color:#0000ff'>Exercise</span>

Do you remember how to find the hidden file? Can you view its contents?

*****

Some files are long enough that we may not want to print them to the screen. Here's one of the system log files:

```
cat /var/log/fontconfig.log
```

It is long enough that it scrolls all the way down the screen, which makes it hard to view.

The `less` command brings up a more convenient viewer that you can scroll through exactly like you did for man pages. Use the space bar or Enter to scroll (one page or one line at a time, respectively). Press "q" to quit and get back to the command line.

```
less /var/log/fontconfig.log
```

### Editing files

A simple application for editing files is called `nano`.

```
cd ~/Linux/Linux_tutorial_S20/Documents
nano file2.txt
```

The command line goes away because now you're actually running a text editing program.

Go ahead and type a line or two of text...whatever you want.

To save your work, hit Ctrl-O. At the bottom, it asks you to confirm that you want to save the file to `file2.txt`. Hit Enter to confirm. It tells you that you wrote some number of lines. Now you can exit by hitting Ctrl-X.

Now you should be back at the command line.


#### <span style='color:#0000ff'>Exercise</span>

Check to see that your file edits worked using the `cat` command.

*****

There are much more sophisticated programs for editing text in Linux. The most common ones are "vi" and "emacs".


## Conclusion

We have only scratched the surface. While you are not by any means a fluent Linux user from just this short tutorial, you've learned enough to do some really common and useful tasks.

With that basic foundation, you're ready to learn more if you're interested. There are any number of online resources&mdash;everything from web tutorials to books to online courses. As was mentioned in the introduction, Ryan's Tutorials (https://ryanstutorials.net/linuxtutorial/) are very good. (This tutorial is pretty close to the first five lessons on that site.)

## Submitting your assignment

When you are done, please follow the instructions below **carefully**.

From the terminal window...

1. Type exit and hit Enter. (**Do not forget this step! Otherwise, your command history will not be saved.** This will exit and restart your terminal session.)

2. Type the following:

```
cat ~/.bash_history > ~/Linux/Linux_tutorial_S20/final_history.txt
```

3. Go back to CoCalc and look in the Linux/Linux_tutorial_S20 folder.
You should see the final_history.txt file in there.

4. Select the checkbox next to the final_history.txt file and find the
"Download" button in the toolbar above the files. This will bring up
another box with a big blue "Download" button, which you should also click. This will download the file to your computer.

5. Go to Canvas and submit the final_history.txt file to the "Linux Tutorial" assignment there.


