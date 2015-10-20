# Git CheatSheet (Part 4)

1. Renaming

## 1. Renaming

### 1.1. Method 1 - Physical Rename file

* Given the file `git_tutorial.md` have already been add and committed to respository.

<table>
  <tbody>
    <tr>
      <th>git</th>
      <th>Outcome</th>
      <th>Notes</th>
    </tr>
    <tr>
      <td></td>
      <td></td>
      <td>
        <font size="1">Physically rename <code>git_tutorial.md</code> to <code>git_tutorial_1.md</code></font>
      </td>
    </tr>
    <tr>
      <td align="left">
        <font size="1"><code>git status</code></font>
      </td>
      <td>
	   <font size="1"><code>On branch master</code></font><br>
	   <font size="1"><code>Changes not staged for commit:</code></font></br>
	   <font size="1"><code>(use "git add/rm <file>..." to update what will be committed)</code></font></br>
	   <font size="1><code>(use "git checkout -- <file>..." to discard changes in working directory)</code></font></br>
       <font size="1"><code>deleted:    git_tutorial.md</code></font></br>
	  <font size="1"><code>Untracked files:</code></font></br>
	  <font size="1"><code>(use "git add <file>..." to include in what will be committed)</code></font></br>
	  <font size="1"><code>	git_tutorial_1.md</code></font>
      </td>
      <td><font size="1">It says a file is removed and a new file is created and untracked</font></td>
    </tr>
    <tr>
      <td><font size="1"><code>git add git_tutorial_1.md</code></font></td>
      <td></td>  
      <td><font size="1">Add the new file. </br> Based on <code>git status</code></font></td>            
    </tr>
    <tr>
      <td><font size="1"><code>git rm git_tutorial.md</code></font></td>
      <td></td>    
      <td><font size="1">Remove the <b>old</b> file</font></td>
    </tr>
     <tr>
      <td><font size="1"><code>git status</code></font></td>
      <td>
        <font size="1"><code>On branch master</code></font></br>
	   <font size="1"><code>Changes to be committed:</code></font></br>
	   <font size="1"><code>(use "git reset HEAD <file>..." to unstage)</code></font></br>
		<font size="1"><code>renamed:    git_tutorial.md -> git_tutorial_1.md</code></font></br>   
      </td>
      <td><font size="1"Double check</font></td>
    </tr>

  </tbody>
</table>

* You will likely need to `commit` after this.



### 1.2. Method 2 - Use git to rename the file



<table>
  <tbody>
    <tr>
      <th>git</th>
      <th>Outcome</th>
      <th>Notes</th>
    </tr>
    <tr>
      <td><font size="1"><code>git mv git_tutorial_1.md git_tutorial.md</code></font></td>
      <td></td>
      <td>
        <font size="1">No need to rename files, </br> just use mv</font>
      </td>
    </tr>
    <tr>
      <td align="left">
        <font size="1"><code>git status</code></font>
      </td>
      <td>
	   <font size="1"><code>On branch master</code></font><br>
	   <font size="1"><code>Changes to be committed:</code></font></br>
	   <font size="1"><code>&nbsp;&nbsp;&nbsp;(use "git reset HEAD <file>..." to unstage)</code></font></p>
	   <font size="1"><code>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;renamed:    git_tutorial.md -> git_tutorial_1.md</code></font>
     </td>
      <td><font size="1">It shows what has been renamed and ready to commit</font></td>
    </tr>
    <tr>
      <td><font size="1"><code>git mv git_tutorial.md git/git_tutorial.md</code></font></td>
      <td></td>  
      <td><font size="1">Instead of renaming a file, can physically create a folder</font></td>            
    </tr>
    <tr>
      <td><font size="1"><code>git status</code></font></td>
      <td>
        <font size="1"><code>On branch master</code></font><br>
        <font size="1"><code>Changes to be committed:</code></font></br>
        <font size="1"><code>&nbsp;&nbsp;&nbsp;(use "git reset HEAD <file>..." to unstage)</code></font></p>
        <font size="1"><code>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;renamed:    git_tutorial.md -> git/git_tutorial.md</code></font></br>      
      </td>    
      <td><font size="1">Remove the <b>old</b> file</font></td>
    </tr>
     <tr>
      <td><font size="1"><code>git status</code></font></td>
      <td>
        <font size="1"><code>On branch master</code></font></br>
	   <font size="1"><code>Changes to be committed:</code></font></br>
	   <font size="1"><code>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;(use "git reset HEAD <file>..." to unstage)</code></font></p>
		<font size="1"><code>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;renamed:    git_tutorial.md -> git_tutorial_1.md</code></font></br>   
      </td>
      <td><font size="1"Double check</font></td>
    </tr>

  </tbody>
</table>


* `mv` won't require us to perform an `add`, but still need to do `commit`
* `git commit -m "Reorganisesd file structure"`

