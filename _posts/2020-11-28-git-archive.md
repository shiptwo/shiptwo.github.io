---
layout: post
title:  "Git Archives"
author: nilesh
categories: [ Git ]
image: "https://images.unsplash.com/photo-1530286443292-077db8d466a4?ixlib=rb-1.2.1&ixid=MXwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHw%3D&auto=format&fit=crop&w=1080&q=80"
comments: false
courtesy: '<span>Photo by <a href="https://unsplash.com/@catvcarvalho?utm_source=unsplash&amp;utm_medium=referral&amp;utm_content=creditCopyText">Catarina Carvalho</a> on <a href="https://unsplash.com/s/photos/archive?utm_source=unsplash&amp;utm_medium=referral&amp;utm_content=creditCopyText">Unsplash</a></span>'
read_time: 5
---
Commands you need when an archive is to be shared with someone either online or offline.

# Offline
Usually we used to `zip` the folder which would then complain while `unzip` with long path error. This happens because because of hidden `.git` folder & related files which are also zipped.
> Path too long    

## :punch: Enter 'git archive' 
[`archive`](https://git-scm.com/docs/git-archive) is useful to create an archive from your local / remote repository.
```shell
git archive --format=zip --output=archive-20201128 HEAD
```

# Online
I ran into a case where my colleage needed codebase to start work but did not have an Git account yet. A solution was to share my credentials but then that does sound good.

## :rainbow: Personal Access Tokens
So rather sharing Git credentials, I created a **Personal Access Token** with only the access I wanted to give using roles. The token could then be used with Git commands or REST API.

I tried this with GitHub but other providers like BitBucket, GitLab also support these.

Here is what you need to do:
- Login to your GitHub account
- Navigate to **Settings** -> **Developer Settings** -> **Personal access tokens**
- Click **Generate new token**
- Add a good name to your token that could also indicate purpose
- Select the roles you want (GitHub explains briefly each one of those) 
- Click **Generate token**
- Copy the generated token (Note: this is the only time you will see it, else you need to create new)
- You can update the roles later or delete the token if not needed
- You can then select respective GitHub API to do your task, like I needed an archive of my code
    - I did not set any specific role to the token
    - I referred GitHub REST API to [download archive](https://docs.github.com/en/free-pro-team@latest/rest/reference/repos#download-a-repository-archive-zip)
    - Then passed the token to [Authenticate API request via Personal access tokens](https://docs.github.com/en/free-pro-team@latest/rest/overview/other-authentication-methods#via-oauth-and-personal-access-tokens)
    - This is the command I finally ran:
      ```shell
      curl -L -u <username>:<personal-token> -H "Accept: application/vnd.github.v3+json" https://api.github.com/repos/<org-or-username>/<repository>/zipball/<branch> > <output-zip-archive>.zip
      ```
- You can use the personal token as a password as well

**:warning: Keep assigned roles to mininum & remember to delete the tokens if you are not using them**