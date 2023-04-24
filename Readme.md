What is Git ?    

		Free and open source version control system 

What is version control ?   

		The management of changes to document,computer programs,large websites and other collection of information

What is difference git and github ?      

		git    : Its a tool that track the code changes
		github : Its a websites where you can host all your repositories in remote

Source Code Management Tools(SCMT):

	GitHub
	GitLab
	BitBucket
	SVN
	TFS
	CVS
	Azure Repos

Git Commands:   
 
	clone  : Bring to local system/ENV  
	add    : track your files and changes in git  
	commit : save the files in git  
	push   : upload git commits to a remote repo like Github  
	pull   : Download changes from remote to local machine [ oppsite of push ]  


Clone:

      git clone URL

Untracked :  Created a new file but not added to track it. Tracking can be done by using git add command.
    
    git status
   
Add:  Two ways   
	
    git add .          # add multiple files  
    git add filename   #single file with filename
 
Note :    If cloned using http url use before commit

    git config --global user.email "you@example.com"  
    git config --global user.name "Your Name"   

Commit :

    git commit -m "Content of commit message" 
    
Push:
    
    git push

git clean: It will remove the files
	
	git clean -f   # it will remove the files
	git clean -f file_name1 file_name2 ...
		
git reset: It will bring back to working-area(Untracked) from staging-area(tracked)
			 
	git reset
	git reset file_name.java
	
git revert: It will revert the last commit. First revert and push code.

	git revert cd80c1c4c2


Github Workflow:

    Write code -> Commit changes  -> Create PR

Local Git Workflow:
    
    Write code -> Stage changes -> Commit changes  -> Push changes  -> Create PR
                  [ git add ]      [ git commit ]      [ git push ]

Git Branching: Branch can be created by developers for development.  Star indicates current branch.
		
		git branch                   	     # used to check  the branch
		git branch <branch_name>    	     # used to create the branch  ex: git branch development
		git branch -d <branch_name> 	     # used to delete the branch  ex: git branch -d development
		git branch -m <old_name> <new_name>  # used to rename any branch  branch ex: git branch development dev-branch   if we are master we can do rename using this 
		git branch -m <new_name>             # used to rename the current branch ex: git branch dev-branch if can rename for current branch
		git checkout <branch_name>           # switch from one to other branch ex: git branch dev-branch
		git checkout -b feature-branch       # Create amnd Switched to a new branch 'feature-branch'




Pull:  The Latest updates to master.....fecth to local repo

    git pull                 [or]
    git pull origin master


Merge Conflict:   Your local branch is not up-to-date with master

Example:

    From master create a branch "quick-test-branch"
	      git checkout -b quick-test-branch
          git status
	 Make some changes in readme file
	      git diff   
	      git commit -am "Message"

    From branch to go to master
          git checkout master
	 Make some changes in readme file     # previous branch will be there beacuse its not merged
	      git branch
	      git checkout quick-test-branch  # please commit your changes or stash them before you switch branches.Aborting [ in master line 2 chaned with <p>Hi</p> , in branch also <p>Welcome</p> ]
	      git status
	      git commit -am "makes changes in readme file"
	      git checkout quick-test-branch
	      git dif master
	      git merge master  # CONFLICT (content): Merge conflict in Readme.md
    
How to fix conflict:
    
    git status     # Newly created branch
    git commit -am "local Master and branch changes with conflit fix"
    git push


Tag: It is immutable. After the prod deployment tag will create. It will create zip and tar files. We cant delete the tag in remote repository

	Branch					Tag
	------					----
	git branch 				git tag
	git branch branch_name			git tag tag_name   (tag_name ->application_namev1.0.0)
	git branch -d branch_name		git tag -d tag_name
	git push an --all			git push --tags
	git push an branch_name			git push an tag_name (an -> alise name)


stash:  The code which is in working-area(untrackedL) will keep in temporary area. Until drop this save stash will be present
save: Will save the changes
	
	git stash                 [or] 
	git stash save "message"
list: git stash list will show how many back-up are there
	
	git stash list	 # how many back-up are there
	Example:
		stash{0}
		stash{1}
		stash{2}
apply: git stash apply will take recent one

	git stash apply stash_name
	Example:
		git stash apply stash{1}
drop: git stash drop will take recent one
	
	git stash drop stash_name
	Example:
		git stash drop stash{1}
	
pop: git stash pop will take recent one
	
	git stash pop stash_name
	Example:
		git stash pop stash{1}


cherry-pick: We can merge based on required commit-id


		master
		dev-branch DC1 DC2 DC3 DC4    # get the commit-id with the help of  "git log" command   DC3 -> ea14536g6
		go to master and run 
			git cherry-pick ea14536g6   ( ea14536g6 -> DC3)
			
Rebase: Using rebase all the commits and going to integrate to master. After integration we can individual commit-id details. Below DC means commit-ids
	
	merge
		 master single commit(DC)
			| merge
			v
		dev-branch DC1 DC2 Dc3

	merge
		 master DC1 DC2 Dc2
			| rebase
			v
		dev-branch DC1 DC2 Dc2
