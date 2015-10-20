# Git Cheatsheet (Part 1)


## Git Installation
* Download git at <http://git-scm.com>
* To check if git is installed sucessfully, try either the followings

	| git commands    | outcome                            |  
	| :---------------|:---------------------------------- | 
	| `which git`     | `/usr/bin/git`                     | 
	| `git --version` | `git version 2.3.2 (Apple Git-55)` |  








## Configuration

* 3 Levels of configurations, namely, **system**, **single user** and **project**.

	* ***System -*** It applies to all users of the computer
		* located in `cat /etc/.gitconfig`
	* ***Single User -*** It applies to a single user
		* located in `cat ~/.gitconfig`
	* ***Project -*** It applies to the project
		* located in `cat <my_project>/.git/config`




	### Typical Configurations

	<table>
	  <tbody>
	    <tr>
	      <th align="center"> Functions </th>
	      <th align="center">Git</th>
	      <th align="center">Notes</th>
	    </tr>
	    <tr>
	      <td rowspan="2">List Configuration</td>
	      <td align="left"> <code>git config --list</code> </td>
	      <td align="left">  </td>	      
	    </tr>	  
	    <tr>
	      <td align="left"><code>git config user.name</code></td>
	      <td align="left"> To list a specific one  </td>
	    </tr>
	    <tr>
           <td rowspan="5">Typical configuration</td>
	      <td align="left"><code>git config --global user.name "ML"</code></td>
	      <td align="left">  </td>
	    </tr>
	    <tr>
	      <td align="left"><code>git config --global user.emal "ML@mail.com"</code></td>
	      <td align="left">  </td>
	    </tr>
	    <tr>
	      <td align="left"><code>git config --global core.editor "vim"</td>
	      <td align="left"> vim editor  </td>
	    </tr>
	    <tr>
	      <td align="left"><code>git config --global core.editor "mate -wl1"</code></td>
	      <td align="left"> Use TextMate editor <p> 
	      	<ul> 
	      		<li>w=wait and not continue </li>
	      		<li>l1 = starts at line 1 </li>
	      	</ul>
	      </td>
	    </tr>
	    <tr>
	      <td align="left"><code>git config --global color.ui true</code></td>
	      <td align="left"> to tell git to use color  </td>
	    </tr>
	  </tbody>
	</table>




















# Git Cheatsheet (Part 2)

## Initialising a project

* At the root of the project, run `git init`


## Add and Commit
* Perform **Add** and **Commit** in the following orders

	
	| Steps  | git commands                   | Definition                              |
	|:-------| :----------------------------- | --------------------------------------- | 
	| 1      | `git add .`                    | To add everything to repository         |
	| 2      | `git add readme.txt`           | To add only readme.txt to repository    |
	| 3      | `git commit -m "comment"`      | To commit the change to repository      |
	

# Logging

* To check who and what has committed and the changes.

	| git                | Notes           |  
	|:-------------------| :---------------| 
	| `git log`          | -               | 
	| `git help log`     | The help file   |
	| `git log -n 1`     | Last commit     |
	| `git log -n 5`     | Last 5 commits  | 


### Log and search 

| git                                                | Notes                                                   |  
|:---------------------------------------------------| :-------------------------------------------------------| 
| `git log --since=2015-06-18`                       | Everything since that day and everything after          | 
| `git log --until=2015-06-15`                       | Everything from the beginning up until                  | 
| `git log --since=2015-06-15 --until=2015-06-18`    | Both since and until, in between a certain range        | 
| `git log --author="Matthew Lai"`                   | Search by Author                                        | 
| `git log --grep="create"`                          | search by grep, use this to look for bug/fixes          | 	



# Architecture (Optional)


### Two-tree architecture

* The concept of **Repository** and **Working** directory using **'commit'** and **'checkout'**


### Three-tree architecture

* From **Working** to **Staging index**, use `git add file.txt`
* From **Staging index** to **repository**, use `git commit file.txt`
* I can save all my files in the working directory, and only commit one file to respostiory
* We will pull everything from respository to working drectory.



# Git Cheatsheet (Part 3)

## Git workflow

### Git HEAD pointer
* **HEAD** points at the last commit

	| git                             | Outcome                     | Notes                                      |  
	|:------------------------------- |:--------------------------- | :----------------------------------------- | 
	| `cat ~/.git/HEAD`               |  `ref: refs/heads/master`   | Shows that pointer points at master branch | 
	| `cat ~/.git/refs/heads/master`  |  `43c01ad50f3d2269c38...`   | Shows which SHA the HEAD is on             | 
	| `git log HEAD`                  | -                           | Shows the tip of the current brunch        |

			
### Make changes to Files

* Follow them in this order, it is a workflow




<table>
  <tbody>
    <tr>
      <th align="center">Steps</th>
      <th align="center">Git</th>
      <th align="center">outcome</th>
      <th align="center">Notes</th>
    </tr>
    <tr>
    	<td>1</td>
    	<td><code>git status</code></td>
    	<td>
      	<code>On branch master</code> <br>
		<code>nothing to commit, working directory clean</code> 
		</code>
    	</td>
    	<td>This means we are working on the Master brunch and we have the latest, there is nothing to commit</td> 
	</tr>
  </tbody>
</table>


1. The status of 3 different brunches


	`$ git status` 

	```
	On branch master
	nothing to commit, working directory clean
	```

	This means we are working on the Master brunch and we have the latest, there is nothing to commit
	
2. If we create a new file in the directory, and do `$ git status`

	```
	On branch master
	Untracked files:
	  (use "git add <file>..." to include in what will be committed)

		git_tutorial.md

	nothing added to commit but untracked files present (use "git add" to track)
	```
3. This means, gif is not tracking `git_tutorial.md`, so to make sure we can track it, we will add

	`$ git add git_tutorial.md`

4. To add multiple files, one follows another

	`$ git add git_tutorial.md second_file.txt third_file.md`

5. or we can 

	`$ git add .`

6. To confirm, run `$ git status` again, and get the following

	```
	On branch master
	Changes to be committed:
	  (use "git reset HEAD <file>..." to unstage)

		new file:   git_tutorial.md
	```	
7. We should get this, since **`hive_installation_guide.md`** was not added and it is not tracked.

	```
	On branch master
	Changes to be committed:
	  (use "git reset HEAD <file>..." to unstage)

		new file:   git_tutorial.md

	Untracked files:
	  (use "git add <file>..." to include in what will be committed)

		hive_installation_guide.md
	```

8. We will have to also add **`hive_installation_guide.md`** 

	`$ git add hive_installation_guide.md`

9. But we can still commit the one file that was added. 

	`$ git commit -m "create git_tutorial.md"`	

10. Always remember to run `$ git status`

## Meaning of **`$ git status`**

	```
	On branch master
	Changes not staged for commit:
	  (use "git add <file>..." to update what will be committed)
	  (use "git checkout -- <file>..." to discard changes in working directory)

		modified:   git_tutorial.md

	Untracked files:
	  (use "git add <file>..." to include in what will be committed)

		hive_installation_guide.md

	no changes added to commit (use "git add" and/or "git commit -a")
	```

* This means **`hive_installation_guide.md`** has not been added at all to staging
* **git_tutorial.md** was added and committed, but now, it has been edited in the working directory, so it says it is not staged.
	* **modified**: means it is in staging, we will need to commit it.
	* **untracked**: means it is in working, not even added to staging yet.

## Meaning of modification **`$ git diff`**

* **`$ git status`** tells us which file has been modified, but we do not know what has actually been modifeid.
* we use diff in unix, we do something similar by comparing stating and working directory `$git diff`
* It tells us what has been added and what has been changed.
* **_Red_** = -removed, **_Green_** = +added
* It only shows a bit of the chnage, not the whole line that is changed..
* ```@@ -1,4 +1,3 @@``` tells us line one and the next 4 lines are removed and replaced by line 1 and next 3 lines from the new file.
* You can diff one file `$ git diff git_tutorial.md`
* `$ git diff` comparing working and staging, as soon as it is added, there won't be a difference
* `$ git diff --staged`, comparing staging and respository, what has been staged and what has been committed.


## Deleting files
* Supposed to you added your unwanted files to staged by `$git add...`
* and then have them committed to respository `$ git commit -m ""`

###Method 1
* physically remove the file `file_to_delete_1.txt` from your working directory
* then do `$ git status`, tells us something has been deleted
	
	```
	On branch master
Changes not staged for commit:
  (use "git add/rm <file>..." to update what will be committed)
  (use "git checkout -- <file>..." to discard changes in working directory)

	deleted:   file_to_delete_1.txt
	```

* then do `$ git add file_to_delete_1.txt`, 
* Then do `$ git status` and should say 

	```
	On branch master
Changes to be committed:
  (use "git reset HEAD <file>..." to unstage)

	deleted:    file_to_delete_1.txt
	```

* the deleted file has not been commited.
* Then do `$ git commit -m "removed file_to_delete_1.txt"`, it should say

	```
	[master ba8bc3b] remove file_to_delete_1.txt
 1 file changed, 1 deletion(-)
 delete mode 100644 file_to_delete_1.txt
 ```
* we see the fiile is now commited and it actually deletes what is in the repository.
	
* To confirm,  do `$git log`, will see what has been commmited.


### Method 2 

* Do not physically remove the file, and follow these steps
* run `$ git rm file_to_delete_2.txt` 
* Then `$ git status`
* In one step, it is already in staging, we don't have to do add, method 1 is a 2 step processes.

	```
	On branch master
	Changes to be committed:
	  (use "git reset HEAD <file>..." to unstage)

		deleted:    file_to_delete_2.txt
	```
* Now, we can do commit `$ git commit -m "remove file_to_delete_2.txt"`
* It should say

	```
	[master de60864] remove file_to_delete_2.txt
	 1 file changed, 1 deletion(-)
	 delete mode 100644 file_to_delete_2.txt
 
 
* Now, try `$ git log`, will say what has been commited.



## Renaming

### Mehod 1
* Physically rename an existing file that was already commited.
* `$git status`

	```
	On branch master
	Changes not staged for commit:
	  (use "git add/rm <file>..." to update what will be committed)
	  (use "git checkout -- <file>..." to discard changes in working directory)

		deleted:    git_tutorial.md

	Untracked files:
	  (use "git add <file>..." to include in what will be committed)

		git_tutorial_1.md
	```

* It should actually tell us a file is removed and a new file is created an untracked

* `$ git add git_tutorial_1.md` adding the NEW file
* `$ git rm git_tutorial.md` remove the OLD file
* `$ git status`

	```
	On branch master
	Changes to be committed:
	  (use "git reset HEAD <file>..." to unstage)

		renamed:    git_tutorial.md -> git_tutorial_1.md
	```		
	
* now you know it has been removed.
* As long as the files are 50% similar, then it is considered a rename

### Method 2
* `$ git mv git_tutorial_1.md git_tutorial.md`, no need to physically to rename files, just use mv command
* `$ git status`

```
On branch master
Changes to be committed:
  (use "git reset HEAD <file>..." to unstage)

	renamed:    git_tutorial.md -> git_tutorial_1.md
```
* the same thing and ready to be committed.
* This is one step process.
* Let's say you remove the existing file to a new folder, we still use
* physicall create a directory called git
* `$ git mv git_tutorial.md git/git_tutorial.md`
* `$ git status`

```
On branch master
Changes to be committed:
  (use "git reset HEAD <file>..." to unstage)

	renamed:    git_tutorial.md -> git/git_tutorial.md
```	
* `$ git commit -m "Reorganisesd file structure"`

## Undo changes

### Working directory
* If we didn't mean to delete teh files
* `git status` it tells us what has been modeifed
* `git diff` tells you hte changes
* you will see Red and -
* So, if we want the respository version back. and replace what I have 
* `git checkout index.html`
* but checkout can do the brunch as well... dangerours
* `git checkout -- index.html`, we are just talking about a file at the current brunch
* `git status`

### Stating directory
* undo in the staging index
* Let's mess up the staging
* `$ git add git_tutorial.md` where it is a corrupted file

```
On branch master
Changes to be committed:
  (use "git reset HEAD <file>..." to unstage)

	modified:   git_tutorial.md
```
* You siill want all your changes in your working directory
* you add in something you didn't want that is to be committed to respository, but it is still someething you want to have in your working directory. maybe something you don't want yet people to see it.
* `$git reset HEAD git_tutorial.md` go to the last commit, where the HEAD is pointing at and bring it in.

```
Unstaged changes after reset:
M	git_tutorial.md
```

* `$ git status`

```
On branch master
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git checkout -- <file>..." to discard changes in working directory)

	modified:   git_tutorial.md
```	

### Undo commit - replace the last commit
* This is tricky and sometimes what I wanted to do.
* We can only chnage thet last commit, because nothing else depends on it. that is.
* We continue to work on it
* `git commit --amend -m` "We want to undo the last commit"
* All the commit amend do is to replace the last commit with this new one, that is all. You are not removing the last commit, just replace it
* So, we will still need to add and commit first.


### Undo commit - Method 2
* Another way is to really checkout the version that we want and then commit.
* Checkout the version you like `$ git checkout fb485686247c5483088 -- hive_installation_guide.md`
* you will now have this version of hive_isntallation_guide.md in your working directory.
* `$git commit -m "use this hive_installation.md from this version instead"`
* You can't do --amend here because it will look exactly the same as in the previous version.
* If you do ammend, then you must not used the last previous commit, otherwise it is empty.

### Undo commit - Method 3
* this may be best - revert, that is to revert back before we commit
* Find the veersion you need, `git revert def4b34e354c6991c6942a4d712d1b09638e717a`
* this is to bring to your working directory as well as to commit the changes all into resposiotry in one step
* you are replacing everything in that version to its previous state.
* `git status` 

	```
    Revert "trying"
    
    This reverts commit cd9329e88c4be3f5c600d65f274547f1df1fe6de.
	```    

 
* you have gone back to its previous committed state, which is still there.


### Undo multiple commits

* `git reset`
* we usually let git to move the HEAD pointer
* now, we are in control
* we can go to a commit and take it from there, which will overwrites all the rest of the commit, actually I might like this.
	* soft - doesn't change staging and working at the same time, safest.
	* mixed - change staging as well, but not with working directory
	* hard -- change everything, whatever it is.

### Some reset

* take a look at the HEAD poniter
* `cat .git/HEAD` - showing master brunch
* `cat .git/refs/heads`
* 'git reset --soft e0c2fd6b4c3558e4158310a8638f3380529dea53` will take you back to the last stable version, but nothing else in your working or staging is changed.
* You can change the HEAD pointer
* git rest --soft 065e974b2ba217f4c82af386e68cc54a5b7be1ac, the last currupted one
* then you can do another commit
* 

* you can do mixed reset and hard reset.. but I am skipping them for now.

### Remove untracked files from working directory
* usually the log files compiled directory whatever, you want them too
* `git clean`
* It is like this
* 'git status'

	```
	Untracked files:
	  (use "git add <file>..." to include in what will be committed)

		junk.md
	```	 
* You can see junk.md is the untracked file
* `git clean -n`	, and we get this
``` Would remove junk.md```
* `git clean -f` forces it to run
```Removing junk.md```
* but it also removes it physiclaly, so same as rm
* but if it is already in the staging directory, it won't be removed.
* to unstage, `git reset HEAD junk.md`, this is to undo all the add junk.md
* Everything is permantly deleted


## Ignore files


## Branching

* Instead of making classes and your new ideas and remove it from master, you can just work on a burnch until you are happy with it.
* Eventually, merge it to Master
* Just one working directory
* You can switch HEAD to Master brunch or your brunch
* The HEAD is always at the last commit wherever you switch brunch

### To see brunches
* to see brunches `git branch`
* `cat .git/HEAD`

	```ref: refs/heads/master```

* That is just what brunch you are on, which is master
* To see if this is master, you can
* `ls -la .git/refs/heads`, you should see this

	```
	drwxr-xr-x  3 emelle  staff  102 19 Jun 18:44 .
	drwxr-xr-x  4 emelle  staff  136 18 Jun 16:37 ..
	-rw-r--r--  1 emelle  staff   41 19 Jun 18:44 master
	192-168-1-109:mink-0.0.1 emelle$ 
	```

* when we do brunch, it will ad a new brunch there
* The sha is in
* `cat .git/refs/heads/master`, it may say `998d1bf0b5c49e218c3e493ee3f6786a9ced034e`
* and to confirm do `git log --online`

	```
	998d1bf Another stable version
	065e974 Completely wrong stuffs commits
	.
	.
	.
	so on
	```
* They both share the master sha
* To create a new brunch
* `git brunch new_feature`
* `git brunch`, you will get

	```
	* master
  new_feature
192-168-1-109:m
```

* but we are still on the Master branch
* `ls -la .git/refs/heads`

```
drwxr-xr-x  4 emelle  staff  136 20 Jun 12:32 .
drwxr-xr-x  4 emelle  staff  136 18 Jun 16:37 ..
-rw-r--r--  1 emelle  staff   41 19 Jun 18:44 master
-rw-r--r--  1 emelle  staff   41 20 Jun 12:32 new_feature
```

* but the two bracnhes are still pointing at the same commit

* `cat .git/refs/heads/new_feature`, it is the same as `998d1bf0b5c49e218c3e493ee3f6786a9ced034e`

* Is it still pointing to Master?
* `cat .git/HEADS` still points to master `ref: refs/heads/master`
*

### To switch branch

* `git checkout new_feature`, you will get

```
M	git_tutorial.md
Switched to branch 'new_feature'
```
* `cat .git/HEAD` points at `ref: refs/heads/new_feature`
* but they are still pointing at the same commit with same SHA
*  `git commit -am "latest branching"`, you can do both at once
*  Now, the new_feature has this latest commit, but Master don't have it, it is still on the old one.
*  In new_feature, do `git log --oneline`

```b2b64cb latest branching```

* now, switch to master, `git checkout master` gets `Switched to branch 'master'`
* `git branch` gets 
	```
	* master
	  new_feature`
	```
* `git log --oneline` gets you

	```
	998d1bf Another stable version
	```
* I think you just like to commit everything before you switch, because it may overwrite everything on your working directory, or unless we have to copies.
* To show head 'git show HEAD` shows the commit and what I changed

### Create new branch and swithc branches
* `git checkout -b good_title`	
* `git branch`
* `git log --oneline` If we were on Master, this good_title branch will have the entire Master up until its last commit, all in there, in fact, they are identical.
* Make a change and then commit
* `git status`
* `git add file.md`
* `git commit -m "A new file with better title"`
* `git log --oneline`
* This now has an updated commit, now if we go back to commit
* `git checkout master`, you won't have th is commit
* `git log --oneline`
*  `git log --graph --oneline --decorate --all`, you can see the tip of each branch.


### Switching with uncommitted changes
* when we siwtch branches, it must be clean, that is, you must commit before we switch.
* iF it is not clean, you can't do a swtich, that is, if you don't commit, and files are still red.

	``` 
	error: Your local changes to the following files would be overwritten by checkout:
			git_tutorial.md
	Please, commit your changes or stash them before you can switch branches.
	Aborting
	```

#### Method 1
* so method 1 is to commit all the time before switching
* then `git checkout new_branch`
* but we are talking about mostly clean, if we have a new file being added in a branch, and a switch to a different branch won't cost the lost of data, then we can still switch


#### Comparing between branches
* you can check the difference between different branches
* `git branch`
* `git diff master..new_feature` The differences between the tip of HEAD between master and new_feature.
* But we don't use this much
* The one starts later in time comes in first..second
* `git diff --color-words master..new_feature`, just one line instead of one on top of another.
* You can go comparing parent of the branch `git diff --color-words new_feature..master^`
* To see if one branch completely cotains another branch
* `git branch --merged`

```
	master
	new_feature
   *	shorten_title	
```

* We are on shorten_title branch as everything new_feature has, so we can omit it
* Now switch branch, `git check new_feature` now we are on new_feature branch
* `git branch --merged`

```
	master
   *	new_feature
```

* Now you are on new_feature and master contains it but shorten_title isn't included in shorten_title.
* So, we need to do a merge 


#### Renaming branches
* `git branch --more new_feature seo_title` just renaming it, or
* `git branch -m new_feature seo_title`	
* To check ,`git branch`, it should show up

#### Delete branches
* Try it by creating a new brunch
* `git branch brach_to_delete`
* `git branch -d branch_to_delete` or `git branch --delete branch_to_delete`
* `git branch` just to check, it is powerful and dangerous
* You cannot delete a branch that you are currently on, so switch branch first
* `git checkout branch_to_delete`
* run 'git branch -d branch_to_delete`, you will get

```
error: Cannot delete the branch 'branch_to_delete` which you are currently on.
```
* But even you are on a different, you may still not able to delete a branch.
* If you just check something in branch which master branch doesn't have or when we commit changes in that branch, you must merge it first. You will get this

```
error: The branch 'branch_to_delete' is not fully merged.
If you are sure you want to delete it, run 'git branch -D branch_to_delete'.
```

* Ok, then do it `git branch -D branch_to_delete`
* Always use -d, and then do -D is that is what you areally need.

## Merging branches

* you have now tried your things in a new branch, so now, merge it to Master
* To see the changes between 2 branches, 
* `git master master..new_feature`
* The steps are.. Look at the receiver
* `git checkout master`, you are in the master branch now, master is going to recieve the changes from new_feature
* `git merge new_feature`, it will tell you the changes are to be made. everying should go there.
* we can do a diff `git diff master .. new_feature`, there should be no difference there

```
Merge made by the 'recursive' strategy.
 git_tutorial.md | 3 ++-
 1 file changed, 2 insertions(+), 1 deletion(-)
``` 

* you can now delete new_feature because 
* to do merge, make sure it is clean, everything is committed. YES, that is what I think so too.

### fast-forward merge
* you don't need this
* `git merge --no-ff branch`
* 


## Merge conflicts



## Resolving Merge Conflicts
* create a new branch `git checkout -b text_edit`
* make changes in text_edits.
* commit, `git commit -am "text edits on page"`
* back to master branch `git checkout master"`
* make changes on the same file on master branch
* do a master commit, `git commit -am "replace another edit"`
* do both log
	* `git log master --oneline`
	* `git log text_edit --oneline`
	* They are different
* To merge 
* `git branch`
* `git merge text_edit`
* 
* Master and new_feature are teh same.
* switch branch to master
* make a new change
* commit 
* `git merge new_feature`

	```
	Auto-merging hive_installation_guide.md
	CONFLICT (content): Merge conflict in hive_installation_guide.md
	Automatic merge failed; fix conflicts and then commit the result.
	```

* This means I am in the middle of the merge
* `git status`

	```
	On branch master
	You have unmerged paths.
	  (fix conflicts and run "git commit")

	Unmerged paths:
	  (use "git add <file>..." to mark resolution)

		both modified:   hive_installation_guide.md

	no changes added to commit (use "git add" and/or "git commit -a")
	```
* if you open up hive_installation.md directly
* `>>>>>` Head 
* `====` seperate them	

## Resoving this conflicts

### abort merge

* `git merge --abort`
* This is back before `git merge text_edit`


### manually

* Go to `hive_installation_guide.md`, because htat is where the problemm is.
* resolve, add and then commit.
* when you are done have remove all <<< or ==== as only a regular file.
* `git add hive_installation.md`
* `git status`

```
On branch master
All conflicts fixed but you are still merging.
  (use "git commit" to conclude merge)

Changes to be committed:

	modified:   hive_installation_guide.md
```	

* it shows it is ready to be commited.
* Since we are in the middle of the merge, you don't have to provide a message.
* `git commit`

``` [master 5c64b50] Merge branch 'test_edit'```

* `git status`

```
On branch master
nothing to commit, working directory clean
```

* `git log --oneline -4`
* `git branch --merged`
* It shows it has been fully merged into the master branch
* `git log --graph --oneline --all --decorate`
* 


### use a merge tool

* `git mergetool --tools=`
* `git mergetool`


## Stash
* doesn't seem to be useful


## Remotes
* version control etc

* add
* commit
* push (master from remote server points to last commit), master points to last commit in local computer, origin/master points to last commit in local computer
* fetch
* merge


### Global setup

* set up git
* `git config --global user.name "Matthew Lai"`
* `git config --global user.email`

### Next steps (important, the first time you do it)
* This looks like we must check in to remote server since the beginning

* `echo "# mink" >> README.md`
* `mkdir mink`
* `cd mink`
* `git init`
* `touch first_file` (optional)
* `git add first_file`
* `git commit -m 'first commit'`
* `git remote add origin https://github.com/emelle1023/mink.git`
* `git push -u origin master`


* check with `git remote` or `git remote -v`, just tells us the URL for fetching and pushing, you may have to shortcut this
* another way to see this `cat .git/config`

```
[core]
	repositoryformatversion = 0
	filemode = true
	bare = false
	logallrefupdates = true
	ignorecase = true
	precomposeunicode = true
[remote "origin"]
	url = https://github.com/emelle1023/mink.git
	fetch = +refs/heads/*:refs/remotes/origin/*
[branch "master"]
	remote = origin
	merge = refs/heads/maste
```	


* To remove remote `git remote rm origin`, so won't be in the config file
* `cat .git/config`, we get this

```
[core]
	repositoryformatversion = 0
	filemode = true
	bare = false
	logallrefupdates = true
	ignorecase = true
	precomposeunicode = true
[branch "master"]
```

* to add it back again `git remote add origin https://github.com/emelle1023/mink.git`
* `git remote` shows it again

```
origin
```





### Existing Git repo
* `cd mink repo`
* `git remote add origin https://github.com/emelle1023/mink.git`
* `git push -u origin master`


### Importing a subversion Repo
* Check out the guide for step by step instruction

### When you're done
* continue




* git remote
* git remote add <alias> <url>
* git remote add origin https://
* to find the info on the remote
* `cat .git/config`
* To remove the remote `git remote rm origin`
* * you just connect to remote, we haven't add or committed yet




## Pushing to remote

* pushing the branch to the remote server, the whole thing
* use this `git push -u origin master`, which you already know
* `cat .git/config `

```
[core]
	repositoryformatversion = 0
	filemode = true
	bare = false
	logallrefupdates = true
	ignorecase = true
	precomposeunicode = true
[branch "master"]
[remote "origin"]
	url = https://github.com/emelle1023/mink.git
	fetch = +refs/heads/*:refs/remotes/origin/*
[branch "master"]
	remote = origin
	merge = refs/heads/master
```	

* The remote has the branch named `origin`
* You can also check the remote branch like this `ls -la .git/refs/remotes`

```
total 0
drwxr-xr-x  3 emelle  staff  102 23 Jun 13:14 .
drwxr-xr-x  5 emelle  staff  170 23 Jun 13:14 ..
drwxr-xr-x  3 emelle  staff  102 23 Jun 13:28 origin
```

* you can also get a SHA `cat .git/refs/remotes/origin/master`

```
21474396d111e1cbdaf7409a75e33025362d129d
```

* works just the same way
* To see your local branch `git branch`
* To see remote branch `git branch -r`
* To see both, `git branch -a`

## To clone an existing project
* From remote respository to local, assuming we don't have a local to start with (totally empty)
* You certinaly can do this if you like another copy of hte project
* `git clone https://github.com/emelle1023/mink.git`, to make me a local copy of it.
* it will also create a directory `mink`
* To overcome, do this
* `git clone https://github.com/emelle1023/mink.git another_name`
* `git branch` on your newly cloned respository has only one branch, because we have add in other branches yet.



## To push, tracking or non tracking branch (don't seem to be important)
* to track, use -u
* to cline, it will track... to check do cat.git/config
* To push another new branch into remote
* `git branch non_tracking`
* `git push origin non_tracking`
* To check listing, do `cat .git/config` and there is no connection to the future to track.
* -u or cloning will create the traacking
* To make it again a tracking, you can
	* `git config branch.non_tracking.remote origin` and also
	* `git config branch.non_tracking.merge refs/heads/mater` will give you the same configuration 
	* another method is
	* `git branch --set-upstream non_tracking origin/non_tracking`, it will tell you what the remote server is



## Remote pushing 
* make some changes in master local
* `git commit -am "another change'`
* `git log master --oneline'`
* The change is local
* `git log --oneline origin/master'` which is the remote branch, which doesn't reflect the latest change.
* To compare, `git diff origin/master..master`
* To push to origin/master, `git push origin master`, which is hte same as before, but because it is a tracking branch (can check in config), we can do `git push` and that is
* If you want some changes to be fetched, you can do it too. Let's create another branch to intimate another local user.

## Fetch
* The changes doesn't exist in local `git log --oneline -5`
* In fact, it doesn't exist in remote either `git log --oneline -5 origin/master'. Very strange
* Also, it only has one branch here. `git branch`

```
* master
```


* If you ask for remote server `git branch -r`, you get only master too

```
  origin/HEAD -> origin/master
  origin/master
```

* It is all very funny
* THat is because this new local branch another_name needs to sync with the remote master, that is to fetch 
* YOu won't get the latest but the latest since we synch up
* So, you always Fetch.
* `git fetch origin`, because we have only one respository, so we can do `git fetch`
* `origin` should be just the remote respository, that is.
* `git log --oneline -5 origin/master`
* `git branch -r`
* You see the new branch can be seen from the working directory, THe remote contains teh latest change, but the commit is not yet fetched down to your local working directory.
* fetch is NOT harmful, in fact, it is not useful enough.


### Guide lines
* always fetch before you work
* fetch before you push. (but you haven't push), maybe others haves already pushed something similar or conflicts
* fetch often, it just makes sure you are in synch with the respository, but nothing of the code has been checked out and your stuffs are still save.
* You have Merge before you commmit.


## Merge 
* master pointer at server is the same as origin/master pointer in local, which both points to the last commit
* origin/master and master are just in sync
* check all branches `git branch -a`
* take master in your local and of course compare it with origin/master
* `git diff origin/master..master` It tells us the difference master in your working directory as comparing with the latest in remote repository.
* If there are difference, we need to merge
* `git merge origin/master`
* If there were no conflicts, it will just merge
* To see if the local master has the latest or the merged version
* `git log --oneline -3 master`
* You always need to do a fetch and then merge or 
* git pull = git fetch + git merge


## Remote checkout
* this seems to be important
* That is to just download the entire branch and work with it. typically
* Do a check on all branches `git branch -r`

```
  origin/HEAD -> origin/master
  origin/master
  origin/new_feature
```

* `git branch new_feature HEAD` HEAD just means the tip of the current branch (maybe master)
* `git branch new_feature origin/new_feature`, you will have a project called new_feature, and it will track origin/new_feature which should be fetched from remote repository
* if you do `git branch` you will see new_feature in your local
* `cat .git/config`, you should see 

```
[branch "new_feature"]
	remote = origin
	merge = refs/heads/new_feature
```

* It tracks new_feature in origin
* we can delete that branch
* `git branch -d non_tracking`, this is in the local 
* In stead of doing this, we can do checkout
* `git checkout -b new_feature origin/new_feature`


## Pushing to remote with it is already been updated.

* origin/master is just a sync from remote resposiotyr
* you commit your stuffs to local master only.
* You cannot do a push to remote server when some others already pushed their code.
* so you do a fetch, and your origin/master will be in synch and then do a merge. This not necessary because we both cahnged the same line of the code, it is because there are new commit.
* fetch, merge, push
* * The merge is a problem, I am not so clear about those


## To delete a branch remotely
* Method 1
	* `git branch -a`
	* `git push origin :new_feature` 
	* `git branch -r`
	* But it is still here at the local branch `git branch` 
	* usually to push a new branch, it is like this `git push origin new_feature:new_feature`
	* but now, you want to push nothing in remote respository, so `git push origin :new_feature`
* Method 2
* To push back the branch `git push origin new_feature`, you don't need that colon
* `git push origin --delete new_feature`
* To check `git branch -r`, it is gone



## GitHug admin
* Collaborators to add users to the project
* To grant users write access, check if someone is working on the project (Issues)
* To a fork of hte project, no longer part of the original one, this way you will have access to
* The issue is what you will be doing so others won't look at it. should always do that
* Fork, so you can commit changes to your local respository. when you are ready to commit to remote respository, issues a Pull Request.
* 


## Work flow
1. `git checkout master` everything from repository to working
2. `git fetch` local and remote in synch, origin/master
3. `git merge origin/master` to merge the changes from remote which is in origin/master to local master
4. `git checkout -b feeback_form` o you work on a new feature on a seperate branch. if you don't want it, you can throw it away. This is to checkout a new branch, or you can create a new branch and switch to it.
5. `git add feedback.html` when my new page is done
6. `git commit -m "Add customer feedback form` To commit to my local respository
7. `git fetch` to make your work in sync
8. `git push -u origin feedback_form` You want to know if there were any issues to conflict your working directory, if not, push your branch to remote. -u making it as a tracking branch. Now all your coworkers can see it. 
9. Send an email to others. please take a look and let me think.
10. Your coworkers will
11. `git checkout msater`
12. `git fetch`, until she does a fetch, she can't see the new branch, it is not synch up.
13. `git merge origin/master`
14. `git checkout -b feedback_form origin/feedback_form` to see my branch and to get it from remote. can always do a `git branch -r`
15. can check what I did, `git log`
16. `git show 84b6afd0` to take a look at it. or use `git show HEAD` if that was the last commit, or `git show feedback_form` the branch name.
17. She made a change and commit, `git commit -am "Add tour selector to feedback form`, that is all in the local machine
18. `git fetch`, to put it on the remote machine
19. `git push`, if all clear, just push. and she is done.
20. Send a email, it looks great and just one change.
21. Back to me
22. `git fetch`, to see the change.
23. `git log -p feedback_form..origin/feedback_form` to see the diff of each log entry. THat is the difference from my copy of feedback_form to the remote respository.
24. `git merge origin/feedback_form` to merge both feedback_forms, now tnhey are in sync, this is a forward merge, because you want only the latest, and we have not chnaged nothing, else. 
25. `git checkout master` switch to master branch
26. `git fetch`
27. `git merge origin/master` if there were changes from our masters, but likely a forward merge. It just means you have done nothing and wanting to the latest.
28. `git merge feedback_form` merge changes from feedback_form to master.
29. `git push` once resolve all conflicts. now my work is in the remote.

