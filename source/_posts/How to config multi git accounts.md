---
title: How to config multi git accounts 
date: 
tags: git ssh config
category: git
---
The background is i have to access both github and company git account on my working computer, i wish it can switch git account automatically.

## **Generate ssh pub & private key**
``` bash
$ ssh-keygen -t rsa -C "your_github_email@example.com"
```
## **Add ssh pub key to github settings**

## **Create independence ssh configuration file for different git account**
``` bash
root directory：~\\.ssh 
-  /company/.gitconfig-company
-  /github/.gitconfig-github
- .config
```
## **Set configuration file**
``` bash
.gitconfig-company

[User]
	name = username
    email = company git account email
```
``` bash
.gitconfig-github

[User]
	name = username
    email = github account email
```
``` bash
.config

#git for company
Host 
User 
IdentityFile ~/.ssh/company/zhaowh3_rsa
  
#git for github
Host github.com
HostName github.com 
User git
IdentityFile ~/.ssh/github/id_rsa_github
```
