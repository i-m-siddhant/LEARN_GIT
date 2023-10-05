git - open source vcs
github - hosting service (if we want our code online) (Github is by Microsoft)

## git --version --> to check the version of git installed

## Configuration

*Checking the current configuration with the commands*

    git config user.name
    git config user.email

*Setting the configuration commands*

    git config --global user.name "user"
    git config --global user.email "email"


## Repository - The main place we track changes and manage our files that are using git is called a Repository.

** 

    A Git "Repo" is a workspace which tracks and manages files within a folder.

## How can we create a git repository?

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

## Public repositories

    We can easily clone public repositories into our local witht the git clone command and then the HTTPS url for the repo. But it is not possible with other private repositories!!!

    git clone https.//github.com/account/repo.git
## Private repositories
    We need to generate the token from the site

    git clone https.//<enter token here>@github.com/account/repo.git

Day 2
## git add, git commit, git push, git pull, git status, git log, git diff

## BASIC GIT USAGE FOR SOLO DEVELOPER

### Adding 

* We use the git add command to stage changes to be committed. It means, to push our changes to the staging area.
* It's a way of telling Git, please include the change in our next commit

    git clone or git init
    
    working directory - work in local
    repository - work in github.com 

    git add <filename>/.(for all files)
    staging area ? -> get ready to commit this 

    git commit -m <message> -> useful for log
    (committed to the repository)

    git push -> pushing it to the github


Example of workflow

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


## Push and remote branch
    How to push the initial commit??

    ** 

    local - your pc

    git remote -v => we can check for remote branches with this command

    We tell git we want to add a remote branch using the git remote command syntax

        git remote add name <gitRepoUrl>

    By convention, we call this remote branch the origin branch

        git remote add origin <gitRepoUrl>

## How can we rename the remote branch?

    ** 

    git remote rename <old> <new>
    git remote remove <name>

## How do we tell git to push to the remote

    **

    main/master branch called origin with the command
    git push -u origin main/master
    git branch -M main -> renaming master to main

## How to fetch and pull 

    **

    There are two options of getting repository changes from a remote branch

    git pull
    git fetch

## WD -> git add -> Staging area -> git commit -> Local repository -> (git push) -> Remote repository

## git fetch -> will update your local repository logs, but remote se code aake aapke local mein files ko overwrite nhi krega!!!

** 

    Git fetch will download changes from the Github remote repository, however you will not see those changes be part of the files you have in the working directory
    
    Fetch allows us to grab additional work done on the remote master branch without needing to merge it in your working directory files

    Git fetch makes sense when you're working with others and want to see whtat changes they've made but aren't ready to overwrite your own files yet.

## Commands 
    ** 

    git fetch <remote> <branch>

## Usually, it is like this 

    ** 

    git fetch origin <branch>

    git pull -> will update your logs
    and as well as remote se saare code leke aayega aur aake aapki working directory mein overwrite krdegea!!!

    Using git pull makes sense when you want to directly grab changes from the remote branch and directly merge them into your current branch
    
    This means, you will literally update the files in your working directory to match up and merge with the remote branch

## But it is not a best practice


## Day 3 topics

    **

    Master/main branch and branches -> important
    What is head? -> very important
    Git branch commands
        -> git branch - basic command, no harm
        -> git switch - good to know
        -> git checkout - very important
    Delete or rename branch  - not so useful
    Merging branch and conflicts - very important 
    Using git diff - not so useful, better to have gitlens!!!


## ---Understanding branches---

* Branch represents an independent line of development
* Branches serve as an abstraction for the edit/stage/commit process
* They are a way to request a brand new working directory, staging area, and project history
* Upon creating a new repo with git init, you create a new branch called the master branch or main branch
This is a branch just like any other, but it's simple the first one created.

## ---Master vs Main---

* Github ke liye initial branch is main branch
* Git ke liye initial branch is master branch, but it has changed
* We can also rename any branch (trunk branch)


## ---Creating a new branch----

    *
    
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


# git branch commands

*Renaming a branch*

    git switch branch_to_rename
    git branch -m new_name

*Deleting a branch*

    git branch -d <branch_to_delete_name>
    #You cannot delete a branch you are checkout at
    #You also will get a warning if the branch is not merged
        -> You can confirm you want to do this anyways with -D
    

# Merging Branches and conflicts


# Simple merge (Fast forward)
    *

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

# More practical case

    * 

            master <- head
            |
    c1 --> c5
        |
        |
        c2 -> c3 -> c4
                    |
                    new_branch

Now, we need to merge new_branch with the master branch. For this we need to do the same thing again , but this is not fast forward merge
    Here, there can be two scenarios

* Auto commit - Best case
 
    *


                                master <- head
                                |
        c1 --> c5 -------> *auto commit*
            |                   |
            |                   |
            c2 -> c3 -> c4 ---- |
                        |
                        new_branch

    Yeh tab hai jab conflicts naa ho dono branches mein 

* Merge Conflicts - Resolving conflicts and merging branches

    Git will warn us about files in conflict
    Our code editor will give a markdown and syntax highlighting for resolving the conflicts

## git diff

* git diff is a powerful tool that can show the differences between data sets
* Display the differences betweent the original file and unstaged changes
