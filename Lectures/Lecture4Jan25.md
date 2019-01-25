# Git workflow

## Clone vs. pull

Clone copies all files from remote repository to local repository

Pull will only pull down incremental changes

Git init creates just a blank repository

### Can I clone to github?

not exactly but you can make a new respository and then push everything there

Create a fresh bare repository on the server:
```
git init --bare newrepo.git
```
or click new repository on git hub :smile:

Add it as a remote in your local repo:
```
git remote add newrepo git://user@server.com/newrepo.git
```
or 
```
git remote add newrepo http://github.com/$username/newrepo.git
```
```
git push newrepo master 
```
to push a particular branch, or
``` 
git push --all newrepo 
``` 
to push all branches


## Where am I pushing and pulling from?

Git remote -v will show remote sites.

Git clone will autmoatically populate git remote with site you cloned (origin)

Can also specify with a catchy name

```
git remote add wax https://github.com/awaxye/workflow
```

Can also remove them if you need

``` 
git remote rm wax
```

## Let's push something out to new repository
VIM readme.md on gitbash
add some description
Git add, git commit

git push wax master  (git push <remote> <branch>)
  
Should now be on your github repository

## Feature Branch Development
* Use branches to develop new features, fix bugs, try out new things without affecting your `master` branch.
* A useful branch naming convention: `$USER/$FEATURE`
* `master` should ideally hold only "functional" code.
* When you want to presrve a snapshot of the `master` branch state, you can create an annotated tag:
```
git tag -a 'v0.0.1' -m 'first semantically-versioned tag'
```

### Collaboration on Single Repository
* Settings -> Collaborators
* Everyone clones the same repository and submits Pull Requests from feature branches.
* How do you know if you're working on the most current version?  
```
git status
```
git log or git pull can also tell you but dangerous to git pull blindly

### Forking Repository
* Fork button is on upper right of window.  Click insights to see a list of forks
* If you don't have Collaborator access to a repository, you can still create a Pull Request from a *fork* of that repository.
* You *must* commit your changes on a branch of your forked-repository; trying
  to issue a Pull Request from your `master` branch will cause headaches.

### Pull Requests 
* A GitHub feature to merge a branch into another branch (commonly a feature
  branch into `master`, but can be any branch into another branch).
* Can use commit / file change review features and/or perform an actual code
  review before accepting changes.
* Merge strategies:
  + Merge (creates a commit reflecting the merged content, in addition to the
    individual commits on the branch being merged)
  + Squash-n-Merge (create a merge commit, but "squash" all of the commits of
    the feature branch into one)
  + Rebase (integrate the commits of the feature branch into your target branch
    by "replaying" them into the history)

### CLI Merging
* Merging can also be be done using the CLI, without a GitHub Pull Request.
* `git merge [--squash]`

### Issues 

Report an issue - can tag a user, label or quote the code

Ex: Create a branch to fix the feature  

```
git checkout -b awaxye\fix_feature
```
Fix the issue - can use
 ```
 git diff
 ```
 to see the changes line by line.
 

### Mission 
For everything below, `$netid` refers to your Duke Net ID (e.g., `apw2`), not your GitHub username.
* Fork this repository: https://github.com/apw2/BME547_lecture4_Jan25
* Clone your forked repository to your local computer
* Create a new branch called `$netid/myinfo`
* In your new branch, create a new file called `$netid.csv`
* Add a line to that file that contains:
```
# Firstname, Lastname, Net ID, GitHub Name
# For example:
Wax, Adam, apw2, awaxye
```
* Push your working branch to your GitHub fork
* Using GitHub, submit a Pull Request to merge your branch on your forked repository back into `awaxye/BME547_lecture4_Jan25`


