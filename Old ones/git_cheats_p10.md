# Git CheatSheet (Part 10)

1. GitHub admin
2. Work flow


## 1. GitHub admin
* Collaborators and to add users to the project.
* To grant users write access, check if someone is working on the project (issues).
* To `fork` of the project, no longer part of the original one, this way you will have access to.
* The issue is what you will be doing so others won't look at it. should always do that.
* `fork`, so you can `commit` changes to your local respository. when you are ready to commit to remote respository, issues a `pull` request.



## 2. Work flow

<table>
  <tr>
    <th><font size="1">Steps</font></th>	
    <th><font size="1">git</font></th>	    
    <th><font size="1">Notes</font></th>	            
  </tr>
  <tr>
  <tr>
    <td><font size="1">1</font></td>
    <td><font size="1"><code>git checkout master</code></font></td>
    <td><font size="1">Get everything from local <code>master</code></font></td>            
  </tr>
  <tr>
    <td><font size="1">2</font></td>
    <td><font size="1"><code>git fetch</code></font></td>
    <td><font size="1">
      Make sure local <code>master</code> and remote respository are in sync. <br>
      So tracking <code>origin/master</code> is the one to check.
    </font></td>            
  </tr>
  <tr>
    <td><font size="1">3</font></td>
    <td><font size="1"><code>git merge origin/master</code></font></td>
    <td><font size="1">
      To merge changes from remote which is in <code>origin/master</code> to lcoal <code>master</code.>
    </font></td>            
  </tr>
  <tr>
    <td><font size="1">4</font></td>
    <td><font size="1"><code>git checkout -b feeback_form</code></font></td>
    <td><font size="1">This is to checkout a new branch.</font></td>            
  </tr>
  <tr>
    <td><font size="1">5</font></td>
    <td><font size="1"><code>git add feedback.html</code></font></td>
    <td><font size="1">When you new page is done, add it.</font></td>            
  </tr>
  <tr>
    <td><font size="1">6</font></td>
    <td><font size="1"><code>git commit -m "Add customer feedback form</code></font></td>
    <td><font size="1">To commit to your local respository.</font></td>            
  </tr>
  <tr>
    <td><font size="1">7</font></td>
    <td><font size="1"><code>git fetch</code></font></td>
    <td><font size="1">To keep your work in sync</font></td>            
  </tr>
  <tr>
    <td><font size="1">8</font></td>
    <td><font size="1"><code>git push -u origin feedback_form</code></font></td>
    <td><font size="1">
      You want to know if there were any issues to conflict your working directory, <br>
      if not, <code>push</code> your branch to remote. 
      <code>-u</code> making it as a tracking branch. <br>
      Now all your coworkers can see it.
    </font></td>            
  </tr>
  <tr>
    <td><font size="1">9</font></td>
    <td><font size="1"><code></code></font></td>
    <td><font size="1">Send an email to others. please take a look and let me think</font></td>            
  </tr>
  <tr>
    <td><font size="1">10</font></td>
    <td><font size="1"><code></code></font></td>
    <td><font size="1">Your coworkers will</font></td>            
  </tr>
  <tr>
    <td><font size="1">11</font></td>
    <td><font size="1"><code>git checkout msater</code></font></td>
    <td><font size="1"></font></td>            
  </tr>
  <tr>
    <td><font size="1">12</font></td>
    <td><font size="1"><code>git fetch</code></font></td>
    <td><font size="1">Until she does a <code>fetch</code>, she can't see the new branch, it is not sync up.</font></td>            
  </tr>
  <tr>
    <td><font size="1">13</font></td>
    <td><font size="1"><code>git merge origin/master</code></font></td>
    <td><font size="1">Merge all the chabges</font></td>            
  </tr>
  <tr>
    <td><font size="1">14</font></td>
    <td><font size="1"><code>git checkout -b feedback_form origin/feedback_form</code></font></td>
    <td><font size="1">To see my branch and to get it from remote. </font></td>            
  </tr>
  <tr>
    <td><font size="1">15</font></td>
    <td><font size="1"><code>git branch -r</code></font></td>
    <td><font size="1">Check what is in remote. </font></td>            
  </tr>
  <tr>
    <td><font size="1">16</font></td>
    <td><font size="1"><code>git log</code></font></td>
    <td><font size="1">To see what you did. </font></td>            
  </tr>
  <tr>
    <td><font size="1">17</font></td>
    <td><font size="1">
      <code>git show 84b6afd0</code><br>
      <code>git show HEAD</code><br>
      <code>git show feedback_form</code>
    </font></td>
    <td><font size="1">
      To take a look at it. <br>
      If it was the last commit. <br>
      Use the branch name to see it.
    </font></td>            
  </tr>
  <tr>
    <td><font size="1">18</font></td>
    <td><font size="1"><code>git log</code></font></td>
    <td><font size="1">To see what you did. </font></td>            
  </tr>
  <tr>
    <td><font size="1">19</font></td>
    <td><font size="1"><code>git commit -am "Add tour selector to feedback form</code></font></td>
    <td><font size="1">If she makes a change and commit, that is all the changes still in her local machine. </font></td>            
  </tr>
  <tr>
    <td><font size="1">20</font></td>
    <td><font size="1"><code>git fetch/code></font></td>
    <td><font size="1">To put it on the remote machine.</font></td>            
  </tr>
  <tr>
    <td><font size="1">21</font></td>
    <td><font size="1"><code>git push</code></font></td>
    <td><font size="1">If all clear, just <code>push</code>. and she is done</font></td>            
  </tr>
  <tr>
    <td><font size="1">22</font></td>
    <td><font size="1"><code></code></font></td>
    <td><font size="1">Send a email, it looks great and just one change.</font></td>            
  </tr>
  <tr>
    <td><font size="1">23</font></td>
    <td><font size="1"><code>git fetch</code></font></td>
    <td><font size="1">Back to me, to see her changes.</font></td>            
  </tr>
  <tr>
    <td><font size="1">24</font></td>
    <td><font size="1"><code>git log -p feedback_form..origin/feedback_form</code></font></td>
    <td><font size="1">
      To see the diff of each log entry. <br>
      That is the difference from my copy of feedback_form to the remote respository.
    </font></td>             
  </tr>
  <tr>
    <td><font size="1">25</font></td>
    <td><font size="1"><code>git merge origin/feedback_form</code></font></td>
    <td><font size="1">
      To merge both feedback_forms, now they are in sync, this is a forward merge, <br>
      because you want only the latest, and we have not changed nothing.
    </font></td>            
  </tr>
  <tr>
    <td><font size="1">26</font></td>
    <td><font size="1"><code>git checkout master</code></font></td>
    <td><font size="1">To switch to master branch.</font></td>            
  </tr>
  <tr>
    <td><font size="1">27</font></td>
    <td><font size="1"><code>git fetch</code></font></td>
    <td><font size="1"></font></td>            
  </tr>
  <tr>
    <td><font size="1">28</font></td>
    <td><font size="1"><code>git merge origin/master</code></font></td>
    <td><font size="1">
      If there were changes from our masters, but likely a forward merge. <br>
      It just means you have done nothing and wanting to the latest.
    </font></td>            
  </tr>
  <tr>
    <td><font size="1">29</font></td>
    <td><font size="1"><code>git merge feedback_form</code></font></td>
    <td><font size="1">merge changes from <code>feedback_form</code> to <code>master</code></font></td>            
  </tr>
  <tr>
    <td><font size="1">30</font></td>
    <td><font size="1"><code>git push</code></font></td>
    <td><font size="1">Once resolve all conflicts. now my work is in the remote.</font></td>            
  </tr>
</table>


