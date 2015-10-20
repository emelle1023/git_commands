# Git CheatSheet (Part 7)

1. Stash (Unnecessary)
2. Remotes

## 1. Stash (Unnecessary)


## 2. Remotes
* This is for version control. 
* The typical functions are
	* `add`
	* `commit`
	* `push` 
		* master from remote server points to last commit 
		* master points to last commit in local computer
		* origin/master points to last commit in local computer
	* `fetch`
	* `merge`


### 2.1. Global setup on local machine

* To setup git to connect local machine to remote server. Only do this once.
* `git config --global user.name "Matthew Lai"`
* `git config --global user.email`

### 2.2. Remote server project connection
* Connect a project and have it linked to the remote server.
* Only do this once

<table>
  <tr>
    <th><font size="1">Steps</font></th>	
    <th><font size="1">commands</font></th>	    
    <th><font size="1">Outcome</font></th>	    
    <th><font size="1">Notes</font></th>	            
  </tr>
  <tr>
  <tr>
    <td><font size="1">1</font></td>
    <td><font size="1"><code> echo "# mink" >> readme.md </code></font></td>
    <td><font size="1"><code></code></font></td>
    <td><font size="1"> Just to see what is in readme.md file </font></td>            
  </tr>
  <tr>
    <td><font size="1">2</font></td>
    <td><font size="1"><code>mkdir mink</code></font></td>
    <td><font size="1"><code></code></font></td>
    <td><font size="1">Create a directory for the mink project</font></td>            
  </tr>
  <tr>
    <td><font size="1">3</font></td>
    <td><font size="1">
      <code>cd minnk</code><br>
      <code>git init</code>      
    </font></td>
    <td><font size="1"><code></code></font></td>
    <td><font size="1">Initialising the project. This is the procedure.</font></td>            
  </tr>
  <tr>
    <td><font size="1">4</font></td>
    <td><font size="1"><code>touch first_file</code></font></td>
    <td><font size="1"><code></code></font></td>
    <td><font size="1">Create a file</font></td>            
  </tr>
  <tr>
    <td><font size="1">5</font></td>
    <td><font size="1"><code>git add first_file</code></font></td>
    <td><font size="1"><code></code></font></td>
    <td><font size="1">Add the first</font></td>            
  </tr>
  <tr>
    <td><font size="1">6</font></td>
    <td><font size="1"><code>git commit -m 'first commit'</code></font></td>
    <td><font size="1"><code></code></font></td>
    <td><font size="1">Commit the file</font></td>            
  </tr>
  <tr>
    <td><font size="1">7</font></td>
    <td><font size="1"><code>git remote add origin https://github.com/emelle/mink.git</code></font></td>
    <td><font size="1"><code></code></font></td>
    <td><font size="1">Add to remote server</font></td>            
  </tr>
  <tr>
    <td><font size="1">8</font></td>
    <td><font size="1"><code>git push -u origin master</code></font></td>
    <td><font size="1"><code></code></font></td>
    <td><font size="1">
      You push it to orgin mater.<br>
      This is another layer.
    </font></td>            
  </tr>

</table>

### 2.3. Check remote URL

<table>
  <tr>
    <th><font size="1">commands</font></th>	    
    <th><font size="1">Outcome</font></th>	    
    <th><font size="1">Notes</font></th>	            
  </tr>
  <tr>
  <tr>
    <td><font size="1">
      <code>git remote</code><br>
      <code>git remote -v</code>
    </font></td>
    <td><font size="1"><code></code></font></td>
    <td><font size="1">
      Check URL for fetching and pushing using <code>git</code>
    </font></td>            
  </tr>
  <tr>
    <td><font size="1"><code>cat .git/config</code></font></td>
    <td><font size="1">
	  <code>[remote "origin"]</code><br>
	  <code>&nbsp;&nbsp; url = https://github.com/emelle1023/mink.git</code><br>
	  <code>&nbsp;&nbsp; fetch = +refs/heads/*:refs/remotes/origin/*</code><br>
    </font></td>
    <td><font size="1">Check URL using commands</font></td>            
  </tr>
</table>


### 2.4. Remove Remote 

<table>
  <tr>
    <th><font size="1">commands</font></th>	    
    <th><font size="1">Outcome</font></th>	    
    <th><font size="1">Notes</font></th>	            
  </tr>
  <tr>
  <tr>
    <td><font size="1"><code>git remote rm origin</code></font></td>
    <td><font size="1"><code></code></font></td>
    <td><font size="1">
      Check URL for fetching and pushing using <code>git</code>
    </font></td>            
  </tr>
  <tr>
    <td><font size="1"><code>cat .git/config</code></font></td>
    <td><font size="1">
	  <code>[core]</code><br>
	  <code>&nbsp;&nbsp; repositoryformatversion = 0</code><br>
	  <code>&nbsp;&nbsp; filemode = true</code><br>
    </font></td>
    <td><font size="1">Check URL using commands</font></td>            
  </tr>
</table>

### 2.5. To add back Remote

<table>
  <tr>
    <th><font size="1">commands</font></th>	    
    <th><font size="1">Outcome</font></th>	    
    <th><font size="1">Notes</font></th>	            
  </tr>
  <tr>
  <tr>
    <td><font size="1"><code>git remote add origin https://github.com/emelle/mink.git</code></font></td>
    <td><font size="1"><code></code></font></td>
    <td><font size="1">To add it back to remote</font></td>            
  </tr>
  <tr>
    <td><font size="1"><code>git remote</code></font></td>
    <td><font size="1"><code>origin</code></font></td>
    <td><font size="1">Double check</font></td>            
  </tr>
</table>

### 2.6. Existing Git repo
* To check for existing repo

	<table>
	  <tr>
	    <th><font size="1">commands</font></th>	    
	    <th><font size="1">Notes</font></th>	            
	  </tr>
	  <tr>
	  <tr>
	    <td><font size="1"><code>cd mink repo</code></font></td>
	    <td><font size="1">Check what is in the repo</font></td>            
	  </tr>
	  <tr>
	    <td><font size="1"><code>git remote add origin https://github.com/emelle1023/mink.git</code></font></td>
	    <td><font size="1">Bring in to remote</font></td>            
	  </tr>
	  <tr>
	    <td><font size="1"><code>git push -u origin master</code></font></td>
	    <td><font size="1">Always do <code>push</code></font></td>            
	  </tr>
	</table>


### 2.7. Importing a subversion Repo

### 2.8. The general steps 

<table>
  <tr>
    <th><font size="1">Steps</font></th>	
    <th><font size="1">git</font></th>	      
    <th><font size="1">Notes</font></th>	            
  </tr>
  <tr>
  <tr>
    <td><font size="1">1</font></td>
    <td><font size="1"><code>git remote</code></font></td>
    <td><font size="1">Just to check</font></td>            
  </tr>
  <tr>
    <td><font size="1">2</font></td>
    <td><font size="1">
      <code>git remote add <alias> <url></code><br>
      <code>git remote add origin https:///code>      
    </font></td>
    <td><font size="1">Remotely add</font></td>            
  </tr>
  <tr>
    <td><font size="1">3</font></td>
    <td><font size="1"><code>cat .git/config</code></font></td>
    <td><font size="1">To find info on the Remote</font></td>            
  </tr>
  <tr>
    <td><font size="1">4</font></td>
    <td><font size="1"><code>git remote rm origin</code></font></td>
    <td><font size="1">To remove the remote</font></td>            
  </tr>

</table>

* we have only connected to remote, we haven't `added` or `committed` yet.

