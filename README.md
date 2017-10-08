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
Git is a version control system. There are lots of different version control
systems, Git is just one of them, and a popular one to boot. 
What is a version control system? It's a way of controlling multiple versions 
of files. Think of it as a way to save off snapshots of your work in different
points of time, much like how a save file would work. Git is basically a way
to create these snapshots of your work and save them off for you. 

The way that you will use Git will consist of a local repostory and a remote 
repository. Think of the local reposity as snapshots that are only on your 
local drive, and the remote repository as snapshots that are on the interwebs. 
To go with a game analogy, it's very much like Steam where you have local
saves, and then you have saves on the Steam cloud. 

An important thing of note: 
You don't have to work on a remote repository. You can actually just work on
a local repository. The remote repostiroy just lets you have your commits saved
in an additional location other than your local computer, so if something does 
happen to said computer, it'll be backed up.

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

For any of this, do not be afraid to ask for help! 

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
	
	FYI: 
		You can check your commit history! 
		Just type in git log and it will show the series of commits that have 
		been made on that branch.
		Next to each commit, there is a combination of letters and symbols. 
		That combination of letters and symbols is called a hash, and it 
		represents the id of the commit. Every commit has this id, and every 
		id is unique. 

---------------------------------------------------------------------------------------------------

	Not really an assignment more so than a lecture. This will teach branching.
	What do I mean by branching? This is basically a way for you to explore 
	other avenues of you work without having to do too much work to get back
	to a previous state you were in. 
	Thus far, we have had a pretty linear progress of how commits are made. 
	This means that the commit history visualized may look something like: 
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
	In simplistic view: 
		* commit B (on master branch)
		|
		* commit A (on master branch)
			
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
	In simplistic view: 
		* commit C (this commit is on demo_branch only) 
		|
		* commit B (on master and demo branch)
		| 
		* commit A (on master and demo branch) 
	Why are there no graphs in this branch? There aren't any graphs in this
	branch because the branches haven't diverged yet. Currently, the second 
	branch that I've made has everything on the original branch, plus an extra
	commit. In other terms, the new branch made is a superset of the original 
	branch / the original branch is a subset of the new branch.
	
	
	If you switch back to your original branch (git checkout 
	<orignial_branch_name>) and make a commit, git will begin to diverge the 
	two. 
	Now the commit history visualized will appear something like: 
		#################
		# Start Example #
		#################
		$ git log --graph --oneline --decorate --all
		* 009df45 (HEAD -> master) Another commit to continue showing branching.
		| * 79731d8 (demo_branch) Intermediate commit. This commit is used to show branching.
		|/
		* 10ab3da (origin/master, origin/HEAD) Adding files for people to practice on. Added guest book and merge conflict story.
		* 86256a4 Initial commit
		################
		# End  Example #
		################
	In simplistic view: 
		* commit D (on master branch only)
		| * commit C (on demo_branch only)
		|/
		* commit B (on master and demo branch)
		|
		* commit A (on master and demo branch)
		
	What does this all mean for you? 
	Well this means that you can easily switch between different states (the
	different commits that you have) without losing all your changes or undoing
	a lot of work. This is useful for working on different tasks in the same 
	repository. Actually, when you checkout to a branch, you can also checkout 
	to different commits, so you can effectively go back in time with the git 
	history.
	
	
---------------------------------------------------------------------------------------------------
	
	Third assignment (please tell me when you are working on this one). 
	This will teach merging and resolving merge conflicts, which as I said, you 
	will not have to do much of, until you are cooperating with others on code.
	There is a text file in here named "Crowdmind Story". 
	Add a new sentence to the last paragraph. Before pushing to the remote 
	repository, please let me know beforehand so I can set up the last bits 
	of the assignemnt.
	Now do the same process as making a commit. Except now, if you are trying 
	to pull, Git won't let you because you have changes on your local branch
	that aren't saved and don't exist on the remote branch. Git doesn't let 
	you pull so that you don't lose you work. 
	Now how do we fix this? 
	
	Several workflows you can do for dealing with merging: 
		workflow 1 (this is the workflow I usually do, but what you do is 
		really up to you): 
			Overall gist: 
				Make changes 
				Stash changes (temporarily save them) 
				Pull from remote 
				Unstash changes 
				Resolve merge conflicts, if any 
			
		workflow 2 (this is workflow is a bit more permanent): 
			Overall gist: 
				Make changes 
				Commit changes (without pulling, I know)
				Pull from remote 
				Resolve merge conflicts, if any
				
	Whichever workflow you take, there may be merge conflicts that you have to
	fix. When this happens, git status will show you which files have merge 
	conflicts and git will be in the merging state. This type of merge conflict 
	occurs when you have changes on your local branch that conflict with the 
	changes on the remote branch. Basically this means that someone tried to 
	change the same things that you did, and now Git doesn't know which changes
	to take. 
	To fix the merge conflictson the files, open the file in your favorite 
	editor. There are a great many diff tools (tools to help you view the
	difference between the two files) out there, but I think it's important 
	to learn how to read the diff raw so that you understand what is occuring 
	when you do a merge. 
	In your file, you will see certain notations. 
		>>>>> commit #
			This means the start of the merge conflict, these changes 
			are the ones grabbed from that particular hash.
		=====
			Separating line between the merge conflict.
		<<<<< commit #
			End of the merge conflict, these are the changes grabbed from that
			particular hash. 
			
	An example may look like: 	
		code stuff
		code stuff code stuff 
		>>>>> HEAD 
			Original changes that came from the branch you are currently on
		=====
			Modified changes from the branch that you are merging in.
		<<<<< 52a1d908ab131c2e82
		more code stuff blah blah blah 
		code code code
		
	To get rid of the merge conflict, you remove all the delimiting markers 
	and put in the changes you want. They can be the original changes, the 
	modified changes, a mixture of the two, or something completely different 
	(althoug that is usually not recommended). 
	
	Going based off of the example above, we would then have: 
		code stuff
		code stuff code stuff 
			Original changes that came from the branch you are currently on
		more code stuff blah blah blah 
		code code code
		
	We would then go back to our git bash prompt and check on the git status.
	Even though we had fixed the merge conflict, git will not consider it 
	resolved until we mark it as resolved, which means adding it as a file to
	be staged. Once that has been done, we make a commit (this will usually
	have information about the merge conflict with it in this case). We then
	follow through with the rest of the steps of pushing it out to the remote
	repository. 
	
	FYI: 
		Yes, resolving a merge conflict is a commit. If you check the git
		history, you will see the merge conflict commit.
		
	Then continue on your merry way! 	
	

---------------------------------------------------------------------------------------------------
	

Key commands to know: 
	git add 
		Stages files for the commit.
		Available arguments: 
			. 
				Adds all the files (including untracked ones!). 
			<file_name> 
				Adds that particular file to be staged.
	git checkout 
		Available arguments: 
			<branch_name>
				Changes the files to reflect the changes on this branch.
			<commit_hash>
				Changes the files to reflect the changes leading up to this 
				commit.
	git clone
		Available arguments: 
			<repository link>
				Clones the remote repository to the local drive.
	git commit 
		Creates a commit. Opens up the text editor you configured Git to 
		so that you can write your commit message.
		Available arguments: 
			-m "<message here in quotes>"
				Shorthand way of creating a commit with the given message in 
				quotes. 
			--amend 
				Amends the most recent commit.
	git log 
		Shows all the commits on the branch starting with most recent commits
		in time to least recent commits in time.
		Available arguments: 
			-p
				Shows the changes for that commit.
			--name-only
				Shows only the names of the changed files for that commit.
	git pull 
		This is really just git fetch + git merge used together.
			Takes the commits from the remote repository that are not yet on
			the local repository and puts them on the local repository.
			Notifies the user of any merge conflicts, if needed.
			
	git push 
		Pushes the commits on the local branch to the remote repository.
			Takes all the commits on the local repostiroy that are not yet on
			the remote repository and puts them on the remote repository.
	git stash
		Git stash is a way for users to temporarily save things without making
		a commit 
		WARNING: If you drop things from the stash, they are deleted. There is
		no way to recover them like with a commit.
		Available arguments: 
			apply stash@{<some_number_here>}
				applies the stash corresponding to the some_number_here
			drop stash@{<some_number_here>}
				removes the stash from the list of stashes
			list 
				Shows the current stash.
			pop 
				With no arguments, this will just take the last stash you pushed
				on, apply it, and drop it from the stash list
				Think of it as a git stash apply and a git stash drop combined.
				different arguments: 
					stash@{<some_number_here>}	
			save "message in quotes"
				Saves the stash with the following message in quotes.
	git status 
		Git status is a way for you to show the current state that you are in. 
		This is mainly pertient so you can view which files have changed as
		well as which files are currently staged for the commit. It will also
		let you know the state of your branch relative to the remote
		repository (if there is one).
		
---------------------------------------------------------------------------------------------------

Interested in trying out git more? 
There are a variety of tutorials out there. Go ahead and Google them.
	
		