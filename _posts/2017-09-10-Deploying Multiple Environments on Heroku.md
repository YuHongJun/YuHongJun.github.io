---
author: Demi_YuHongJun
comments: true
date: 2017-09-10 05:42:32+00:00
layout: post
title: Deploying Multiple Environments on Heroku
description: deploying-multiple-environments-on-heroku
keywords: Deploy
categories:
- Tech
tags:
- Heroku
---
* 目录
{:toc}
---

https://devcenter.heroku.com/articles/git#deploying-code

[Managing Multiple Environments for an App](https://devcenter.heroku.com/articles/multiple-environments)

```
heroku create appname --remote staging
git push staging master / git push -f staging dev:master
heroku ps --remote staging
```

Deploying code
To deploy your app to Heroku, you typically use the git push command to push the code from your local repository’s master branch to your heroku remote, like so:
```
$ git push heroku master
Initializing repository, done.
updating 'refs/heads/master'
```
...
Use this same command whenever you want to deploy the latest committed version of your code to Heroku.

Note that Heroku only deploys code that is pushed to the master branch of your heroku remote. Pushing code to another branch of the remote has no effect.

If you want to deploy code to Heroku from a non-master branch of your local repository (such as testbranch), use the following syntax to ensure it is pushed to the remote’s master branch:
```
$ git push heroku testbranch:master
```

