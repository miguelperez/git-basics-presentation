# Welcome to git basics

## slide one

We all use git, we all 'know' what git is.

## ...as a reminder

* git its a version control system.
* git stores snapshots not differences.

    >  Conceptually, most other systems store information as a list of file-based changes. These systems (CVS, Subversion, Perforce, Bazaar, and so on) think of the information they keep as a set of files and the changes made to each file over time^1
    
	![file system](http://git-scm.com/figures/18333fig0104-tn.png)

	> Git thinks of its data more like a set of snapshots of a mini filesystem. Every time you commit, or save the state of your project in Git, it basically takes a picture of what all your files look like at that moment and stores a reference to that snapshot. To be efficient, if files have not changed, Git doesn’t store the file again—just a link to the previous identical file it has already stored.^1
	
	![snapshots](http://git-scm.com/figures/18333fig0105-tn.png)
    
Git does it that way because the longer the commit history gets, the more calculation it takes to compare ranges of revisions (deltas).

--

1. http://git-scm.com/book/en/Getting-Started-Git-Basics

## Three states to rule them all

committed, modified, and staged.

1. Committed = data is safely stored in your local database.

2. Modified = changed the file but have not committed it to your database yet.

3. Staged = Current version of file market to go in your next commit snapshot.

	![git stages](http://git-scm.com/figures/18333fig0106-tn.png)


## Enough with the chitchat

Lets work on something.

	$ means to type in the terminal

1. Open a terminal
2. $ mkdir git_basics
3. $ git init
4. $ echo "version 1" >> miguel_perez
5. $ git add miguel_perez
6. $ git commit -m "adding version file"
7. ? WTF


Basically we created a directory, initialized an empty git repository and added a version file to it. Nothing fancy.


--


So, I have a public repository that have some code. That repository its on github. I want you to help me develop my app. so:

go to wwww

and in the same terminal type:

	$ git remote add chopi www.git...

so now you have my repository as a remote repo on your project...

so type

	$ git fetch chopi

	$ ls -la

nothing happened… why?

why not git pull?

## git fetch

>update your local copy of a remote branch. This operation never changes any of your own branches and is safe to do without changing your working copy^1

----
1. http://stackoverflow.com/questions/292357/whats-the-difference-between-git-pull-and-git-fetch

## Why not a git pull?

>git pull does a git fetch followed by a git merge.

This sometimes includes a 'merge' commit. It clutters the github history… seems ugly.

example of a repo that uses heavilly git pull

![with git pull](https://raw.github.com/miguelperez/git-basics-presentation/master/images/Screen%20Shot%202013-07-19%20at%2011.03.51%20AM.png?login=miguelperez&token=cd6a52a56518789d240684387a03022f)

example of a repo that uses a different git workflow.

![with git fetch](https://raw.github.com/miguelperez/git-basics-presentation/master/images/Screen%20Shot%202013-07-19%20at%2011.12.49%20AM.png?login=miguelperez&token=b8279cade3974d37fa53d308831f27ee)

## Lets create a local branch

	git branch -b local_branch
	
The branch its local.

## 

Push it to the remote repo.

	git push origin local_branch

## Rename a branch

	git branch -m <oldname> <newname>
	
If you want to rename the current branch:

	git branch -m <newname>	
	
example:

	git branch -m remove_me_later
	
## Push a branch to a remote repository

	git push remote remove_me_later:remove_me_later

The :remove_me_later tells git to push it to a branch named remove_me_later in the remote repository remove_me_later in this case is optional as we want it to have the same name.

	git push remote remove_me_later
	
## Delete a remote branch

	git push remote :branch_name_to_delete
	
example:

	git push origin :remove_me
	
## So why all this commands?

![lets play a game](http://d15uu3l1sro2ln.cloudfront.net/wp-content/uploads/2013/02/jigsaw-lets-play3.jpg)


## Simple app

Simple js application that needs some features… Lets all finish it together.

Es una calculadora implementada en javascript en donde falta funcionalidad.

## Ah, fork it!

Please go to www.github.com/miguelperez/simple-calc

fork it.

	Now you have a repository that its a clone of mine. Clone it to your machines.

## Mergetool -> this and not that!

By default when fixing conflicts git will use vim for merging conflicts, we can change it to use FileMerge (a visual tool shipped with all macs).

	git mergetool -t opendiff
	
Will open FileMerge for conflicts fixing, if we want to set it as a default tool we would:

	git config --global merge.tool opendiff

## explicar rebase interactivo

## explicar cherry pick

## explicar git reflog

## explicar git reset