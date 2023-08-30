git - open source vcs
github - hosting service (if we want our code online) (Github is by Microsoft)

~ git --version --> to check the version of git installed

~ Configuration

-> Checking the current configuration with the commands
    1) git config user.name
    2) git config user.email

-> Setting the configuration commands 
    1) git config --global user.name "user"
    2) git config --global user.email "email"


Repository - The main place we track changes and manage our files that are using git is called a Repository.


How can we create a git repository?

-> git init
    This command initializes a Git Repository on your local machine
    You only need to run this command once per project
-> git status
    This command will report back the status of your git repository


Public repositories
    We can easily clone public repositories into our local witht the git clone command and then the HTTPS url for the repo. But it is not possible with other private repositories!!!

    git clone https.//github.com/account/repo.git
Private repositories
    We need to generate the token from the site

    git clone https.//<enter token here>@github.com/account/repo.git


Day 2
 --> git add, git commit, git push, git pull, git status, git log, git diff

BASIC GIT USAGE FOR SOLO DEVELOPER
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


    Push and remote branch

    local - your pc

    git remote -v => we can check for remote branches with this command

    We tell git we want to add a remote branch using the git remote command syntax

        git remote add name <gitRepoUrl>

    By convention, we call this remote branch the origin branch

        git remote add origin <gitRepoUrl>

How can we rename the remote branch?

    git remote rename <old> <new>
    git remote remove <name>

How do we tell git to push to the remote
main/master branch called origin with the command
git push -u origin main/master

git branch -M main -> renaming master to main