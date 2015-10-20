# Git CheatSheet (Part 8)

1. Pushing to remote
2. Check existing branches
3. To clone an existing project
4. To push and track untracked branches (Unnecessary)
5. Remote pushing


## 1. Pushing to remote

<table>
  <tr>
    <th><font size="1">git</font></th>	    
    <th><font size="1">Notes</font></th>	            
  </tr>
  <tr>
  <tr>
    <td><font size="1"><code>git push -u origin master</code></font></td>
    <td><font size="1">To push the whole branch to remote server</font></td>            
  </tr>
</table>

## 2. Check existing branches
<table> 
  <tr>
    <th><font size="1">Commands</font></th>	    
    <th><font size="1">Outcomes</font></th>	    
    <th><font size="1">Notes</font></th>	            
  </tr> 
  <tr>
    <td><font size="1"><code>cat .git/config</code></font></td>
    <td><font size="1">
      <code>[core]</code><br>
	 <code>&nbsp;&nbsp; repositoryformatversion = 0 </code><br>
	 <code>&nbsp;&nbsp; filemode = true </code><br>
	 <code>&nbsp;&nbsp; bare = false </code><br>
	 <code>&nbsp;&nbsp; logallrefupdates = true </code><br>
	 <code>&nbsp;&nbsp; ignorecase = true </code><br>
	 <code>&nbsp;&nbsp; precomposeunicode = true </code><br>
	 <code> [branch "master"] </code><br>
	 <code> [remote "origin"] </code><br>
	 <code>&nbsp;&nbsp; url = https://github.com/emelle/mink.git </code><br>
	 <code>&nbsp;&nbsp; fetch = +refs/heads/*:refs/remotes/origin/* </code><br>
	 <code> [branch "master"] </code><br>
	 <code>&nbsp;&nbsp; remote = origin </code><br>
	 <code>&nbsp;&nbsp; merge = refs/heads/master </code>
    </font></td>
    <td><font size="1">
      To check master, origin etc. <br>
      The remote server has the branch named <code>origin</code>
      </font></td>            
  </tr>  
  <tr>
    <td><font size="1"><code>ls -la .git/refs/remotes</code></font></td>
    <td><font size="1">
      <code> total 0 </code><br>
	 <code> drwxr-xr-x  3 el  staff  102 23 Jun 13:14 . </code><br>
	 <code> drwxr-xr-x  5 el  staff  170 23 Jun 13:14 .. </code><br>
	 <code> drwxr-xr-x  3 el  staff  102 23 Jun 13:28 origin </code>
    </font></td>
    <td><font size="1">You can also check the remtoe branch with this</font></td>            
  </tr>
  <tr>
    <td><font size="1"><code>cat .git/refs/remotes/origin/master</code></font></td>
    <td><font size="1"><code> 21474396d111e1cbdaf7409a75e33025362d129d </code><br></font></td>
    <td><font size="1">You can check the SHA here</font></td>            
  </tr>
  <tr>
    <td><font size="1"><code> git branch </code></font></td>
    <td><font size="1"><code></code></font></td>
    <td><font size="1">Check local branches</font></td>            
  </tr>  
  <tr>
    <td><font size="1"><code>git branch -r</code></font></td>
    <td><font size="1"><code></code></font></td>
    <td><font size="1">Check remote branches</font></td>            
  </tr>  
  <tr>
    <td><font size="1"><code>git branch -a</code></font></td>
    <td><font size="1"><code></code></font></td>
    <td><font size="1">Check both remote and local branches</font></td>            
  </tr>  
</table>


## 3. To clone an existing project
* To clone an existing project from Remote to local.
* Assuming we have no project and copy one from Remote directly to local.

<table>
  <tr>
    <th><font size="1">git</font></th>	    
    <th><font size="1">Notes</font></th>	            
  </tr>
  <tr>
  <tr>
    <td><font size="1"><code>git clone https://github.com/emelle1023/mink.git</code></font></td>
    <td><font size="1">
      To copy it directly from remote to local. It will create a directory called <code>mink</code>.
    </font></td>            
  </tr>
  <tr>
    <td><font size="1"><code>git clone https://github.com/emelle1023/mink.git <i>another_name</i></code></font></td>
    <td><font size="1">
      To copy directly from remote and have a directly to your liking <i><code>another_name</code></i>.
    </font></td>            
  </tr>
  <tr>
    <td><font size="1"><code>git branch</code></font></td>
    <td><font size="1">It should have only one branch as we haven't added another branch yet.</font></td>            
  </tr>
</table>


## 4. To push tracking/non-tracking branch

<table>
  <tr>
    <th><font size="1">Steps</font></th>	
    <th><font size="1">git</font></th>	     
    <th><font size="1">Notes</font></th>	            
  </tr>
  <tr>
  <tr>
    <td><font size="1">1</font></td>
    <td><font size="1"><code>cat.git/config</code></font></td>
    <td><font size="1">To check branches and <code>HEAD</code> etc.</font></td>            
  </tr>
  <tr>
    <td><font size="1">2</font></td>
    <td><font size="1"><code>git branch non_tracking</code></font></td>
    <td><font size="1">Start to track a branch.</font></td>            
  </tr>
  <tr>
    <td><font size="1">3</font></td>
    <td><font size="1"><code>git push origin non_tracking</code></font></td>
    <td><font size="1">To push another new branch into remote.</font></td>            
  </tr>
  <tr>
    <td><font size="1">4</font></td>
    <td><font size="1"><code>cat .git/config</code></font></td>
    <td><font size="1">To check listing and there is no connection to the future of the track.</font></td>            
  </tr>
  <tr>
    <td><font size="1">5</font></td>
    <td><font size="1"><code>-u</code></font></td>
    <td><font size="1">To create tracking.</font></td>            
  </tr>
  <tr>
    <td><font size="1">6</font></td>
    <td><font size="1">
      <code>git config branch.non_tracking.remote origin</code><br>
      <code>git config branch.non_tracking.merge refs/heads/master</code><br>
      <code>git branch --set-upstream non_tracking origin/non_tracking</code>
    </font></td>
    <td><font size="1">
      To make tracking. <br>
      To make tracking, and to also give you the same configuration. <br>
      To make tracking, and to also tell you the remote server is.
    </font></td>            
  </tr>
</table>



## 5. Remote pushing 
<table>
  <tr>
    <th><font size="1">git</font></th>	    
    <th><font size="1">Notes</font></th>	            
  </tr>
  <tr>
  <tr>
    <td><font size="1"><code> git commmit -am "another change" </code></font></td>
    <td><font size="1">Make some chagnes in master local and commit it</font></td>            
  </tr>
  <tr>
    <td><font size="1"><code> git log --oneline origin/master </code></font></td>
    <td><font size="1">
      Check the log and expect the latest change is in remote. However, it doesn't have the latest change.
    </font></td>            
  </tr>
  <tr>
    <td><font size="1"><code> git diff origin/master..master </code></font></td>
    <td><font size="1">
      To compare our local master to origin/master.
    </font></td>            
  </tr>
  <tr>
    <td><font size="1">
      <code> git push origin master </code> <br>
      <code> git push </code>
    </font></td>
    <td><font size="1"> 
     To push our change to <code>origin/master</code>. <br>
     Since it is a tracking branch (check <code>config</code>), we can simply do <code>git push</code>
   </font></td>            
  </tr>
</table>




