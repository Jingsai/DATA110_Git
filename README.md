# Git tutorial

The material in this tutorial is covered in much more detail in the amazing tutorial "Learn Enough Git to Be Dangerous" (https://www.learnenough.com/git-tutorial).


## 1. Getting a Github account

Go to https://github.com.

If you happen to have a Github account already, go ahead and log in.

For most of you, you will need to set up a Github account. You can use any email address you want for that. Choose a username you'll be happy with in case you decide to use Github for future professional projects. Also try to remember your password in the future!

When you get logged in to a pre-existing account, you may see a green button that says "New". Click on that. If you are a new user, it's likely you'll be asked some survey questions, asked to verify your email address, and then you will likely be dropped right into the "Create new repository screen", which is where you want to be.


## 2. Creating a repository

Under "Repository name", type

`Learning-Git`

Add a brief description. It doesn't really matter what you type, but maybe something like "This is my first repo!"

Scrolling down, check the box to "Initialize this repository with a README".

Push the button to "Create repository".


## 3. Adding a file to the repository

Once inside your new repo, find the "Create new file" button. Name the file "file.txt" and type one line of text in the body of the file. (It can be anything.) At the bottom, click the green button to "Commit new file".

We're about to leave Github and go back to CoCalc, but before you go, copy and paste the URL for your Github repository. It should have the form

`https://github.com/<username>/Learning-Git`

where your username appears in place of `<username>`. If you see extra stuff at the end of the URL like `/tree/master`, don't copy any of that. Just grab the stuff up to and including `Learning-Git`.


## 4. Using the terminal in CoCalc to set up a local git repository

Now go over to CoCalc and open up our course project. Navigate to folder `Git/Git_tutorial_S20`.

Open the terminal file called "git_terminal.term". At the command prompt, type

```
git clone <URL>
```

where `<URL>` should be replaced by the repo's URL from Github that you copied a minute ago. This will grab a copy of the repository from Github and place it in your folder.

Use `ls` to see that a new directory has been created called Learning-Git. Go ahead and `cd` into that new directory. From here on, make sure that any command you type starting with `git` is run from inside the Learning-Git directory. If, for some reason, you leave that directory, be sure to come back to it before you run any more git commands. You can always get back to this directory by typing

```
cd ~/Git/Git_tutorial_S20/Learning-Git
```

Type the following and observe the results:

```
ls -a
```

Notice the hidden directory `.git`. This is where the git magic happens, but you should not mess with anything in that directory.

Now we need to set some global options before we proceed:

```
git config --global user.email "<email address>"
```

Obviously, you should replace `<email address>` with your own email address without the angle brackets. But you do need to include the quotes. Be sure to use the same email you used to set up your Github account.

```
git config --global user.name "<Name>"
```

Same goes for `<Name>`.


## 5. Modifying files

Let's edit the file `file.txt`:

```
nano file.txt
```

This brings up the very simple `nano` text editor. You should see the text you typed in Github. Go ahead and add one more line of text to the file. Save with Control-O. Hit Enter to confirm that you want to write to `file.txt`. Finally, hit Control-X to exit `nano`.

Print the file to the screen so that you can confirm that you have successfully edited the file by adding a second line of text:

```
cat file.txt
```

Check the status of the changes we've made with the `git status` command:

```
git status
```

We're going to be doing a lot of these status checks to learn what is happening to our files in the process of using git. This particular status check should tell you that there are "Changes not staged for commit." It also points out that the reason for this is that the file `file.txt` has been modified.

We can also see the changes directly by using

```
git diff
```

Using `git diff` allows us to see both the original state of the file and the changes we have made.


## 6. Staging modified files

"Staging" your files means telling git we'd like it to pay attention to any changes we've made and to get ready to commit those changes.

```
git add -A
```

The flag `-A` in the previous command means that we want to stage all files in this directory. (Of course there is only the one file in this case.)

Again, check the status:

```
git status
```

This time we get a list of "Changes to be committed". (Again, this is just the one file.)


## 7. Committing files

Committing a file means allowing git to permanently record the change that has been made. This record stored in git tracks the state of the file before and after the change. This alteration to a file is sometimes called a "diff" (for "difference") and we saw before that the `git diff` command showed us precisely that difference.

The following command uses the option `-m` to record a message about the commit.

```
git commit -m "Edit file.txt"
```

Check the status to see that it worked:

```
git status
```

The message "nothing to commit, working tree clean" means that after the last commit, we start with a blank slate again. Git has nothing left to track because there have been no changes since the last commit.


## 8. Pushing files to the cloud

A new message that appeared in the last status check says

`Your branch is ahead of 'origin/master' by 1 commit.`

What does this mean? Remember that we have a copy of the repository stored in the cloud in Github. But now we also have a copy of the repository that we've been looking at in our CoCalc directory. (And if you're using git on your own machine, your repository will be located on your physical computer.) The point is that the local copy has now changed, but Github does not yet know about the change. The local copy is one "commit" ahead of the Github repo (called `origin/master` here).

Therefore, we need to "push" the changes we've made up to the cloud.

```
git push -u origin master
```

When you run this command, you'll have to provide your username and password for Github. (This is important because it means that random people can't just clone your repository, make changes, and then push them back into the cloud without your knowledge.)

The `-u` flag is a technical option required to make a future command work more easily, so don't worry too much about it. The naming conventions (like "origin" and "master") are also somewhat confusing to people new to git, so don't worry too much about those either. Just know that `git push` sends all the changes back up to Github so that your changes are uploaded and stored in the cloud.

Check the status as always:

```
git status
```

It should say

`Your branch is up to date with 'origin/master'.`

In other words, the local copy you're working with is now synced with the cloud.


## 9. Verifying the changes in Github

Now go back to Github. (If you left it open in a tab in your web browser, you may need to refresh the page.) Click on the file "file.txt" and see that the changes you made in CoCalc have been "pushed" back to Github!


## 10. The log file

Type

```
git log
```

to see the log file. This is a record of everything that has been done in this git repository. It appears in reverse chronological order; the newest changes are listed first. You should see three commits. The first one (at the bottom) was generated when you created the repository. The next one was performed in Github when you created `file.txt`. The final one (listed first) is the commit we performed in the terminal after editing `file.txt`.

Each commit is identified by a unique set of characters called a hash. More specifically, the information that encodes all changes made during a commit is converted via the SHA1 hash algorithm to a hexadecimal string (digits 0 through 9 or letters a through f) that is 40 characters long.

If you want to inspect a particular commit, you can use `git show` as follows, but replace `<SHA>` with the 40-character hash that appears in the log file with the commit of interest.

```
git show <SHA>
```

In other words, you should copy and paste the latest commit hash into the `git show` command to see the diff for that commit.


## 11. Staging versus committing

The distinction between staging files and committing changes is often not well understood.

Staging files (using `git add`) is telling git to pay attention to those files. Committing will permanently record any changes to those files by adding an entry to the log.

Here is a way to think about it. (From an answer on an internet forum: https://softwareengineering.stackexchange.com/questions/119782/what-does-stage-mean-in-git):

"Consider a scenario where you call the movers to get your stuff from your old apartment to your new apartment. Before you do that, you will go through your stuff, decide what you take with you and what you throw away, pack it in bags and leave it in the main hallway. The movers simply come, get the (already packed) bags from the hallway and transport them. In this example, everything until the movers get your stuff, is staging: you decide what goes where, how to pack it and so on (e.g. you may decide that half your stuff will be thrown away before the movers even get there - that's part of staging)."

So, for example, perhaps I have a number of files in my directory and I've made changes to a bunch of them. I'm ready to make a commit, but perhaps I want each commit to be focused on only one small task that involves only a few files. If I stage only those files and then commit, git will record the changes to those files, but it won't worry about the other changes to my directory yet. Later, when I'm done with other changes, I can stage a different set of files and commit those. It will be more clear when I go back and read my commit messages later which changes I made when, rather than having one big commit with lots of little changes in lots of places.

Let's try staging and committing changes separately to illustrate this.

First, make sure we're in the right directory:

```
cd ~/Git/Git_tutorial_S19/Learning-Git
```

Make a new file called `newfile.txt` as follows:

```
touch newfile.txt
```

The `touch` command is a Linux command that creates a new (empty) file.

Check that everything worked:

```
ls
```

Now our repo has changed, which we can see as follows:

```
git status
```

While we're at it, let's also modify `file.txt` again:

```
nano file.txt
```

This will bring up the `nano` text editor again. Add a third line of text, then hit Control-O, Enter, and Control-X to save your changes and exit `nano`.

Check:

```
git status
```

Okay, so at this point, there are two changes to our repo: we have added a new file, and we have modified an existing file. We could, if we wanted, just stage all files and commit all changes at once. But what if we want to track these two events separately?

Let's stage just the change to `file.txt`.

```
git add file.txt
```

```
git status
```

Contrast this with our earlier use of `git add` where we used a flag (`-A`) to indicate that we wished to stage all files.

Now we commit just the one change:

```
git commit -m "Change only file.txt"
```

```
git status
```

Notice that the status still tells us that there is a new untracked file, but the change to `file.txt` has been committed.

Let's make the other change, first by staging the new file.

```
git add newfile.txt
```

```
git status
```

And then making the commit:

```
git commit -m "Add newfile.txt"
```

Now we have committed all changes, so our "working tree is clean" again.

Of course, we are also told that our "`branch is ahead of 'origin/master' by 2 commits`". In other words, we have made two commits locally that are not reflected in the cloud yet.

How do we sync our local repo with Github? We use `git push`.

In fact, since we did something more complicated earlier using the `-u` flag, we can use a shortcut and just type:

```
git push
```

(No need to specify "`origin master`").

```
git status
```

Everything is clean now. Our changes are all committed and we've pushed to the cloud. If you go to Github on the web, you'll see that all your files are there with all the changes we made.


## 12. Staging and committing in one step

There are plenty of circumstances in which we are totally fine with staging all files and committing all changes all at once. Rather than using a sequence of two commands (`git add -A` and `git commit -m "<message>"`), we can use a shortcut:

```
git commit -am "message"
```

The flag `-a` tells the commit command to do the staging and the commit in one step. (And we still need `-m` too, of course, so that we can include a message. Single-letter flags like `-a` and `-m` can be combined into one flag: `-am`.)

Of course, nothing happened with that last `commit` command because there were no changes to our repo; that was just to show you the syntax.

(Note that there are some subtleties we're sweeping under the rug here. See https://atrystwithprogramming.wordpress.com/tag/git-add-vs-git-add/)


## 13. Reviewing commits on Github

We learned earlier that we can use

```
git log
```

to see in the terminal the history of all commits we've made. (If that list starts getting long, it might not all appear on the screen all at once. If the terminal appears to be "frozen", you can use the Enter key to keep printing one line at a time, or the space bar to print the next screen. When it reaches the "END", you may still need to press "q" to quit out of the screen scrolling at get back to a command prompt.)

It's much easier to see the commit history in a nicer format in the web broswer. So go to Github. From the main page of your repository, there should be a link above your file listing that shows the number of commits. If you click on that, you'll see the list of commits in the log. And clicking on any given commit will show you the diffs from that commit. Very handy!


## 14. Typical git workflow

All the above can be boiled down to the following. After editing our files (or even adding or deleting files), we can do the following two steps:

```
git commit -am "<message>"
```

```
git push
```

Now we know a little about staging, committing, and pushing files. But an important question still remains: when and how often should we stop working on files to commit them? When and how often should we push to Github?

There isn't one right answer here. I like to think of it as follows: whenever I commit, that saves a permanent copy of the changes I've made. It's similar to making a backup of my files. If I imagine that the power went out and I were to lose all my work, where would I have to start over? Well, the point in time from which I am guaranteed to recover my work is the last time I committed. And worst-case scenario, if I lost the files on my computer, say to a hard drive failure, I am guaranteed to recover the files from Github from the last time I pushed to the cloud.

It's annoying to have to stop your workflow every few minutes to make commits. On the other hand, the more commits we make, the easier it will be to review my past steps and recover my work from any given point in the past, so there's a balance.

Personally, I like to wait until I get to a natural "stopping point". Maybe I finish an important paragraph, or a complicated bit of computer code and I'm ready to take a break and get a bowl of cereal. That's when I'll commit my code.

You can push as often as you want, and it's pretty easy to do, so I generally commit and push my code at the same time. But that's not strictly necessary. A lot of people push their code at the end of the day, or maybe even after a few days of working on a project. If you're colloborating on a project with other people and it's important that their versions stay current, it is usually to push more often.

## 15. Conclusion

Git and Github combine to make for a powerful tool. Version control makes it easy to keep our files updated and backed up. We don't need to save different copies or versions of files because every version from the past is stored in our commit history. In the event of a crisis, it's relatively easy to "rollback" to a previous version and start from scratch at that point.

While we haven't said anything about collaboration in this tutorial, that turns out to be the best feature of a version control system. When multiple people are working on the same documents or codebase, git makes it possible to keep one set of files in the cloud that everyone can share. It does all the work in the background to keep everyone's local versions of the files (on their separate individual machines) in sync with each other. Every change you make, once pushed to the cloud, can be "pulled" down to everyone else's machines so that everyone is working on the same thing.

It takes a bit of effort to learn git. And when things go wrong, there is quite a bit of Googling required to solve git problems. Nevertheless, it's worth the effort to reap the benefits that version control provides.


## 16. Submitting your assignment

Go to Github and grab the URL for your repository. It should be of the following form:

`https://github.com/<username>/Learning-Git`

(As before, remove any extra stuff from the end of the URL after the `/Learning-Git` part.)

Submit this URL to Canvas as proof that you completed the assignment.


