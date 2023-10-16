#### About git and github

*git - open source vcs*
*github - hosting service (if we want our code online) (Github is by Microsoft)*

#### 

    git --version --> to check the version of git installed

#### *Configuration*

*Checking the current configuration with the commands*

    git config user.name
    git config user.email

*Setting the configuration commands*

    git config --global user.name "user"
    git config --global user.email "email"


#### *Repository - The main place we track changes and manage our files that are using git is called a Repository.*

    A Git "Repo" is a workspace which tracks and manages files within a folder.

#### How can we create a git repository?

    git init
    This command initializes a Git Repository on your local machine
    You only need to run this command once per project
    Initialize the repo in the top-level folder containing your project

    git status
    This command will report back the status of your git repository

### Warning - Don't init a repo inside a repo!!! 

* Before running git init, use git status to verify you are not inside the repo
* If you do end up making a repo inside of a repo, you can delete it and try again!
* To delete a repo, locate the associated .git directory and delete it

### Public repositories

*We can easily clone public repositories into our local witht the git clone command and then the HTTPS url for the repo. But it is not possible with other private repositories!!!*

    git clone https.//github.com/account/repo.git
### Private repositories

*We need to generate the token from the site*

    git clone https.//<enter token here>@github.com/account/repo.git

## BASIC GIT USAGE FOR SOLO DEVELOPER

### Adding 

* We use the git add command to stage changes to be committed. It means, to push our changes to the staging area.
* It's a way of telling Git, please include the change in our next commit

#### Beginner revision points 

    git clone or git init
    
    working directory - work in local
    repository - work in github.com 

    git add <filename>/.(for all files)
    staging area ? -> get ready to commit this 

    git commit -m <message> -> useful for log
    (committed to the repository)

    git push -> pushing it to the github


#### *Example of workflow*

    1) go into the folder and open it in text editor
    2) run git status to check whether it's an git repository or not
    3) git init --> initializes a git working directory
    4) Make changes , add code and save it
    5) run git status, u will be able to see untracked changes
    6) git add <fileName1> <fileName2>
    7) we can instead use git add . to stage all the changes
    8) git commit -m <message>
    9) Run git status, you will find clean working tree
    10) git log - to view log history of commits

#### *More about committing and other stuff*

* Difference between using -m flag with git commit is to pass in an inline message rather than opening a text editor

* *Below tip can be handy*

    Suppose we made a commit and then realized that we forgot to include a file or maybe we had made a typo in the commit message, which we need to correct. So rather than making a brand new seperate commit, we can redo the previous commit using the --amend option

* *Workflow to understand above tip*
###

    git commit -m "some wrong commit"
    git add forgetten file
    git commit --amend

### Quick tips about committing
* *Commit early and often*
* *Make commits atomic - group similar changes together*
* *Write meaningful but concise commit messages*
* *Present tense or Past tense - Always describe your changes in imperative mood, as if you are giving order to the codebase to change its behavior*
* *Some developers prefer past tense as well, it all depends on you, but just be consistent with one*

### Ignoring files

* We can tell Git which files and directories to be ignored in given repo, using a .gitignore file
* This is useful for files you know you NEVER want to commit, including:
###
    Secrets, API KEYS, Github Token, Credentials
    .DS_Store on Mac
    Log files
    Dependencies and Packages

### *How to make a proper .gitignore file*

    Create a file called .gitignore in the root of a repo
    Inside the file you can write patterns to tell Git which files and folders to ignore
    For example, 
    .DS_Store will ignore files named .DS_Store
    folderName/ will ignore an entire directory
    *.log will ignore any files with the .log extension

### Branches

* Alternative timelines for a project
* If we make changes on one branch, they don't impact the other branch (unless we merge the changes)
* In git, we are always working on a branch by default, called master/main
* It doesn't do anything special or have fancy powers. It's just like any other branch
* Many people designate the master branch as their "source of truth" or the "official branch" for their codebase, but not necessary to treat it in this way

### *In 2020, Github renamed the default branch from master to main. The default Git branch name is still master (not sure about this)*

### Head

* *Head is simply a pointer that refers to the current "location" in your repo. It points to a particular branch reference*

### Push and remote branch
*How to push the initial commit??*

    local - your pc

    git remote -v => we can check for remote branches with this command

    We tell git we want to add a remote branch using the git remote command syntax

        git remote add name <gitRepoUrl>

    By convention, we call this remote branch the origin branch

        git remote add origin <gitRepoUrl>

### How can we rename the remote branch?

    git remote rename <old> <new>
    git remote remove <name>

### How do we tell git to push to the remote

    main/master branch called origin with the command
    git push -u origin main/master
    git branch -M main -> renaming master to main

## How to fetch and pull 

*There are two options of getting repository changes from a remote branch*

* git pull
* git fetch

#### 

    WD -> git add -> Staging area -> git commit -> Local repository -> (git push) -> Remote repository

#### 

    git fetch -> will update your local repository logs, but remote se code aake aapke local mein files ko overwrite nhi krega!!!

* *Git fetch will download changes from the Github remote repository, however you will not see those changes be part of the files you have in the working directory*
    
* *Fetch allows us to grab additional work done on the remote master branch without needing to merge it in your working directory files*

* *Git fetch makes sense when you're working with others and want to see whtat changes they've made but aren't ready to overwrite your own files yet.*

#### *Commands*

    git fetch <remote> <branch>

#### *Usually, it is like this* 

    git fetch origin <branch>

    git pull -> will update your logs
    and as well as remote se saare code leke aayega aur aake aapki working directory mein overwrite krdegea!!!

    Using git pull makes sense when you want to directly grab changes from the remote branch and directly merge them into your current branch
    
    This means, you will literally update the files in your working directory to match up and merge with the remote branch

*But git pull is not a best practice*

### ---Understanding branches---

* Branch represents an independent line of development
* Branches serve as an abstraction for the edit/stage/commit process
* They are a way to request a brand new working directory, staging area, and project history
* Upon creating a new repo with git init, you create a new branch called the master branch or main branch
This is a branch just like any other, but it's simple the first one created.

### ---Master vs Main---

* Github ke liye initial branch is main branch
* Git ke liye initial branch is master branch, but it has changed
* We can also rename any branch (trunk branch)


### ---Creating a new branch----
    
    c1 -> c2 -> c3 <- main
    at c3 we make a new branch

    c1 -> c2 -> c3 - main
                |
                newBranch

    we make changes in new branch and commit it

    c1 -> c2 -> c3 - main
                |
                c4 -> c5 - newBranch

    Now we merge it 

    c1 -> c2 -> c3    
                |     
                c4 -> c5 - main, newBranch

* Branches are just references to a commit
* Using HEAD tells us which branch reference we are currently "checking out".
* We can always switch back out HEAD to some other branch (which is a pointer to a commit reference)

### *Creating and Switching*

*First method*

    git branch <newBranchName>
    git switch <newBranchName>

*Second method*

    git checkout -b <newBranchName>

*Third method*

    git switch -c <newBranchName>
    -c stands for create

### *Viewing more info about a branch*

    git branch -v

# git branch commands

*Renaming a branch*

    git switch branch_to_rename
    git branch -m new_name

*Deleting a branch*

    git branch -d <branch_to_delete_name>
    #You cannot delete a branch you are checkout at
    #You also will get a warning if the branch is not merged
        -> You can confirm you want to do this anyways with -D
    
### Merging - key points

* *We merge branches and not specific commits*
* *We always merge to the current HEAD branch*

### *Follow these steps for merging*

* Switch to or checkout the branch you want to merge the changes into (the recieving branch)
* Use the git merge command to merge changes from a specific branch into the current branch

###

    git switch master 
    git merge bugfix


### Kinds of merge

* Fast forward - master branch se koi branch banayi ho, uspe commits kiya ho, par master pe kisi aur ne koi commit na kiya ho toh, fast forward merge hojata hai. Bas master pointer ko apne branch ke pointer pe laana hota hai
* Merge commit - master branch se koi branch banayi ho, new branch pe commits kiya ho, par master pe aur kisi ke bhi commits aagaye ho to, merge commit krna padta hai jahan pe master aur abhi wali branch ke pointers merge commit wale pe aajate hain

### How do conflicts look

*Below is a example of conflict marker*

    <<<<<<<< HEAD
    I have 2 cats 
    I also have chickens
    ========
    I used to have a dog :(
    >>>>>>>> bug-fix

* *Content from your current HEAD (jis branch mein hum merge kr rahe hote hain (generally master or main)) is displayed between <<<<<< HEAD and ==========*
* *The content from the branch you are trying to merge from is displayed between the ======= and  >>>>>>> symbols.*

### Resolving conflicts

* Open up the file(s) with merge conflicts
* Edit the file(s) to remove the conflicts. We can decide which branch's content you want to keep for each or we can keep content from the both
* Remove the conflict markers in the document
* Add your changes and then

*Whenever you encounter merge conflicts, follow these steps to resolve them:*
### Merges more in detail
#### *Simple merge (Fast forward)*
    
    master
    |
    c1 -> c2 -> c3 
                |
            new_branch <- head

    For fast forward merge (example is taken for master and a branch named new_branch)
    1) git switch master
    2) git merge new_branch

                master <- head
                |
    c1 -> c2 -> c3 
                |
                new_branch

*More practical case*

            master <- head
            |
    c1 --> c5
        |
        |
        c2 -> c3 -> c4
                    |
                    new_branch

*Now, we need to merge new_branch with the master branch. For this we need to do the same thing again , but this is not fast forward merge*
#### *Here, there can be two scenarios*

* Auto commit - Best case
 
    


                                master <- head
                                |
        c1 --> c5 -------> *auto commit*
            |                   |
            |                   |
            c2 -> c3 -> c4 ---- |
                        |
                        new_branch

*Yeh tab hai jab conflicts naa ho dono branches mein*

* Merge Conflicts - Resolving conflicts and merging branches

    Git will warn us about files in conflict
    Our code editor will give a markdown and syntax highlighting for resolving the conflicts

### git diff

    git diff

* git diff is a powerful tool that can show the differences between data sets
* Display the differences betweent the original file and unstaged changes
* compares staging area and working directory

####

    git diff HEAD

* git diff HEAD list all changes in the working directory since the last commit

### Understand git diff output 


    diff --git a/rainbow.txt b/rainbow.txt
    index 72d1d5a..f2c8117 100644
    --- a/rainbow.txt
    +++ b/rainbow.txt
    @@ -3,4 +3,5 @@ orange
    yellow
    green
    blue 
    -purple
    +indigo
    +violet

* Above is a sample output of git diff command 
* First line explains which files it is comparing. Usually these are the two versions of the same file
* Git declares one version as A and other as B
* Next line the is the file metadata containing the hashes of two file being compared.Last number is the internal file mode identifier and first two are the hashes.
* Markers - These are important. Basically, how the two files are going to be represented. File A gets the minus sign (-). While the file B gets the plus sign (+).
* Chunks - A diff won't show the entire contents of a file, but instead only shows portions or chunks that were modified.
* *Chunks also include some unchanged lines before and after a change to provide some context*
* *Each chunk starts with a chunk header found between @@ and @@*
* *@@ -3,4 +3,5 @@ orange, this chunk header means, 4 lines are extracted from file A starting from line 3. Also 5 lines are extracted dfrom file B starting from line 3*

#### What is going to get committed?

    git diff --staged
    git diff --cached

* These two commands works the same. Both will list the changes between the staging area and our last commit. This means that below quote :

    *Show me what will be included in my commit if I run git commit right now*

#### Viewing changes with a file

    git diff HEAD [filename]
    git diff --staged [filename]

* We can view the changes within a specific file by providing git diff with a filename.

#### Comparing branches

    git diff branch1..branch2

* git diff branch1..branch2 will list the changes between the tips of branch1 and branch2

#### Comparing commits

    git diff commit1..commit2

* To compare two commits, provide git diff with the commit hashes of the commits in question.