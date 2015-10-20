# Git CheatSheet (Part 2)

1. Initialisation
2. Add and Commit
3. Logging
4. Architecture (Optional)

## 1. Initialising a project

* At the root of the project, run `git init`


## 2. Add and Commit
* To track a file, perform **Add** 
* To include changes in respository, perform **Commit** 
* Perform **Add** first then **Commit**

	
	| git                            | Definition                              |
	| :----------------------------- | :-------------------------------------- | 
	| `git add .`                    | To add everything to repository         |
	| `git add readme.txt`           | To add only readme.txt to repository    |
	| `git commit -m "comment"`      | To commit the change to repository      |
	

## 3. Logging

* To check who and what has committed and the changes.

	<table>
	  <tbody>
	    <tr>
	      <th>git</th>
	      <th>Notes</th>
	    </tr>
	    <tr>
	      <td><code>git log</code></td>
	      <td></td>
	    </tr>
	    <tr>
	      <td><code>git help log</code></td>
	      <td>Output help file</td>
	    </tr>
	    <tr>
	      <td>
	       <code>git log -n 1</code> <br>
	       <code>git log -n 5</code>
	      </td>
	      <td>
	        Last commit <br>
	        Last 5 commits
	      </td>
	    </tr>
	  </tbody>
	</table>


### 3.1. Log and search 

| git                                                | Notes                                                   |  
|:---------------------------------------------------| :-------------------------------------------------------| 
| `git log --since=2015-06-18`                       | Everything since that day and everything after          | 
| `git log --until=2015-06-15`                       | Everything from the beginning up until                  | 
| `git log --since=2015-06-15 --until=2015-06-18`    | Both since and until, in between a certain range        | 
| `git log --author="Matthew Lai"`                   | Search by Author                                        | 
| `git log --grep="create"`                          | search by grep, use this to look for bug/fixes          | 	



## 4. Architecture (Optional)


### 4.1. Two-tree architecture

* The concept of **Repository** and **Working** directory using **'commit'** and **'checkout'**. Git follows three-tree architecture.


### 4.2. Three-tree architecture

* From **Working** to **Staging index**, use
	* `git add file.txt`
* From **Staging index** to **repository**, use 
	* `git commit file.txt`. 
* Able to save all files in the **working directory**, and commit only just one file to **respository**.
* Ale to pull everything from **respository** to **working drectory**.

