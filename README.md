Git-Tutorial

Hello! This is Yan's git tutorial. 
This will make life much easier for you and I with regards to editing and
going back to previous version of code.
A few things of note. I will be teaching this via Git Bash since I feel it
provides a clearer understanding as to what is going on while using Git. 

If you want a more in depth explanation, please read the Git documentation. 
(https://git-scm.com/doc)

I will be writing this under the assumption that you will be working for the 
most part, on your own, which will leave out some of the more complicated 
merging and other issues that come with cooperation. I will briefly touch on 
merging, but you probably will not need much exposure until later when working
with others on the same repository.
This is going to be a fairly watered down version, so here goes. 

First things first, what is Git? 
Git is a version control system. There are losts of different version control
systems, Git is just one of them, and a popular one to boot. 
What is a version control system? It's a way of controlling multiple versions 
of files. Think of it as a way to save off snapshots of your work in different
points of time, much like how a save file would work. Git is basically a way
to create these snapshots of your work and save them off for you. 

The way that you will use Git will consist of a local repostory and a remote 
repository. Think of the local reposity as snapshots that are only on your 
local drive, and the remote repository as snapshots that are on the interwebs. 
To go with a game analogy, it's very much like Steam where you have local
saves, and then yo uhave saves on the Steam cloud. 

When using Git the process will go something along the lines of such. Again, 
note that this is taking into account that you are the sole contributor to the
repository. 
Make changes to the files. 
Add changed files to be staged (saved in the commit (snapshot)).
Commit changes (make the commit (snapshot)).
Push to the remote repository.

Just for funsies, what it may look like if you were working with others 
(workflow may vary depending on your style)
Make changes to the files.
Stash them.
Pull the latest.
Unstash changes.
Resolve any merge conflicts 
Add changes to be committed.
Commit changes. 
Push to the remote repository.

---------------------------------------------------------------------------------------------------

https://git-scm.com/book/en/v2/Customizing-Git-Git-Configuration


Basic setup: 
	Create an account on Github. You will be using this to submit your work. 
	Install Git. Use the default settings. 
	Add your name and email to the global settings.
		Pop open Git Bash anywhere by right clicking in a windows explorer 
		and opening Git Bash.
		Type: 	
			git config --global user.name "John Doe"
			git config --global user.email johndoe@example.com
		Replacing "John Doe" and johndoe@example.com with your information. 
		Note that this information will be public, so if you want to use an 
		online alias, do so.
		
	Also configure the editor you will be using for your commits:
		Open Git Bash anywhere by right clicking in a windows explorer 
		and opening Git Bash.
		Type: 
			git config --global core.editor notepad
		This will configure notepad as your editor for the commits. By default
		it uses vim, so feel free to keep that as your editor if you are 
		comfortable with vim or use another editor of your choice.
			
	Make a folder somewhere to hold your repositories. 
	Inside the folder that you just created, type: 
		git clone https://github.com/YanZ777/Git-Tutorial.git
	A new folder should be created with the name of "Git-Tutorial".
	
---------------------------------------------------------------------------------------------------

There are two options available from here. 

You can continue with my assignments below, or you can do much more well made
try Git tutorial, available here:
https://try.github.io/levels/1/challenges/1

At the very least, I would read through the assignments to get a general idea
of what is going on, then do the tutorials. 

---------------------------------------------------------------------------------------------------

	First assignment. This will teach basics of using Git.
	There is a text file in here named "Guest Book".
	Edit it and add your name to it, and push to the remote repository.
	Go into the directory where you cloned my repository, and open a Git Bash 
	by right clicking and opening Git Bash. 
	First check the status of the remote repository by doing a git status. 
	There should be no local changes - i.e. nothing red or green should appear
	in the window after typing "git status" and hitting enter. This is mainly
	to get you into the habit of checking status before doing anything with
	your repository.
	In a regular text editor, make modifications to the Guest Book file and
	save those changes. When you type git status into Git Bash again, you
	should now see "Guest Book" in red with the text modified to the left of 
	it signaling that it has been modified. It will be under the section 
	"Changes not staged for commit"
	You'll then want to type: git add "Guest Book.txt" 
	This will mark it as staged. Staged files go into the commit. When doing a 
	git status again, it should now show up as green under "changes to be 
	committed".
	You should now commit your changes by typing "git commit". If you have 
	everything configured properly, a notepad window should now open up. This 
	will let you type in a commit message. Your commit message should detail 
	what you've done in that commit. Write a message that others will thank 
	you for when they read it later. In fact, write a message that future you 
	will thank past you for writing.
	
	So in order here are the steps: 
	git status 
		Verify that there are no changes
	git pull
	Make changes to "Guest Book"
	git status 
		Notice that "Guest Book" is now in red labeled modified under the
		section of "Changes not staged for commit"
	git add "Guest Book" 
	git status 
		Notice that "Guest Book" is now in green label modified under the 
		section of "Changes to be committed".
	git commit 
		Write a commit message that future you will thank past you for writing 
	git status 
		Notice that there is now text saying that the 
	git push
	
---------------------------------------------------------------------------------------------------

	Second assignment. This will teach branching.
	What do I mean by branching? This is basically a way for you to explore 
	other avenues of you work without having to do too much work to get back
	to a previous state you were in. 
	Thus far, we have had a pretty linear progress of how commits are made. 
	This means that you commit history visualized may look something like: 
		#################
		# Start Example #
		#################
		# This is how you show the graph in Git Bash by the way.
		$ git log --graph --oneline --decorate --all
		* 10ab3da (HEAD -> master, origin/master, origin/HEAD) Adding files for people to practice on. Added guest book and merge conflict story.
		* 86256a4 Initial commit
		################
		# End  Example #
		################
	In a very simplistic view: 
		* commit B 
		|
		* commit A
			
	In Git, you can create a new branch, and this will do exactly what it says,
	which is to branch off of your current state. 
	To create a branch, you type:
		git branch "branch_name_here" 
	This will create the branch only, but not actually switch you over to that branch. 
	To switch over to a branch, you type: 
		git checkout "branch_name_here"
	Any commits made onto this branch will appear on the new branch you have made. 
	Lets say that you make a commit on this new branch you created.
	The commit history visualized, should now look like: 
		#################
		# Start Example #
		#################
		$ git log --graph --oneline --decorate --all
		* 79731d8 (demo_branch) Intermediate commit. This commit is used to show branching.
		* 10ab3da (HEAD -> master, origin/master, origin/HEAD) Adding files for people to practice on. Added guest book and merge conflict story.
		* 86256a4 Initial commit
		################
		# End  Example #
		################

	
	So now, your commit history visualized will appear something like: 
	In a very simplistic view: 
		
		/
		* commit B 
		|
		|
		|
		* commit A
	
	
---------------------------------------------------------------------------------------------------
	
	Third assignment (please tell me when you are working on this one). 
	This will teach merging and resolving merge conflicts, which as I said, you 
	will not have to do much of, until you are cooperating with others on code.
	There is a text file in here named "Crowdmind Story". 
	Add a new sentence to the last paragraph. Before pushing to the remote 
	repository, please let me know beforehand so I can set up the last bits 
	of the assignemnt.
	Now do the same process as 
	
	
	Several workflows you can do for dealing with merging: 
		workflow 1 (this is the workflow I usually do, but what you do is 
		really up to you): 
			Overall gist: 
				Make changes 
				Stash changes (temporarily save them) 
				Pull from remote 
				Unstash changes 
				Resolve merge conflicts, if any 
				
	

---------------------------------------------------------------------------------------------------
	

Key commands to know: 
	git add 
		different arguments: 
			. 
				add all 
			<file_name> 
				adds that particular file to be staged				
	git clone
	git commit 
		different arguments: 
			-m 
				message 
			--amend 
				amends the most recent commit 
	git log 
		different arguments: 
			-p
				shows the changes for that commit 
			--name-only
				shows only the changed files for that commit 
	git pull 
		really just git fetch + git merge used together
	git push 
	git stash 
		save 
		list 
		pop
		push 
	git status 
		shows the status of your work 
		really useful 
		you'll use it a lot 
		
---------------------------------------------------------------------------------------------------

Interested in trying out git more? 
There are a variety of tutorials out there. Go ahead and Google them.
	
		