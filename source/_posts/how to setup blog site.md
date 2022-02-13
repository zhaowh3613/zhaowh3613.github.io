---
title: What i did to setup this site
tag: blog site
---
Welcome to [my blog](https://www.zhaowenhui.tech)!  This is my very first post. It records the steps about how to setup personal blog site on github and how to use travis CI to auto deploy the changes. 

## Steps

### Create a new repo and push to github

```
repo must be named account_name.github.io
```

### Init hexo

``` bash
$ hexo init blog
$ cd blog
$ npm i
```
### Update _config.yml for common
``` bash
url: https://username.github.io
``` 

### Update _config.yml for deploy
``` bash
deploy:
  type: git
  repo: git@github.com:username/username.github.io.git
  branch: gh-pages
``` 
### Update theme
``` bash
npm i hexo-theme-next --save

copy _config.next.yml to the root directory
```
or
``` bash
$ cd hexo
$ git clone https://github.com/theme-next/hexo-theme-next themes/next

```

``` bash
modify _config.yml as below
theme: next
``` 
### Generate static files

``` bash
$ hexo clean
$ hexo generate
```

### Deploy to remote sites manually
``` bash
$ npm i hexo-deployer-git
$ hexo deploy
```

### Deploy to remote sites by travis CI
``` bash
generate githup personal access token
grant github repo permission to travis
add token to travis Environment Variables
```
``` bash
add .travis.yml 

sudo: false
language: node_js
node_js:
  - 16 # use nodejs v10 LTS
cache: npm
branches:
  only:
    - master # build master branch only
script:
  - hexo clean
  - hexo generate # generate static files
deploy:
  provider: pages
  skip-cleanup: true
  github-token: $GH_TOKEN
  keep-history: true
  on:
    branch: master
  local-dir: public
```

### Customize domain
``` bash
purchase personal domain from ali yun
parse my github page ip with domain
update new domain in github page of this repo setting page 
```
