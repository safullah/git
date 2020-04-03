**git** <br/>
echo "# angularjs" >> README.md
git init 
The word init means initialize. The command sets up all the tools Git needs to begin tracking changes made to the project.
intitialzes a new git project

git init [setup of working directory] -> git add [staging area] -> git commit [repository]
A Working Directory: where you’ll be doing all the work: creating, editing, deleting and organizing files
A Staging Area: where you’ll list changes you make to the working directory
A Repository: where Git permanently stores those changes as different versions of the project

staging area is to stage file changes for commit
commit Permanently stores  changes from staging area in the repository

git status 
As you write the screenplay, you will be changing the contents of the working directory. You can check the status of those changes with:
git status show: untracked files and file changes staged for commit

git add README.md

git commit -m "Complete first step"
Standard Conventions for Commit Messages:
Must be in quotation marks
Written in the present tense
Should be brief (50 characters or less) when using -m

git remote add origin git@github.com:safullah/angularjs.git
git push -u origin master

$ mkdir project.git
$ cd project.git
$ git init --bare
Initialized empty Git repository in /srv/git/project.git/
Then, John, Josie, or Jessica can push the first version of their project into that repository by adding it as a remote and pushing up a branch. 

# on John's computer
$ cd myproject
$ git init
$ git add .
$ git commit -m 'initial commit'
$ git remote add origin git@gitserver:/srv/git/project.git
$ git push origin master
At this point, the others can clone it down and push changes back up just as easily:

$ git clone git@gitserver:/srv/git/project.git
$ cd project
$ vim README
$ git commit -am 'fix for the README file'
$ git push origin master

//after cloning
//when cloning foreign repository and want to push to own repository
git remote set-url origin git@github.com:safullah/angularjs.git

git pull origin master
git pull --allow-unrelated-histories <branch>

//setup upstream
git push --set-upstream origin master

#### renaming a repository
$ git remote set-url origin <new_url>

//tutorial
https://guides.github.com/activities/hello-world/
https://www.git-scm.com

//checkout out a branch 
git checkout -b newfeature
git add . 
git commit -a -m "work of new feature finised"
//adding single file
git add -p report.md
git commit -m "added report.md"
//but before merge I have to push everything to my newfeature branch, 
//then I can merge into master
git push origin newfeature

//looking at history
git log --graph --decorate --abbrev-commit --all --pretty=oneline

//It’s typical to create a new branch and want to switch to that new branch at the same
//time — this can be done in one operation with 
git checkout -b <newbranchname>

//only creating new branch, but not switching
git branch <newbranchname>
//now switching to this branch
git checkout <newbranchname>

//check white space error before commiting
git diff --check

//after cloning before pushing
//update first
git fetch origin

//merge origin/master to your local master or branch
git merge origin/master
git push origin master

Often with Git, you’ll need to refer back to an earlier version of a project. Commits are stored chronologically in the repository and can be viewed with: git log
output of git log:
A 40-character code, called a SHA, that uniquely identifies the commit. This appears in orange text.
The commit author (you!)
The date and time of the commit
The commit message

//to look what is in one branch that the other does not have
//show what commits are in origin/master that are not in issue54
git log --no-merges issue54..origin/master

//merge issue54 to master
//first checkout master
git checkout master
git merge issue54

//merge origin/master into my master
git merge origin/master

//push changes to the server
git push origin master

//create new branch
git checkout -b feautreA
//push featureA branch to server
git push -u origin featrureA

//start a new feature branch, basing it off the server’s master branch
git fetch origin
git checkout -b featureB origin/master

//create the branch based off your master branch like this
//(sc is the initial of contributer )
git branch sc/ruby_client master
//or, if you want to also switch to it immediately, you can use the 
git checkout -b sc/ruby_client master

//push one branch to another
//-u stands for --set-upstream
git push -u origin featureB:featureBee


//Checking Out Remote Branches
git remote add jessica git://github.com/jessica/myproject.git
git fetch jessica
git checkout -b rubyclient jessica/ruby-client

//checking out a second branch from jessica
//not need for remote add, because already setup
git fetch jessica
git checkout -b rubyclient jessica/ruby-client

//When you “fork” a project, GitHub will make a copy of the project that is entirely yours;
//it lives in your namespace, and you can push to it.

//see all branches
git branch -a (all flag)

//delete local branch
git branch -d <name of branch>

//delete remote branch
git push origin --delete <name of branch>

//to unstage a file [I have done git add, now I want to remove it from the staging area]
git rm --cached <file> 

git checkout HEAD filename
will restore the file in your working directory to look exactly as it did when you last made a commit.

git reset
Great! The files you’ve added to the staging area belong in the same commit.

What if, before you commit, you accidentally delete an important line from scene-2.txt? Unthinkingly, you add scene-2.txt to the staging area. The file change is unrelated to the Larry/Laertes swap and you don’t want to include it in the commit.

We can unstage that file from the staging area using

git reset HEAD filename
This command resets the file in the staging area to be the same as the HEAD commit. It does not discard file changes from the working directory, it just removes them from the staging area.

Creating a project is like hiking in a forest. Sometimes you take a wrong turn and find yourself lost.

Just like retracing your steps on that hike, Git enables you to rewind to the part before you made the wrong turn. You can do this with:

git reset commit_SHA
This command works by using the first 7 characters of the SHA of a previous commit. For example, if the SHA of the previous commit is 5d692065cf51a2f50ea8e7b19b5a7ae512f633ba, use:

git reset 5d69206
HEAD is now set to that previous commit.

git checkout HEAD filename: Discards changes in the working directory.
git reset HEAD filename: Unstages file changes in the staging area.
git reset commit_SHA: Resets to a previous commit in your commit history.