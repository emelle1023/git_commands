# Git CheatSheet (Part 3)

1. Git Workflow
2. Meaning of `git status`
3. Meaning of `git diff`


## 1. Git workflow
* The steps we should take in a git workflow. It includes
	* Knowing where the last commit is (**HEAD Pointer**)
	* Knowing what steps to take when making changes on a file


### 1.1. Git HEAD pointer
* **HEAD** points at the last commit
* To check where **HEAD** is pointing, we try the following

	| git                             | Outcome                     | Notes                                      |  
	|:------------------------------- |:--------------------------- | :----------------------------------------- | 
	| `cat ~/.git/HEAD`               |  `ref: refs/heads/master`   | Shows that pointer points at master branch | 
	| `cat ~/.git/refs/heads/master`  |  `43c01ad50f3d2269c38...`   | Shows which SHA the HEAD is on             | 
	| `git log HEAD`                  | -                           | Shows the tip of the current brunch        |

			
### 1.2. Make changes to Files

* Follow them in this order, it is a workflow




<table>
  <tbody>
    <tr>
      <th align="center">Git</th>
      <th align="center">outcome</th>
      <th align="center">Notes</th>
    </tr>
    <tr>
    	<td>
    	   <font size="2"><code>git status</code>
    	   </font>
    	</td>
    	<td>
    	<font size="1">
      	<code>On branch master</code> <br>
		<code>nothing to commit, working directory clean</code> 
		</code>
	</font>	    	
    </td>
    	<td>
    	  Always do <code>git status</code> to see the status of the files. <br>
    	  This says we are on the Master branch and we have the latest code, nothing to commit.
    	</td> 
	</tr>
    <tr>
    	<td>
    	   <font size="2"><code>git status</code>
    	   </font>
    	</td>
    	<td>
    	<font size="1">
      	<code>On branch master</code> <br>
		<code>Untracked files:</code> <br>
		<code>&nbsp;&nbsp;(use "git add (file)..." to include in what will be committed)</code> <p>
		<code>&nbsp;&nbsp;&nbsp;&nbsp; readme.md</code> <p>
		<code>nothing added to commit but untracked files present (use "git add" to track)</code>
	</font>	
    	</td>
    	<td>Create a new file. <br>
    	  This means we are on master branch. a file is untracked, we need to add it.
    	</td> 
	</tr>
    <tr>
    	<td>
    	<font size="2">
    	  <code>git add readme.md</code> <br>
    	  <code>git add readme.md 2nd.md</code> <br>
    	  <code>git add .</code>
    	</font>  
    	</td>
    	<td></td>
    	<td>Add multiple or all files for tracking</td> 
	</tr>
    <tr>
    	<td>
    	<font size="2">
    	  <code>git status</code>
    	</font>  
    	</td>
    	<td>
    	<font size="1">
      	<code>On branch master</code> <br>
		<code>Changes to be committed:</code> <br>
		<code>&nbsp;&nbsp;&nbsp;(use "git reset HEAD <file>..." to unstage)</code> <p>
		<code>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;new file:&nbsp;&nbsp;&nbsp;git_tutorial.md</code>
	</font>	
    	</td>
    	<td>Even after all, check status again</td> 
	</tr>	
  </tbody>
</table>



## 2. Meaning of `git status`

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

* The above means `hive_installation_guide.md` has not been added at all to **staging**.
* `git_tutorial.md` has recently been added and committed. Yet it is not staged, as it has just been edited in the **working directory**.
* <font color="red"><code>**modified**:</code></font> means it is in **staging**, but not yet in **respository**, we'll need to commit it.
* <font color="red"><code>**Untracked**:</code></font> means it is in **working directory**, not even added to **staging** yet.


## 3. Meaning of `git diff`

* `git diff` compares **staging** and **working directory**
	* <font color="red">`red`</font> = -removed
	* <font color="green">`green`</font> = +added
* It only shows a bit of the change but the whole line.
* <code>@@ <font color="red">-1</font>,4 <font color="green">+1</font>,3 @@</code>
	* tells us line one and the next 4 lines are removed and 
	* replaced by line 1 and next 3 lines from the new file.


### 3.1. Typical `diff`

<table>
 <tbody>
   <tr>
     <th>git</th>
     <th>Notes</th>
   </tr>   
   <tr>
     <td><code>git diff git_tutorial.md</code></td>
     <td>
       Compare staging and working directory. <br>
       Based on the outcome of <code>git status</code>
     </td>
   </tr>   
   <tr>
     <td><code>git diff</code></td>
     <td>comparing working and staging of all modified files, <br> 
     as soon as it is added, there won't be a difference</td>
   </tr>   
   <tr>
     <td><code>git diff --staged</code></td>
     <td>comparing staging and respository, what has been staged and what has been committed.</td>
   </tr>   
 </tbody>
</table>


