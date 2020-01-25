**git** <br/>
echo "# angularjs" >> README.md
git init
git add README.md
git commit -m "first commit"
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