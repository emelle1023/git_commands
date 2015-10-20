# Git CheatSheet (Part 5)

1. Undo Changes

## 1. Undo changes

### 1.1. Working directory
* Just when we accidently delete a file `index.html` in the **working directory**, you should always do the following

<table>
  <tbody>
    <tr>
      <th>git</th>
      <th>Notes</th>
    </tr>
    <tr>
      <td><code>git status</code</td>
      <td>Run it and tells us what were changed</td>
    </tr>
    <tr>
      <td><code>git diff</code></td>
      <td>Tells us what the changes are</td>
    </tr>
    <tr>
      <td><code>git checkout index.html</code></td>
      <td>
        To go back to the previous version and replace the current corrupted one. <br> 
        <code>checkout</code> can replace the entire branch as well. Dangerous
      </td>
    </tr>
    <tr>
      <td><code>git checkout --index.html</code></td>
      <td>
        This will only replace one file in the current branch
      </td>
    </tr> 
    <tr>
      <td><code>git status</code></td>
      <td>To confirm</td>
    </tr>       
  </tbody>
</table>


### 1.2. Staging
* Supposed we added a corrupted file `git_tutorial.md` in the **staging index** by `git add git_tutorial.md` 
* However, you still want the changes in your **working directory**, except we don't want them to be committed.

<table>
  <tbody>
    <tr>
      <th>git</th>
      <th>Output</th>
      <th>Notes</th>
    </tr>
    <tr>
      <td><font size="1"><code>git add git_tutorial.md</code></font></td>
      <td></td>
      <td>
        You didn't mean to add the file to staging,
        but you still want to keep them in the <b>working drectory</b>
    </td>
    </tr>
    <tr>
      <td><font size="1"><code>git status</code></font></td>
      <td>
        <font size="1"><code>On branch master</code></font></br>
        <font size="1"><code>Changes to be committed:</code></font></br>
        <font size="1"><code>&nbsp;&nbsp;&nbsp;(use "git reset HEAD <file>..." to unstage)</code></font></p>
        <font size="1"><code>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;modified:   git_tutorial.md</code></font>
      </td>
      <td>Tells us what the changes are in <b>staging</b></td>
    </tr>
    <tr>
      <td><font size="1"><code>git reset HEAD git_tutorial.md</code></font></td>
      <td>
        <font size="1"><code>Unstaged changes after reset:</code></font></br>
        <font size="1"><code>M	git_tutorial.md</code></font>   
      </td>
      <td>
        Go to the last commit (<b>repository</b>), where the HEAD is pointing at and bring in
        <code>git_tutorial.md</code>
      </td>
    </tr>
    <tr>
      <td><font size="1"><code>git status</code></font></td>
      <td>
        <font size="1"><code>On branch master</code></font></br>
        <font size="1"><code>Changes not staged for commit:</code></font></br>
          <font size="1">
            <code>
               &nbsp;&nbsp;&nbsp;
               (use "git add <file>..." to update what will be committed)
            </code>
          </font></br>
          <font size="1">
            <code>
              &nbsp;&nbsp;&nbsp;
              (use "git checkout -- <file>..." to discard changes in working directory)</code>
          </font></p>
	     <font size="1"><code>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;modified:   git_tutorial.md</code></font>      
      </td>
      <td>To confirm</td>
    </tr>       
  </tbody>
</table>




### 1.3. Repository
* To undo what has already been commited to Repository.

#### 2.3.1. Undo commit
##### Method 1 `amend`
* Replace the last commit. We can only change the last commit, because nothing else depends on it.

	<table>
	  <tbody>
	    <tr>
	      <th>git</th>
	      <th>Functions</th>
	    </tr>
	    <tr>
	      <td><font size="1"><code>git commit --amend -m "Undo last commit"</code></font></td>
	      <td>All `commit --amend` do is to replace the last commit. </br>You are not removing the last commit, just replace it.</td>
	    </tr>
	  </tbody>
	</table>


##### Method 2
* Checkout the version of files we want and then commit.

	<table>
	  <tbody>
	    <tr>
	      <th>git</th>
	      <th>Functions</th>
	    </tr>
	    <tr>
	      <td><font size="1"><code>git checkout fb483ds30 --readme.md</code></font></td>
	      <td>
	      Checkout the version you like. </br>
	      You will now have this version of <code>readme.md</code> in your <b>working directory</b></td>
	    </tr>
	    <tr>
	      <td><font size="1"><code>git commit -m "use this readme.md version instead"</code></font></td>
	      <td>Now you can commit</td>
	    </tr>
	  </tbody>
	</table>


##### Method 3 `revert`
* Known to be the best approach. It reverts back right before the commit.

	<table>
	  <tbody>
	    <tr>
	      <th>git</th>
	      <th>Output</th>
	      <th>Functions</th>
	    </tr>
	    <tr>
	      <td><font size="1"><code>git revert def4b17a...</code></font></td>
	      <td>
	          <font size="1"><code>Revert "trying"</code></font></br>
               <font size="1"><code>    This reverts commit cd9329e...</code></font>
	      </td>
	      <td>
	        Find the version. </br>
	        This brings to your <b>working directory</b> as well as to commit the changes all into resposiotry in one step. </br>
	        You are replacing everything in that version to its previous state. </br>
	        You have gone back to its previous committed state, which is still there.
	      </td>
	    </tr>
	  </tbody>
	</table>


#### 2.3.2. Undo multiple commits `reset`
* This will move the **HEAD** pointer and will overwrite all the rest of the commit
* 3 parameters
	* ***soft*** - doesn't change staging and working at the same time, safest.
	* ***mixed*** - change staging as well, but not with working directory
	* ***hard*** -- change everything, whatever it is.
* ***Soft*** reset steps

	<table>
	  <tbody>
	    <tr>
	      <th>git</th>
	      <th>Functions</th>
	    </tr>
	    <tr>
	      <td>
	        <font size="1">
	          <code>cat .git/HEAD</code></br>
	          <code>cat .git/refs/heads</code>
	        </font>
	      </td>
	      <td>Take a look at the <b>HEAD</b> poniter.</td>
	    </tr>
	    <tr>
	      <td><font size="1"><code>git reset --soft e0c2fd6b...</code></font></td>
	      <td>Take you back to the last stable version, 
	      but nothing else in your working or staging is changed. 
	      This can be different for hard and mixed.
	      </td>
	    </tr>
	    <tr>
	      <td><font size="1"><code>git reset --soft 065e974...</code></font></td>
	      <td>Change the <b>HEAD</b> pointer if you want.
	      </td>
	    </tr>
	  </tbody>
	</table>

* Afterwards, you can do another commit
* you can do **mixed** and **hard** reset.

### 1.5. Remove untracked files from working directory


<table>
  <tbody>
    <tr>
      <th>git</th>
      <th>Output</th>
      <th>Functions</th>
    </tr>
    <tr>
      <td><font size="1"><code>git status</code></font></td>
      <td>
          <font size="1"><code>Untracked files:</code></font></br>
          <font size="1"><code>&nbsp;&nbsp;(use "git add <file>..." to include in what will be committed)</code></font></p>
          <font size="1"><code>&nbsp;&nbsp;&nbsp;	junk.md</code></font>
      </td>
      <td>You can see <code>junk.md</code> is the untracked file.</td>
    </tr>
    <tr>
      <td><font size="1"><code>git clean</code></font></td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>
        <font size="1">
          <code>git clean -n</code>
        </font>
      </td>
      <td><font size="1"><code>Removing junk.md</code></font></td>
      <td></td>
    </tr>    
    <tr>
      <td>
        <font size="1">
          <code>git clean -f</code>
        </font>
      </td>
      <td>
          <font size="1"><code>Would remove junk.md</code></font>
      </td>
      <td>Removes it physiclaly, so same as <code>rm</code></br>
      If it is already in the staging directory, it won't be removed.
      </td>
   </tr>   
    <tr>
      <td>
        <font size="1">
          <code>git reset HEAD junk.md</code>
        </font>
      </td>
      <td></td>
      <td>
         This is to undo all the add <code>junk.md</code></br>
	    Everything is permantly deleted
      </td>
   </tr>   
  </tbody>
</table>





