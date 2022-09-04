What is Git ?    

		Free and open source version control system 

What is version control ?   

		The management of changes to document,computer programs,large websites and other collection of information

What is difference git and github ?      

		git    : Its a tool that track the code changes
		github : Its a websites where you can host all your repositories in remote

Git Commands:   
 
	clone  : Bring to local system/ENV  
	add    : track your files and changes in git  
	commit : save the files in git  
	push   : upload git commits to a remote repo like Github  
	pull   : Download changes from remote to local machine [ oppsite of push ]  


Clone:

      git clone URL

Note:  
Untracked : Created a new file but not added to track it. Tracking can be done by using git add command
    
    git status
Add:  Two ways   
	
	git add .          # add multiple files  
    git add filename   #single file with filename
 
Note :   
If cloned using http url use before commit

    git config --global user.email "you@example.com"  
    git config --global user.name "Your Name"   

Commit :

    git commit -m "Content of commit message" 
Push:
    
    git push

Github Workflow:

    Write code -> Commit changes  -> Create PR

Local Git Workflow:
    
    Write code -> Stage changes -> Commit changes  -> Push changes  -> Create PR
                  [ git add ]      [ git commit ]      [ git push ]

Git Branching:

Check the current branch :

    git branch

Creating a new branch:    [ new branch name is feature-branch]

    git checkout -b feature-branch    #Switched to a new branch 'feature-branch'

Switch from one branch to other branch:  
star indicates current branch

    git checkout master
    git checkout feature-branch

Pull:  
The Latest updates to master.....fecth to local repo

    git pull                 [or]
    git pull origin master

Delete branch:
    
    git branch -d feature-branch

Merge Conflict:   
  Your local branch is not up-to-date with master

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