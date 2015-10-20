# Git CheatSheet (Part 6)

1. Branching


## 1. Branching

* Create a branch and try your new ideas and eventually merge it with Master
* You can switch **HEAD** between Master branch or your branch.
* The **HEAD** is always at the last commit of whatever branch you are on.

## 2. HEAD branches

<table>
  <tbody>
    <tr>
      <th>git</th>
      <th>Outcome</th>
      <th>Notes</th>
    </tr>
    <tr>
      <td><font size="1"><code>git branch</code></font></td>
      <td>
      <font size="1"><code>* <font color="green">master</font></code></font></br>
      <font size="1"><code>new_feature</code></font></br>
      <font size="1"><code>test_edit</code></font>
      </td>
      <td><font size="1">
          To see what branch there are <br>
          You see <code>* <font color="green">master</font></code> means it is on master
      </font></td>
    </tr>
    <tr>
      <td><font size="1"><code>cat .git/HEAD</code></font></td>
      <td><font size="1"><code>ref: refs/heads/master</code></font></td>
      <td><font size="1">
          To find out what branch it is now pointing at</br>
          This tells us we are on <code><font color="green">master</font></code>
      </font></td>
    </tr>
    <tr>
      <td><font size="1"><code>ls -la .git/refs/heads</code></font></td>
      <td><font size="1">
        <font size="1"><code>drwxr-xr-x  3 em  staff  102 19 Jun 18:44 .</code></font><br>
	   <font size="1"><code>drwxr-xr-x  4 em  staff  136 18 Jun 16:37 ..</code></font><br>
	   <font size="1"><code>-rw-r--r--  1 em  staff   41 19 Jun 18:44 master</code></font><br>
	   <font size="1"><code>mink-0.0.1 em$ </code></font>
      </font></td>
      <td><font size="1">To see if this is <font color="green"><code>master</code></font></font></td>
    </tr>
    <tr>
      <td><font size="1"><code>cat .git/refs/heads/master</code></font></td>
      <td><font size="1"><code>998d1bf0b5c3ee...</code></font></td>
      <td><font size="1">To check where the <code><b>SHA</b></code> is</font></td>
    </tr>
    <tr>
      <td><font size="1"><code>git log --oneline</code></font></td>
      <td><font size="1">
	     <code>998d1bf Another stable version</code><br>
	     <code>065e974 Completely wrong stuffs commits</code><br>
	     <code>&nbsp;&nbsp;.</code><br>
	     <code>&nbsp;&nbsp;.</code><br>
	     <code>&nbsp;&nbsp;.</code><br>
	     <code>so on</code>
      </font></td>
      <td><font size="1">To double check in the <code>log</code></font></td>
    </tr>
  </tbody>
</table>

## 2. Create a branch

<table style="width:100%">
  <tr>
    <th>git</th>
    <th>Outcome</th> 
    <th>Notes</th>
  </tr>
  <tr>
    <td><font size="1"><code>git branch new_feature</code></font></td>
    <td><font size="1">
      <code>drwxr-xr-x  4 emelle  staff  136 20 Jun 12:32 .</code><br>
      <code>drwxr-xr-x  4 emelle  staff  136 18 Jun 16:37 ..</code><br>
      <code>-rw-r--r--  1 emelle  staff   41 19 Jun 18:44 master</code><br>
      <code>-rw-r--r--  1 emelle  staff   41 20 Jun 12:32 new_feature</code>         
    </font></td> 
    <td><font size="1">    
        To create a new brunch <br>
        They both share the same <b>SHA</b> as <font color="green">master</font>
    </font></td>
  </tr>
  <tr>
    <td><font size="1"><code>ls -la .git/refs/heads</code></font></td>
    <td><font size="1"></font></td> 
    <td><font size="1">You are still on the master branch</font></td>
  </tr>
  <tr>
    <td><font size="1"><code>cat .git/refs/heads/new_feature</code></font></td>
    <td><font size="1"><code>998d1bf0b5c49e218c3e493ee3f6786a9ced034e</code></font></td> 
    <td><font size="1">Pointing at the same SHA as master</font></td>
  </tr>
  <tr>
    <td><font size="1"><code>cat .git/HEADS</code></font></td>
    <td><font size="1"><code> 998d1bf0b5c49e218c3e493ee3f6786a9ced034e </code></font>
    </td> 
    <td><font size="1"> In fact, it is still pointing at master</font></td>
  </tr>
</table>

* We will have to switch branch even after creating a new branch.

## 3. Switch branches

<table style="width:100%">
  <tr>
    <th>git</th>
    <th>Outcome</th> 
    <th>Notes</th>
  </tr>
  <tr>
    <td><font size="1"><code> git checkout new_feature </code></font></td>
    <td><font size="1">
        <code> M &nbsp;  git_tutorial.md </code><br>
	   <code> Switched to branch 'new_feature' </code>
    </font></td> 
    <td><font size="1"> To switch to a new branch </font></td>
  </tr>
  <tr>
    <td><font size="1"><code> cat .git/HEAD </code></font></td>
    <td><font size="1"><code> ref: refs/heads/new_feature </code></font></td> 
    <td><font size="1">
      Now you have switched branch to <code>new_feature </code><br>
      But they are still pointing at the same <b>SHA</b>
    </font></td>
  </tr>
  <tr>
    <td><font size="1"><code> git commit -am "latest branching" </code></font></td>
    <td><font size="1"><code> </code></font></td> 
    <td><font size="1">
      <code> new_feature </code> has this latest commit, but Master is still on the old one </code>
    </font></td>
  </tr>
  <tr>
    <td><font size="1"><code> git log --oneline </code></font></td>
    <td><font size="1"><code> b2b64cb latest branching </code></font></td> 
    <td><font size="1">
      In <code>new_feature</code>, check the latest <b>SHA</b> </code>
    </font></td>
  </tr>
  <tr>
    <td><font size="1"><code> git checkout master </code></font></td>
    <td><font size="1"><code> Switched to branch 'master' </code></font></td> 
    <td><font size="1"> To switch back to <code> master </code> </code></font></td>
  </tr>
  <tr>
    <td><font size="1"><code> git branch </code></font></td>
    <td><font size="1">
      <code> * <font color="green"> master </font></code><br>
	 <code> new_feature </code>
    </font></td> 
    <td><font size="1"><code> To check which branch you are on </code></font></td>
  </tr>
  <tr>
    <td><font size="1"><code> git log --oneline </code></font></td>
    <td><font size="1"><code> 998d1bf Another stable version... </code><br></font></td> 
    <td><font size="1"> To double check the <code> log </code> </font></td>
  </tr>  
  <tr>
    <td><font size="1"><code> git show HEAD </code></font></td>
    <td><font size="1"><code> </code><br></font></td> 
    <td><font size="1"> shows <b>HEAD</b> and the commit and what was changed </font></td>
  </tr>  
</table>

* `commit` everything upon switching branches, because `checkout` may overwrite everything on your working directory


## 4. Steps to create a new branch and switch branches

* This is just a summary of section 2 and 3.

	<table>
	  <tr>
	   <th>Section</th>
	   <th>Steps</th>
	   <th>git</th>
	   <th>Notes</th>
	  </tr>
	  <tr>
	   <td rowspan="3"><font size="1"> Create <br> new branch </font></td>
	   <td align="center"><font size="1"> 1 </font></td>
	   <td><font size="1"><code> git checkout -b good_title </code></font></td>
	   <td><font size="1"> 
	     Switch to latest branch <code>good_title</code>. <br>
	     It should also create the branch.
	   </font></td>
	  </tr>
	  <tr>
	   <td align="center"><font size="1"> 2 </font></td>
	   <td><font size="1"><code> git branch </code></font></td>
	   <td><font size="1"> To see what branch you have </font></td>
	  </tr>
	  <tr>
	   <td align="center"><font size="1"> 3 </font></td>
	   <td><font size="1"><code> git long --oneline </code></font></td>
	   <td><font size="1"> 
	     <code>good_title</code> branch would contain the latest <code>master</code>. <br>
	     Both branches are identical </font></td>
	  </tr>
	  <tr>
	   <td rowspan="8"><font size="1"> Make changes <br> in <br> new branch </font></td>
	   <td align="center"><font size="1"> 4 </font></td>
	   <td><font size="1"> </font></td>
	   <td><font size="1"> Now, make a change in <code>good_title</code> </font></td>
	  </tr>
	  <tr>
	   <td align="center"><font size="1"> 5 </font></td>
	   <td><font size="1"><code> git add file.md </code></font></td>
	   <td><font size="1"> Add that file you have changed </font></td>
	  </tr>
	  <tr>
	   <td align="center"><font size="1"> 6 </font></td>
	   <td><font size="1"><code> git commit -m "A new file with better title" </code></font></td>
	   <td><font size="1"> Commit and comment it </font></td>
	  </tr>
	  <tr>
	   <td align="center"><font size="1"> 7 </font></td>
	   <td><font size="1"><code> git log --oneline </code></font></td>
	   <td><font size="1"> Check the <code>log</code> if it has been committed </font></td>
	  </tr>
	  <tr>
	   <td align="center"><font size="1"> 8 </font></td>
	   <td><font size="1"><code> git checkout master </code></font></td>
	   <td><font size="1"> Back to <code>master</code> branch </font></td>
	  </tr>
	  <tr>
	   <td align="center"><font size="1"> 9 </font></td>
	   <td><font size="1"><code> git log --oneline </code></font></td>
	   <td><font size="1"> 
	     Check the log in <code>master</code> of its latest commit. <br>
	     They may not have the same commit. 
	   </font></td>
	  </tr>
	  <tr>
	   <td align="center"><font size="1"> 10 </font></td>
	   <td><font size="1"><code> git log --graph --oneline --decorate --all </code></font></td>
	   <td><font size="1"> To see the tip of each branch </font></td>
	  </tr>
	</table>


## 5. Switching with uncommitted changes
* Upon switching branches, it must be clean. That is, you must **commit** before switching. Else, you can't swtich to a differenct branch. 
* If you don't **commit**, files will still be shown in red wiht `git sta†us`.

	```
	error: Your local changes to the following files would be overwritten by checkout:
			git_tutorial.md
	Please, commit your changes or stash them before you can switch branches.
	Aborting
	```

### Method 1 
* **commit** all the time before switching

	<table>
	  <tr>
	    <th><font size="1">Step</font></th>
	    <th><font size="1">git</font></th>
	    <th><font size="1">Notes</font></th>
	  </tr>
	  <tr>
	    <td><font size="1">1</font></td>
	    <td><font size="1"><code>git commit -am "Latest commit"</code></font></td>    
	    <td><font size="1">Do a commit</font></td>
	  </tr>
	  <tr>
	    <td><font size="1">2</font></td>
	    <td><font size="1"><code>git checkout new_feature</code></font></td>    
	    <td><font size="1">Switch branch</font></td>
	  </tr>
	</table>

* But we are talking about mostly clean, if we have a new file being added in a branch, and a switch to a different branch won't cost the lost of data, then we can still switch.


### Method 2
* Compare between branches

	<table>
	  <tr>
	    <th><font size="1">Step</font></th>
	    <th><font size="1">git</font></th>
	    <th><font size="1">outcome</font></th>
	    <th><font size="1">Notes</font></th>
	  </tr>
	  <tr>
	    <td><font size="1">1</font></td>
	    <td><font size="1"><code>git branch</code></font></td>
	    <td></td>
	    <td><font size="1">Check all existing branches</font></td>
	  </tr>
	  <tr>
	    <td><font size="1">2</font></td>
	    <td><font size="1"><code>git diff master..new_feature</code></font></td>
	    <td></td>
	    <td><font size="1">
	      Check the difference between different branches.<br>
	      This tells the differnces between tip of HEAD between master and new_feature.<br>
	      But we don't use this much.<br>
	      The newwer branch comes second.<br>
	      <code>old_branch..new_branch</code>
	    </font></td>
	  </tr>
	  <tr>
	    <td><font size="1">2</font></td>
	    <td><font size="1"><code>git diff --color-words master..new_feature</code></font></td>
   	    <td></td>
	    <td><font size="1">just one line instead of one on top of another</font></td>
	  </tr>
	  <tr>
	    <td><font size="1">3</font></td>
	    <td><font size="1"><code>git diff --color-words new_feature..master</code></font></td>
	    <td></td>
	    <td><font size="1">You can go comparing parent of the branch</font></td>
	  </tr>
	  <tr>
	    <td><font size="1">4</font></td>
	    <td><font size="1"><code>git branch --merged</code></font></td>
	    <td><font size="1"><code>
	    		master <br>
			new_feature <br>
   			* shorten_title	
	    </code></td>
	    <td><font size="1">To see if one branch completely cotains another branch</font></td>
	  </tr>
	  <tr>
	    <td><font size="1">5</font></td>
	    <td><font size="1"><code>git checkout new_feature</code></font></td>
	    <td></td>
	    <td><font size="1">Now, to finally switch branch and we are on <code>new_feature</code></font></td>
	  </tr>
	  <tr>
	    <td><font size="1">6</font></td>
	    <td><font size="1"><code>git branch --merged</code></font></td>
	    <td><font size="1"><code>
	    		master <br>
			* new_feature
	    </code></font></td>
	    <td><font size="1">To see if our branch submerged in <code>master</code></font></td>
	  </tr>
	</table>


## 6. Renaming branches

<table>
  <tr>
    <th><font size="1">Step</font></th>
    <th><font size="1">git</font></th>
    <th><font size="1">Notes</font></th>
  </tr>  
  <tr>
    <td><font size="1">1</font></td>
    <td><font size="1">
      <code>git branch --more new_feature seo_title</code> <br>
      <code>git branch -m new_feature seo_title</code>      
    </font></td>
    <td><font size="1">
      To just rename it. <br>
      A simplified version. <br>
    </font></td>
  </tr>
  <tr>
    <td><font size="1">2</font></td>
    <td><font size="1"><code>git branch</code></font></td>
    <td><font size="1">After renaming, check branch</font></td>
  </tr>  
</table>


## 7. Delete branches

* Try by creating a new branch

<table>
  <tr>
    <th><font size="1">Step</font></th>
    <th><font size="1">git</font></th>
    <th><font size="1">Outcome</font></th>
    <th><font size="1">Notes</font></th>
  </tr>
  <tr>
    <td><font size="1">1</font></td>
    <td><font size="1"><code>git checkout branch_del</code></font></td>
    <td><font size="1"></font></td>
    <td><font size="1">Create a new branch</font></td>
  </tr>
  <tr>
    <td><font size="1">2</font></td>
    <td><font size="1">
      <code>git branch -d branch_del</code><br>
      <code>git branch -delete branch_del</code>
    </font></td>
    <td><font size="1"></font></td>
    <td><font size="1">Delete the branch</font></td>
  </tr>
  <tr>
    <td><font size="1">3</font></td>
    <td><font size="1"><code>git branch</code></font></td>
    <td><font size="1"></font></td>
    <td><font size="1">Check what branches we have</font></td>
  </tr>
  <tr>
    <td><font size="1">4</font></td>
    <td><font size="1"><code>git branch -d branch_del</code></font></td>
    <td><font size="1">
      <code>error: Cannot delete the branch</code><br>
      <code>'branch_del`</code><br>
      <code>which you are currently on.</code>
    </font></td>
    <td><font size="1">You cannot delete a branch we are currently on.</font></td>
  </tr>
  <tr>
    <td><font size="1">5</font></td>
    <td><font size="1"><code>git branch -d branch_del</code></font></td>
    <td><font size="1">
      <code>error: The branch 'branch_del' </code><br>
      <code>is not fully merged.</code><br>
      <code>If you are sure <c/code><br>
      <code>you want to delete it, run<code><br> 
      <code>'git branch -D branch_del'.</code>
    </font></td>
    <td><font size="1">
      Even on different branch, sometimes, still can't delete.<br>
      This means sometihng in branch_del where master branch doesn't have. <br>
      Usually, this means you haven't merged
    </font></td>
  <tr>
    <td><font size="1">6</font></td>
    <td><font size="1"><code>git branch -D branch_del</code></font></td>
    <td><font size="1"></font></td>
    <td><font size="1">
      Run the git as suggested.<br>
      But use <code>-d</code> rather than <code>-D</code> unless you must.
    </font></td>
  </tr>  
</table>


## 8. Merging branches
* After you have tried your things in a new branch, you can merge it to **master**

	<table>
	  <tr>
	    <th><font size="1">git</font></th>
	    <th><font size="1">Outcome</font></th>
	    <th><font size="1">Notes</font></th>    
	  </tr>
	  <tr>
	    <td><font size="1"><code>git master master..new_feat</code></font></td>
	    <td><font size="1"></font></td>
	    <td><font size="1">To see changes between 2 branches</font></td>    
	  </tr>
	  <tr>
	    <td><font size="1"><code>git checkout master</code></font></td>
	    <td><font size="1"></font></td>
	    <td><font size="1">
	      Now in the master branch, and <code>master</code> 
	      is going to receive the changes from <code>new_feat</code>.
	    </font></td>    
	  </tr>
	  <tr>
	    <td><font size="1"><code>git merge new_feat</code></font></td>
	    <td><font size="1"></font></td>
	    <td><font size="1">Tells us the changes are to be made.</font></td>    
	  </tr>
	  <tr>
	    <td><font size="1"><code>git diff master..new_feat</code></font></td>
	    <td><font size="1">
	      <code>Merge made by the 'recursive' strategy.</code><br>
	  	 <code>git_tutorial.md | 3 ++-</code><br>
	 	 <code>1 file changed, </code><br>
	 	 <code>2 insertions(+), </code><br>
	 	 <code>1 deletion(-)</code>
	    </font></td>
	    <td><font size="1">To confirm if there are differences.</font></td>    
	  </tr>
	  <tr>
	    <td><font size="1"><code>git delete new_feat</code></font></td>
	    <td><font size="1"></font></td>
	    <td><font size="1">Youc can now delete <code>new_feat</code>.</font></td>    
	  </tr>
	</table>

* To merge, make sure it is clean, everything is committed.

## 9. Fast-forward merge (not needed)
* `git merge --no-ff branch`



## 10. Resolving Merge Conflicts

<table>
  <tr>
    <th><font size="1">Steps</font></th>	
    <th><font size="1">git</font></th>		    
    <th><font size="1">Outcome</font></th>	
    <th><font size="1">Notes</font></th>	
  </tr>
  <tr>
    <td><font size="1">1</font></td>
    <td><font size="1"><code>git checkout -b text_edit</code></font></td>
    <td><font size="1"></font></td>
    <td><font size="1">Create a new branch and make changes</font></td>
  </tr>
  <tr>
    <td><font size="1">2</font></td>
    <td><font size="1"><code>git commit -am "text edits page"</code></font></td>
    <td><font size="1"></font></td>
    <td><font size="1">Commit the changes</font></td>
  </tr>
  <tr>
    <td><font size="1">3</font></td>
    <td><font size="1"><code>git checkout master</code></font></td>
    <td><font size="1"></font></td>
    <td><font size="1">Switch to master branch</font></td>
  </tr>
  <tr>
    <td><font size="1">4</font></td>
    <td><font size="1"></font></td>
    <td><font size="1"></font></td>
    <td><font size="1">Make changes in the same file</font></td>
  </tr>
  <tr>
    <td><font size="1">5</font></td>
    <td><font size="1"><code>git commit -am "Another edit"</code></font></td>
    <td><font size="1"></font></td>
    <td><font size="1">Commit the chnages in master</font></td>
  </tr>
  <tr>
    <td><font size="1">6</font></td>
    <td><font size="1">
      <code>git log master --oneline</code><br>
      <code>git log text_edit --oneline</code>
    </font></td>
    <td><font size="1"></font></td>
    <td><font size="1">Check the logs for both branches, they are different</font></td>
  </tr>
  <tr>
    <td><font size="1">7</font></td>
    <td><font size="1">
      <code>git branch</code><br>
      <code>git merge text_edit</code>
    </font></td>
    <td><font size="1">
    	 <code>Auto-merging guide.md</code><br>
	 <code>CONFLICT (content): </code><br>
	 <code>Merge conflict guide.md</code><br>
	 <code>Automatic merge failed; </code><br>
	 <code>fix conflicts and then </code><br> 
	 <code>commit the result.</code>
    </font></td>
    <td><font size="1">
      Check what branches there are and merge them. <br>
      There you may have some problems. <br>
      This means we are in the middle of a merge.
    </font></td>
  </tr>
  <tr>
    <td><font size="1">8</font></td>
    <td><font size="1"><code>git status</code></font></td>
    <td><font size="1">    
	<code>On branch master </code><br>
	<code>You have unmerged paths. </code><br>
	<code>&nbsp;&nbsp;  (fix conflicts and run "git commit") </code><p>
	<code>Unmerged paths: <code> <br>
	<code>&nbsp;&nbsp;  (use "git add <file>..." to mark resolution) </code><p>
	<code>&nbsp;&nbsp;	both modified:   guide.md </code><p>
	<code>no changes added to commit (use "git add" and/or "git commit -a") </code>
    </font></td>
    <td><font size="1">To really check and we may have to do a merge</font></td>
  </tr>
  <tr>
    <td><font size="1">9</font></td>
    <td><font size="1"></font></td>
    <td><font size="1">
      <code>>>>>></code> Head<br>
      <code>=====</code> Seperate them
    </font></td>
    <td><font size="1">You may need to do a merge and open up a file.</font></td>
  </tr>  
</table>


## 11. Resoving conflicts

### 11.1 Just abort a merege

<table>
  <tr>
    <th><font size="1">Step</font></th>	
    <th><font size="1">git</font></th>	
    <th><font size="1">Notes</font></th>	    
  </tr>
  <tr>
    <td><font size="1">1</font></td>
    <td><font size="1"><code>git merge text_edit</code></font></td>
    <td><font size="1">
      If you aim to a merge of <code>text_edit</code> branch, stop it and look at the next step.
    </font></td>        
  </tr>
  <tr>
    <td><font size="1">2</font></td>
    <td><font size="1"><code>git merge --abort</code></font></td>
    <td><font size="1">Abort it instead of merge</font></td>        
  </tr>  
</table>


### 11.2 Resolve conflicts manually and merge

<table>
  <tr>
    <th><font size="1">Step</font></th>	
    <th><font size="1">git</font></th>	
    <th><font size="1">Outcomes</font></th>	
    <th><font size="1">Notes</font></th>	            
  </tr>
  <tr>
    <td><font size="1">1</font></td>
    <td><font size="1"><code>vim readme.md</code></code></font></td>
    <td><font size="1"></font></td>
    <td><font size="1">Go to <code>readme.md</code> where the problem is</font></td>            
  </tr>
  <tr>
    <td><font size="1">2</font></td>
    <td><font size="1"></font></td>
    <td><font size="1"></font></td>
    <td><font size="1">Resolve the issues and remove <code><<<<<</code> and <code>=======</code></font></td>            
  </tr>  
  <tr>
    <td><font size="1">3</font></td>
    <td><font size="1"><code>git add readme.md</code></font></td>
    <td><font size="1"><code></code></font></td>
    <td><font size="1">Add the changes.</font></td>            
  </tr>  
  <tr>
    <td><font size="1">4</font></td>
    <td><font size="1"><code>git status</code></font></td>
    <td><font size="1">
	 <code>On branch master </code> <br>
	 <code>All conflicts fixed but you are still merging. </code><br>
	 <code>&nbsp;&nbsp; (use "git commit" to conclude merge) </code><p>
	<code>Changes to be committed:</code><p>
	<code>&nbsp;&nbsp; 	modified:   hive_installation_guide.md </code>
      </font></td>
    <td><font size="1">It shows it is ready to be commited.</font></td>            
  </tr>  
  <tr>
    <td><font size="1">5</font></td>
    <td><font size="1"><code>git commit</code></font></td>
    <td><font size="1"><code>[master 5c64b50] Merge branch 'test_edit</code></font></td>
    <td><font size="1">Since we are in the middle of a merge, we don't provide a commit message.</font></td>            
  </tr>  
  <tr>
    <td><font size="1">6</font></td>
    <td><font size="1"><code>git status</code></font></td>
    <td><font size="1">
      <code>On branch master</code><br>
      <code>nothing to commit, working directory clean</code>
    </font></td>
    <td><font size="1">Check our status again</font></td>            
  </tr>  
  <tr>
    <td><font size="1">6</font></td>
    <td><font size="1"><code>git log --oneline -4<code></code></font></td>
    <td><font size="1"><code></code></font></td>
    <td><font size="1">Check the log</font></td>            
  </tr>  
  <tr>
    <td><font size="1">7</font></td>
    <td><font size="1"><code>git branch --merged</code></font></td>
    <td><font size="1"><code></code></font></td>
    <td><font size="1">It shows it has been fully merged into master branch</font></td>            
  </tr>  
  
</table>


* The fully specified logging 
* `git log --graph --oneline --all --decorate`



## 12. Merge tools

* `git mergetool --tools=`
* `git mergetool`
