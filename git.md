Git Usage
=========

## Init start

## Install git client

## Configure git client

## Create a new git repository
#### step1: prepare
make local dir for repository
```bash
mkdir repository-dir
cd repository-dir
```
#### step2: git init
init local git repository
```bash
  git init
```
as we init a new repository,git will talk with us like that:
```bash
Initialized empty Git repository in /path/repository-dir/.git/
```
#### step3: add local resource
some your project resource to this *repository-dir* as you wish
```bash
xxxxxxxxx
```
#### step4: add to git
your resource to git repository
```bash
git add dir/file
```
#### step5: commit it
commit to git,should with some **comment**
```bash
git commit -m "some comment for tag your modification"
```
#### step6: local to remote
at this time,you create your repository localized,when you want to push to public github,you should do these
```bash
git remote add origin https://github.com/*gitAccount*/*repository*.git
git push -u origin master
```