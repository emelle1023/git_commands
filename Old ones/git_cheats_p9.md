# Git CheatSheet (Part 9)

1. Remote `fetch`
2. Remote `merge`
3. Remote `checkout`
4. Pushing to remote (already updated)
5. Remote delete a branch


## 1. Fetch
* After pushing, we'll look into fetching.

<table>
  <tr>
    <th><font size="1">Steps</font></th>	
    <th><font size="1">git</font></th>	    
    <th><font size="1">Outcome</font></th>	    
    <th><font size="1">Notes</font></th>	            
  </tr>
  <tr>
  <tr>
    <td><font size="1">1</font></td>
    <td><font size="1"><code>git log --oneline -5</code></font></td>
    <td><font size="1"><code></code></font></td>
    <td><font size="1">
      Our change is only in local master, but not in remote master. 
      The log doesn't show any change made in <code>origin/master</code> <br>
      In fact, it shows only one branch.
    </font></td>            
  </tr>
  <tr>
    <td><font size="1">2</font></td>
    <td><font size="1"><code>git branch</code></font></td>
    <td><font size="1"><code>* master</code></font></td>
    <td><font size="1">
      It doesn't show <code>origin/master</code> branch except master
    </font></td>            
  </tr>
  <tr>
    <td><font size="1">3</font></td>
    <td><font size="1"><code>git branch -r</code></font></td>
    <td><font size="1">
      <code>origin/HEAD -> origin/master</code><br>
  	 <code>origin/master</code>
    </font></td>
    <td><font size="1">
      Alternatively, you can use <code>git branch</code> and it shows only
      <code>master</code> branch
    </font></td>            
  </tr>
  <tr>
    <td><font size="1">4</font></td>
    <td><font size="1"><code>git fetch origin</code></font></td>
    <td><font size="1"></font></td>
    <td><font size="1">
      Since the respositories aren't in synch, we must <code>fetch</code> in order to get the latest.
    </font></td>            
  </tr>
  <tr>
    <td><font size="1">5</font></td>
    <td><font size="1"><code>git log --oneline -5 origin/master</font></td>
    <td><font size="1"></font></td>
    <td><font size="1"> Just to check if <code>origin/master</code> has the latest. </font></td>            
  </tr>
  <tr>
    <td><font size="1">6</font></td>
    <td><font size="1"><code>git branch -r</font></td>
    <td><font size="1"></font></td>
    <td><font size="1"> 
      Check the branch again in which working directory. <br>
      The remote should have the latest branch. 
    </font></td>            
  </tr>
</table>

* `fetch` just to make sure `origin/master` and remote `master` are in sync.
* `fetch` always before you work.
* `fetch` before you push. 
* `fetch` often. This just makes sure you are in synch with the respository, but your stuffs are still safe.
* `merge` before you commit. So, `merge` is really important and we will look into it.


## 2. Merge 
* `master` pointer at server points at the last commit.
* `origin/master` pointer in local points at the last commit.
* `origin/master` and `master` should always be in sync. To do so, we `fetch`.

<table>
  <tr>
    <th><font size="1">Steps</font></th>	
    <th><font size="1">git</font></th>	    
    <th><font size="1">Notes</font></th>	            
  </tr>
  <tr>
  <tr>
    <td><font size="1">1</font></td>
    <td><font size="1"><code>git branch -a</code></font></td>
    <td><font size="1">
      To check what branches we have. <br> 
      We take <code>master</code> in local and compare it with <code>origin/master</code>
    </font></td>            
  </tr>
  <tr>
    <td><font size="1">2</font></td>
    <td><font size="1"><code>git diff origin/master..master</code></font></td>
    <td><font size="1"> 
      Compare <code>master</code> in your working directory with the latest commit. <br>
      If there are differences, we need merge.
    </font></td>            
  </tr>
  <tr>
    <td><font size="1">3</font></td>
    <td><font size="1"><code>git merge origin/master</code></font></td>
    <td><font size="1"> Merge it. </font></td>            
  </tr>
  <tr>
    <td><font size="1">4</font></td>
    <td><font size="1"><code>git log --oneline -3 master</code></font></td>
    <td><font size="1">To check if local <code>master</code> has the latest merged version.</font></td>            
  </tr>
</table>

* The idea is to o a `fetch`, followed by a `merge`.
* Alternatively, we do `git pull`.
* `git pull` = `git fetch` + `git merge`.


## 3. Remote checkout
* This is to download the entire branch from remote server.

<table>
  <tr>
    <th><font size="1">Steps</font></th>	
    <th><font size="1">git</font></th>	    
    <th><font size="1">Outcome</font></th>	    
    <th><font size="1">Notes</font></th>	            
  </tr>
  <tr>
  <tr>
    <td><font size="1">1</font></td>
    <td><font size="1"><code>git branch -r</code></font></td>
    <td><font size="1">
      <code> origin/HEAD -> origin/master </code><br>
      <code> origin/master </code><br>
      <code> origin/new_feature </code>
    </font></td>
    <td><font size="1">Do a check on all branches, including remote server.</font></td>            
  </tr>
  <tr>
    <td><font size="1">2</font></td>
    <td><font size="1"><code>git branch new_feature HEAD</code></font></td>
    <td><font size="1"></font></td>
    <td><font size="1">
      <code>HEAD</code> just means the tip of the current branch (maybe master). <br>
      You may try to download latest to local <code>master</code>.
    </font></td>            
  </tr>
  <tr>
    <td><font size="1">3</font></td>
    <td><font size="1"><code>git branch new_feature origin/new_feature</code></font></td>
    <td><font size="1"></font></td>
    <td><font size="1">
      You will have a project called <code>new_feature</code>, 
      and it will track <code>origin/new_feature</code> which should be fetched from remote repository.
    </font></td>            
  </tr>
  <tr>
    <td><font size="1">4</font></td>
    <td><font size="1"><code>git branch</code></font></td>
    <td><font size="1"></font></td>
    <td><font size="1">You will see <code>new_feature</code> in your local.</font></td>            
  </tr>
  <tr>
    <td><font size="1">5</font></td>
    <td><font size="1"><code>cat .git/config</code></font></td>
    <td><font size="1">
	 <code>[branch "new_feature"]</code><br>
	 <code>&nbsp;&nbsp; remote = origin </code><br>
	 <code>&nbsp;&nbsp; merge = refs/heads/new_feature </code>
    </font></td>
    <td><font size="1">You will see all these.</font></td>            
  </tr>
  <tr>
    <td><font size="1">6</font></td>
    <td><font size="1"><code></code></font></td>
    <td><font size="1"></font></td>
    <td><font size="1">It tracks <code>new_feature</code> in <code>origin</code>.</font></td>            
  </tr>
  <tr>
    <td><font size="1">7</font></td>
    <td><font size="1"><code></code></font></td>
    <td><font size="1"></font></td>
    <td><font size="1">we can delete that branch.</font></td>            
  </tr>  
  <tr>
    <td><font size="1">8</font></td>
    <td><font size="1"><code>git branch -d non_tracking</code></font></td>
    <td><font size="1"></font></td>
    <td><font size="1">This is in the local.</font></td>            
  </tr> 
  <tr>
    <td><font size="1">9</font></td>
    <td><font size="1"><code>git checkout -b new_feature origin/new_feature</code></font></td>
    <td><font size="1"></font></td>
    <td><font size="1">Do this instead..</font></td>            
  </tr> 
</table>


## 4. Pushing to remote when it's already been updated
* You cannot do a `push` to remote server when some others already pushed their code. Therefore, we take the following 3 steps instead of just `push`.

	<table>
	  <tr>
	    <th><font size="1">Steps</font></th>	
	    <th><font size="1">git</font></th>	        
	    <th><font size="1">Notes</font></th>	            
	  </tr>
	  <tr>
	  <tr>
	    <td><font size="1">1</font></td>
	    <td><font size="1"><code>fetch</code></font></td>
	    <td><font size="1">
	      Make sure <code>origin/master</code> and remote are in sync. <br>
	      We can only commit to local `master`
	    </font></td>            
	  </tr>
	  <tr>
	    <td><font size="1">2</font></td>
	    <td><font size="1"><code>merge</code></font></td>
	    <td><font size="1">
	      We <code>merge</code> not because there are conflicts or when the same line of code is changed. <br>
	      It is because there was a new commit.</font></td>            
	  </tr>
	  <tr>
	    <td><font size="1">3</font></td>
	    <td><font size="1"><code>push</code></font></td>
	    <td><font size="1">Finally <code>push</code> to remote.</font></td>            
	  </tr>
	</table>



## 5. To delete a branch remotely
### Method 1

<table>
  <tr>
    <th><font size="1">Steps</font></th>	
    <th><font size="1">git</font></th>	        
    <th><font size="1">Notes</font></th>	            
  </tr>
  <tr>
  <tr>
    <td><font size="1">1</font></td>
    <td><font size="1"><code>git branch -a</code></font></td>
    <td><font size="1">Check what branches we have. </font></td>            
  </tr>
  <tr>
    <td><font size="1">2</font></td>
    <td><font size="1"><code>git push origin :new_feature</code></font></td>
    <td><font size="1">Push whatever we have. </font></td>            
  </tr>
  <tr>
    <td><font size="1">3</font></td>
    <td><font size="1"><code>git branch -r</code></font></td>
    <td><font size="1">Check the remote branch.</font></td>            
  </tr>  
  <tr>
    <td><font size="1">4</font></td>
    <td><font size="1"><code>git branch</code></font></td>
    <td><font size="1">But it is still here at the local branch.</font></td>            
  </tr>  
  <tr>
    <td><font size="1">5</font></td>
    <td><font size="1"><code>git push origin new_feature:new_feature</code></font></td>
    <td><font size="1">To push a new branch.</font></td>            
  </tr>   
  <tr>
    <td><font size="1">6</font></td>
    <td><font size="1"><code>git push origin :new_feature</code></font></td>
    <td><font size="1">To delete, it is like to push nothing.</font></td>            
  </tr>     
</table>

### Method 2

<table>
  <tr>
    <th><font size="1">Steps</font></th>	
    <th><font size="1">git</font></th>	    
    <th><font size="1">Outcome</font></th>	    
    <th><font size="1">Notes</font></th>	            
  </tr>
  <tr>
  <tr>
    <td><font size="1">1</font></td>
    <td><font size="1"><code>git push origin new_feature</code></font></td>
    <td><font size="1"><code></code></font></td>
    <td><font size="1">We don't need the colon.</font></td>            
  </tr>
  <tr>
    <td><font size="1">2</font></td>
    <td><font size="1"><code>git push origin --delete new_feature</code></font></td>
    <td><font size="1"><code></code></font></td>
    <td><font size="1">To push nothing to remote.</font></td>            
  </tr>
  <tr>
    <td><font size="1">3</font></td>
    <td><font size="1"><code>git branch -r</code></font></td>
    <td><font size="1"><code></code></font></td>
    <td><font size="1">To check, it is gone.</font></td>            
  </tr>  
</table>

