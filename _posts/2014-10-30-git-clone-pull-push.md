---
layout: post
title: "git basics: clone, push, pull"
date:   2014-10-31 20:49:52
authors: SARAH ELMENDORF, CLAIRE LUNCH, NATALIE ROBINSON, and heavily derivative of similar materials by KEVIN GUAY and Software Carpentry 
categories: [Git Training]
tags : [ ]
description: "Learning to clone, push, and pull are crucial to interacting with a git repository.  This will guide you through the basics, and provide some pointers for When Things Go Wrong"
code1: 
image:
  feature: textur2_FieldWork.jpg
  credit: Ordway Swisher Biological Station, NEON, thx to Courtney Meier
  creditlink: http://www.neoninc.org
---

<img src= "http://git-scm.com/images/logos/downloads/Git-Logo-Black.png" alt="Drawing" style="width: 300px;"/>

##**for NEON**##

## What is Git / GitHub

<p align="center">
<img src= "http://software-carpentry.org/v5/novice/git/img/phd101212s.gif" description="Piled Higher and Deeper by Jorge Cham, http://www.phdcomics.com" link="www.phdcomics.com" style="width: 350px;" />
</p> 
<br><br>

## Overview
<figure> <img src="../../images/overviewchart.png"> </figure>


###Git: open-source version control system

#####Version Control
- Revert to previous versions
- Keep track of changes with comments
<br>

#####Collaboration
- Each user works on a local copy
- Changes are *pushed* to a central repository (GitHub)
- Conflicts are identified and handled
- Always work on the most up-to-date copy
<br><br>

###GitHub: a place to host a git repository and track issues

#####Viewing contents of a repository on github
- Find a repository.  We have set up this repository for testing today: [https://github.com/scelmendorf/gittest](https://github.com/scelmendorf/gittest "example")
- Click on any folder or file to view the current contents
- Click on any file to open it.  If it is a .docx or other binary file, you will need to then click 'view raw' which should open up a dialogue box and open the file locally using the appropriate program (e.g. ms windows)
- This will only work to VIEW files in the repository.  You cannot add or modify most types of files in the repo through the github.com webUI

#####Issue tracking
- Click on 'Issues' <figure> <img src="../../images/issuesbutton.png"> </figure> to create, view, comment or close issues
- To reference specific people in an issue, you can include their username in your comment, e.g. @scelmendorf
- You can also add labels to an issue, and you can add labels to the list of available labels <figure> <img src="../../images/gitlabels.png"> <figcaption> Some labels from the organismalIPT repository issues </figcaption> </figure>
- Default setting is to receive email alerts for all issues and comments. To change this setting, click on Unwatch and change setting to Not watching. You will still get emails when your username is mentioned. Do NOT use the Ignoring setting.
<br><br>

## Git setup
1. Create a GitHub account (www.github.com)
2. Send Sarah your username (if you want access to the private repositories)
3. Download <a href= "http://git-scm.com/downloads"> Git</a>
4. Open the git client or terminal (or another shell; bash, csh, etc.)
5. Follow the <a href= "https://help.github.com/articles/set-up-git/" > setup instructions</a> to configure your computer
	* you must git config BOTH your user.name and user.email through the shell
6. If you need additional help, follow screenshots on the IT sharepoint page
7. If you want to use a GUI (Graphical User Interface) to interact with Git, download either <a href="https://mac.github.com/"> GitHub Mac</a> or <a href="https://windows.github.com/">GitHub Windows</a>
<br><br>

## Git basics

### Clone the repository onto your local hard drive

*Conventions in this document:*

- *Everything after a > is something you should type into the computer*
- *Everything after a '#' is representative of something the computer types back at you*

**From command line**
- Visit the repository on github.  [https://github.com/scelmendorf/gittest](https://github.com/scelmendorf/gittest)
- Copy the  **HTTPS** clone URL 
- Open git bash
- navigate to where you want to clone the repository
Example:

    > cd C:/Users/scelmendorf/Desktop

- Clone the repository:

Example:

	> git clone https://github.com/scelmendorf/gittest.git
	
	# Cloning into 'gittest'...
	# remote: Counting objects: 12, done.
	# remote: Total 12 (delta 0), reused 0 (delta 0)
	# Unpacking objects: 100% (12/12), done
	# Checking connectivity...done

- When cloning is finished, the repository will appear as a folder on your computer

- *Tip: instead of typing out the url, you can copy it and then use shift-insert to paste text into the command line*


<br>

**Using the graphical user interface (GUI)**

- Visit the repository on github.  [https://github.com/scelmendorf/gittest](https://github.com/scelmendorf/gittest)
- Click the Clone in Desktop button <figure> <img src="../../images/clonebutton.png"> </figure>
- GUI application will launch and prompt to choose a location to clone to (these instruction and screenshots use GitHub Mac, but GitHub Windows is extremely similar)
- When cloning is finished, the repository will appear as a folder on your computer

<br>

### Stage your work for upload to the repository
Before you can save your work to the repository, you must stage it. This means that git knows about the change, but it is not permanent in the repository (so if you messed up, it's not yet finalized).
<br>

**From command line**

- Work on your file and save it locally (e.g., create a document called yourname.txt, type some text in, and save it in the cloned repository on your computer)

	*Your work is not officially uploaded yet, which you can see by checking the status of the repository*

Example:

    > git status
    # On branch master
    # Your branch is up-to-date with 'origin/master'

	# Untracked files:
   	#  (use "git add <file>..." to include in what will be committed)   
    #        yourname.txt
    # nothing added to commit but untracked files present (use "git add" to track)

- Navigate to the cloned repository:

*tip: most command line programs will automatically fill in partially typed commands and/or filenames if you hit tab. Try typing:*

Example:

	> cd gitt
	
*and then hitting the tab key in lieu of typing in the entire next line and see what happens*


	> cd gittest

- Stage your file using the 'add' command

Example:

	> git add yourname.txt
	
*Check the status again and you will see that your file has been added to the index*
	
	> git status
	# On branch master
	# Changes to be committed:
	#  (use "git reset HEAD <file>..." to unstage)
		
	# new file:   yourname.txt
<br>

**Using the graphical user interface (GUI)**

- Work on your file and save it locally (e.g., create a document called yourname.txt, type some text in, and save it in the cloned repository on your computer)

*Your work is not officially uploaded yet, which you can see by checking the Changes tab in the GitHub GUI*

<figure> <img src="../../images/uncommitted.png"> <figcaption> GitHub Mac with uncommitted changes. Panel on the right shows changes made to the highlighted file, with deletions in red and additions in green. </figcaption> </figure>


<br>

### Committing and pushing your work to the repository
Committing your changes will create a new version of the repository on your local machine. You can commit as many times as you want before pushing to the repository. When you commit changes, make sure to use the `-m` flag followed by a descriptions in "quotation marks" (i.e., git commit -m "this is a new commit with a great description").

If you accidentally overwrite a file or delete something, you will be able to revert back previous commits. Therefore, it is good practice to commit often.

**From command line**

- First, pull the latest version of the repository, so you can avoid conflicts (covered below)

Example:

	> git pull

*You may see that your repository updates, if someone else has added something to the repository. For example, if John added his test file (HelloJohn.txt) to the repository's test directory, you might see:*

	> git pull
	# remote: Counting objects: 5, done.
	# remote: Compressing objects: 100% (3/3), done.
	# remote: Total 5 (delta 0), reused 0 (delta 0)
	# Unpacking objects: 100% (5/5), done.
	# From https://github.com/scelmendorf/gittest.git
	#   478cbcb..db9ed4e  master     -> origin/master
	# Updating 478cbcb..db9ed4e
	# Fast-forward
	# test/HelloJohn.txt  | 1 +
	# test/test.txt | 2 +-
	# 2 files changed, 2 insertions(+), 1 deletion(-)
	# create mode 100755 test/HelloJohn.txt
	# mode change 100644 => 100755 test/yourname.txt

- Now, commit your changed document

Example:

	> git commit -m “added yourname.txt to the test files.”
	# [master 478cbcb] added yourname.txt to the test files.
	# 1 file changed, 1 insertion(+)
    # create mode 100644 test/yourname.txt

- Advanced: You can reference an issue in your commit message! Just add the issue number to the commit message

Example:

	> git commit -m “added yourname.txt to the test files resolved #102”


- Finally, push your changes to the remote host (origin) and branch (master)

Example:

	> git push origin master
	# Counting objects: 6, done.
	# Delta compression using up to 8 threads.
	# Compressing objects: 100% (3/3), done.
	# Writing objects: 100% (4/4), 402 bytes | 0 bytes/s, done.
	# Total 4 (delta 1), reused 0 (delta 0)
	# o https://github.com/scelmendorf/#gittest.git
	# 117f31d..478cbcb  master -> master

*Check the status again and you should have a 'clean' directory*

	> git status
	# On branch master
	# nothing to commit, working directory clean
<br>

**Using the graphical user interface (GUI)**

- Before you commit any changes, click the Sync button in the upper right corner. This will pull any changes other people have made to the repository. Sync early and sync often!

- Write a message in the Summary field describing the changes you've made. This is your commit message. You can reference issues, as described in the command line instructions above. Click on the Commit button.

<figure> <img src="../../images/committedunsynced.png"> <figcaption> GitHub Mac with committed, unsynced changes. </figcaption> </figure>

- Click on the Sync button in the upper right corner to push the changes to the repository.

<figure> <img src="../../images/nochanges.png"> <figcaption> GitHub Mac with no uncommitted or unsynced changes. </figcaption> </figure>



<br>
	

## Helpful reminders, tips, and info

### Basic Git Commands

<!--please leave this as a table, not as a code block -->
Command      | description
----------|----------------
git clone | make a local copy of the repository in your current working directory
git add   | add a new file to the git index (ie. `git add .` adds all of the files in the current directory)
git rm    | remove a file from the index (so that it removes it from your workspace and from the repository next time you commit/ push). This will also remove it from everyone else's local files the next time they pull
git mv    | move a file from one location to another. Can also be used to rename a file (see examples in *Basic Unix Commands*, but be sure to add 'git' before the command)
git status| check the status of files (ie. added, deleted or modified) since your last commit
git commit| make a new version of the repository on your local machine. Make sure to use a descriptive comment (ie. `git commit -m 'descriptive comment'`)
git pull  | get the latest version of the repository. This should be done before you start working on a new file and before you push your changes (see git push)
git push  | *push* your changes (commits) to the GitHub repository (`git push origin master`)
git log   | shows the commit logs

###GitHub Tips
- Keep your version of the repository up to date
- Commit often
- Use meaningful comments when committing changes
- Use `git mv` & `git rm` to move and remove files, respectively
- Pull (update) before pushing your changes

### Basic Unix Commands
<!--please leave this as a table, not as a code block -->
Command   | description
------|-----------------
pwd   | print the working [current] directory
ls    | list files in the current directory
cd    | change directory (eg. to move into the directory called *folder1*, use `cd folder1`. To navigate to the *parent* directory, use `cd ..`)
mv    | move a file (or directory) to another location. This is also used for renamming a file/ directory. (eg. to move *yourname.txt* from *folder1* to *folder2*, use `mv folder1/yourname.txt folder2`. To rename a file from *test1.txt* to *test2.txt*, use `mv test1.txt test2.txt`)
cp    | copy a file or directory (ie. `cp test.txt test_copy.txt`)
rm    | remove [delete] a file
rmdir | remove [delete] a directory


*Example: view the contents of the cloned gittest repository*

	>cd C:/Users/scelmendorf/Desktop/gittest 
	> ls
	# README.md	yourname.txt

*Example: delete the yourname.txt file from your local repository. This will not remove it from the remote repository unless you use git rm*

	> rm yourname.txt
	> ls
	# README.md
<br>

###History

**History on the GUI**

- History is a very useful tab for seeing what other people have been pushing to a repository recently

<figure> <img src="../../images/guihistory.png"> <figcaption> Snapshot of history on the organismalIPT repository. Panel on the right shows changes associated with the highlighted commit. </figcaption> </figure>


<br>


**History on GitHub**

- History is also very useful to see the history of a specific file. You can do this on github.com
- This is especially handy in the event you had a great plan/code/document a few weeks ago, but failed to recognize how awesome it was, and overwrote it. 
- Today's materials won't cover all the ways to revert an entire file in the repository, but if you want to grab an old version of a document, simply:
- Open the file in the repository on github (example shown below is the <a href="https://github.com/NEONdps/organismalIPT/commits/master/beetles/bet_ATBD_NEONDOC001238.docx"> beetle ATBD on the organismalIPT repository</a>)

<figure> <img src="../../images/beetlepage.png"> <figcaption> Beetle ATBD file view on GitHub.com </figcaption> </figure>

- Click the History button

<figure> <img src="../../images/beetlehistory.png"> <figcaption> Beetle ATBD history on GitHub.com </figcaption> </figure>

- Voila!  Your smart ideas of two weeks/months/years ago are right there!  Browse code, view raw, download, the world of two weeks/months/years ago is **ALL STILL THERE**
- Better yet, if you have good commit messages, that amazing code nugget will be easier to find than searching through final_rev.22_comments49_corrections10

## Beyond the Basics

#### Handling a conflict 

John edits HelloWorld.txt to:

	Hello Universe

and commits / pushes his changes to the repository.

You edit the same file to:

	Hello Earth

When you pull the latest copy of the repository before pushing your version, git informs you that there is a conflict (see output below). Here is how you resolve the conflict:

	> git pull
	#remote: Counting objects: 7, done.
	#remote: Compressing objects: 100% (1/1), done.
	remote: Total 4 (delta 2), reused 4 (delta 2)
	#Unpacking objects: 100% (4/4), done.
	#From https://github.com/scelmendorf/gittest.git
	#   bc49f48..f06171d  master     -> origin/master
	#Auto-merging test/HelloWorld.txt
	#CONFLICT (content): Merge conflict in test/HelloWorld.txt
	#Automatic merge failed; fix conflicts and then commit the result.

Git adds standard conflict-resolution markers to the files that have conflicts, so you can open them manually and resolve those conflicts.  If you open the file, it will look like this:

	<<<<<<< HEAD
	Hello Earth
	=======
	Hello Universe
	>>>>>>> f06171dbc245cf1492a7c47f95a2ae9445eee9df
	
This means the version in HEAD (your master branch, because that was what you had checked out when you ran your merge command) is the top part of that block (everything above the =======), while the version in your f06171dbc245cf1492a7c47f95a2ae9445eee9df commit looks like everything in the bottom part. In order to resolve the conflict, you have to either choose one side or the other or merge the contents yourself. For instance, you might resolve this conflict by replacing the entire block with this:

    Hello Earth and Universe

This resolution has a little of each section, and the <<<<<<<, =======, and >>>>>>> lines have been completely removed. After you’ve resolved each of these sections in each conflicted file, run git add on each file to mark it as resolved. Staging the file marks it as resolved in Git.

Now, you can commit your changes and then pull and push to the repository.

### Simple tools to assist in handling a conflict
- A mergetool is a nice GUI that allows you to point and click to any mismatched parts of a file and select which you'd like to keep.
- window-users have had good success with p4merge
- Instructions for p4merge setup and installation are here: [http://danlimerick.wordpress.com/2011/06/19/git-for-window-tip-use-p4merge-as-mergetool/](http://danlimerick.wordpress.com/2011/06/19/git-for-window-tip-use-p4merge-as-mergetool/)
- After installing a mergetool, you can resolve conflicts by running the mergetool in the repository directory

Example:

	> git mergetool
	
When prompted, type yes. A GUI window should open with the two versions of the file on either side. You can use the left and right arrow keys to choose which version to keep.

When you are done, save and close the window.

Now, you can commit your changes and then pull and push to the repository.

##Further reading
#### There are also many great interactive git tutorials….
- https://try.github.io/levels/1/challenges/1
- http://pcottle.github.io/learnGitBranching/
- http://software-carpentry.org/v5/novice/git/index.html


### Interacting with git via R
- Follow instructions here:
- http://www.molecularecologist.com/2013/11/using-github-with-r-and-rstudio/
- TIP: Rstudio uses 'project' to interact with git.  Do NOT push your .Rproj file to the remote repository.  DO add your .Rproj file the .gitignore file.

### What to do when you can't pull from the repository
- A dumb move you will most likely make is to try to clone the repository with files open on your local machine.  This causes problems, especially with file types that git does not automatically merge
- Another problem is that sometimes microsoft office products 'think' you have updated a file, just because you've opened it
- Either of the above This will cause issues when you try to push/pull to the repository, because there are not good tools for merging your changes with those on github
- This will be evident by an error message when you try to pull, such as 'error: your local changes to the following files would be overwritten by merge'[list of files that are causing problems]

#####Solutions
**Git checkout**
discards local changes to a file.  This only works if you have *not yet committed* your changes

First check to see if your changes were committed

    > git status
    
This command show you all files that have been modified but not committed, and or committed, both will cause conflicts when you pull the repo if the remote has also been updated.  If your file is modified not committed, type git checkout <filename>.  
Example:
	
	> git checkout myProblemFile

This will reset your local copy of the file and discard any modifications you have made but *not committed*
	
	> git status 
    # should now show the file is no longer in the 'changes not staged for commit']
	
	> git pull 
	#should work now

**Git reset**
Works to rollback files that you have committed locally but not yet pushed to the remote

- Not covered in the interest of time, but you can google it, or ask one of us.

**The nuclear option**

- When all else fails simply delete your local copy of the repository, and clone it again.
    - If you have work you have not yet pushed to the remote (or even just think you might, and are feeling cautious), you can simply RENAME your local copy of the repository (example (test\_10\_31\_2014Backup)
    - After recloning the repository, you can replace any brilliant work you did (saved in your backup copy), into the new clone of the remote, and try committing and pushing again



       
