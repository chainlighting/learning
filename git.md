Git Usage
=========

## Init start
####1. signup github
>signup github,you will get your github account **username** and **email**. this account will be used in your git trip.
####2. setup git client
> setup git client(macos/windows/linux),you can reference this url:https://help.github.com/articles/set-up-git/#platform-all

## Configure git client
####1. set git access acount
> we should configure the git's remote access account for get remote repository.
> **global setting**
> ```bash
> git config --global user.name "your name"
> git config --global user.email "your email"
> ``` 
> this setting will be saved in "*~/.gitconfig*"
> [*we can use this setting for a special linux user*]
> 
> **system setting**
> ```bash
> git config --system user.name "your name"
> git config --system user.email "your email"
> ```
> this setting will be saved in "*/etc/gitconfig*"
> [*we can use this setting for whole host*]
> 
####2. set the remote repository url
> you can set a local repository linked with a remote repository url,like that:
> ```bash
> cd repository_dir
> git remote set_url origin https://github.com/"username"/"repository".git
> ```

## Create a new git repository
####0. github
> when create a new repository,you first step is to create it in github,so you can binging local repository with github repository at later step.
> 
> *login github.com*
> *use create repository to create a github repository*
####1. prepare
> make local dir for repository
> ```bash
> mkdir repository-dir
> cd repository-dir
> ```
####2. git init
> init local git repository
> ```bash
> git init
> ```
> as we init a new repository,git will talk with us like that:
> ```bash
> Initialized empty Git repository in /path/repository-dir/.git/
> ```
####3. add local resource
> some your project resource to this *repository-dir* as you wish
> ```bash
> xxxxxxxxx
> ```
####4. add to git
> your resource to git repository
> ```bash
> git add dir/file
> ```
####5. commit it
> commit to git,should with some **comment**
> ```bash
> git commit -m "some comment for tag your modification"
> ```
####6. local to remote
> at this time,you create your repository localized,when you want to push to public github,you should do these
> ```bash
> git remote add origin https://github.com/"username"/"repository".git
> git push -u origin master
> ```

## Push a existing repository to remote github
> when you have a local repository,you want to push it to a new github repository,you can do like that:
> ```bash
> git remote add origin https://github.com/"username"/"repository".git
> git push -u origin master
> ```

## Common Usage
####1. git status
> you can check your repository's change like that
> ```bash
> cd repository_dir
> git status
> ```
> 
> git will reply like that
> ```bash
> # On branch master
> # Changes not staged for commit:
> #   (use "git add <file>..." to update what will be committed)
> #   (use "git checkout -- <file>..." to discard changes in working directory)
> #
> #       modified:   git.md
> #
> no changes added to commit (use "git add" and/or "git commit -a")
> ```
> this reply tips us the "git.md" has been modified
####2. git diff
> you can find the differnet with *last commit*.
> **repository diff**
> ```bash
> cd repository_dir
> git diff
> ```
> **special file diff**
> ```bash
> cd repository_dir
> git diff "special file or dir"
> ```
####3. git log
####4. git checkout
####5. git branch
####6. git merge
####7. git push
####8. git clone
####9. git pull
####10. git stash
####11. git init
####12. git reflog
####13. git rm
####14. git remote


## Advanced Usage
####1. set git's http proxy
> at some environment,we should use http proxy to access extra-network,so we must set git's http proxy for working.
> git's config have the http proxy setting,we can set like that:
> ```bash
> git config [--global|--system] http.proxy http://"http_proxy_username":"http_proxy_pwd"@http_proxy_server:http_proxy_port
> ```
####2. set ssh remote access
> use ssh remote access,we can push to remote without passwd.
> ####2.1 create the sshkey
> > ```bash
> > ssh-keygen -t rsa -C "youremail@example.com"
> > ```
> > then you will get your git's rsa pubkey. will be at this position:
> > [*~/.ssh/id_rsa.pub*]
> ####2.2 put pubkey to github
> > login github.com,goto *User Profile/SSH keys/*,click run *Add SSH key*,
> > and then put the id_rsa.pub content into it,click run *Add key*.
> > 
