# Git CheatSheet (Part 1)

1. Installation
2. Configuration



## 1. Git Installation
* Download git at <http://git-scm.com>
* To check if git is installed sucessfully, use the followings
	* `which git`
	* `git --version`




## 2. Configuration


### 2.1. Three Levels of configurations

* ***System -*** It applies to all users of the computer. File located in `cat /etc/.gitconfig`
* ***Single User -*** It applies to a single user. File located in `cat ~/.gitconfig`
* ***Project -*** It applies to the project. File located in `cat <my_project>/.git/config`



### 2.2. Typical Configurations

<table>
  <tbody>
    <tr>
      <th align="center"> Functions </th>
      <th align="center">Git</th>
      <th align="center">Notes</th>
    </tr>
    <tr>
      <td rowspan="2">List <br>config</td>
      <td align="left"> <code>git config --list</code> </td>
      <td align="left">  </td>	      
    </tr>	  
    <tr>
      <td align="left"><code>git config user.name</code></td>
      <td align="left"> To list a specific one  </td>
    </tr>
    <tr>
      <td rowspan="5">Typical <br>config</td>
      <td align="left"><code>git config --global user.name "ML"</code></td>
      <td align="left">  </td>
    </tr>
    <tr>
      <td align="left">
        <code>
          git config --global user.email "ML@mail.com" <br>          
        </code>
      </td>
      <td align="left">  </td>
    </tr>
    <tr>
      <td align="left">
        <code>git config --global core.editor "vim" </code><br>
        <code>git config --global core.editor "mate -wl1"</code>
      </td>
      <td align="left"> 
        vim/Textmate editor <br>
        w = wait <br>
        l1 = starts in line 1
      </td>
    </tr>
    <tr>
      <td align="left"><code>git config --global color.ui true</code></td>
      <td align="left"> to tell git to use color  </td>
    </tr>
  </tbody>
</table>

