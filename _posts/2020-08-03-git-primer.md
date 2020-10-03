---
layout: post
title:  "Git Primer"
author: nilesh
categories: [ Git ]
image: "https://images.unsplash.com/reserve/bOvf94dPRxWu0u3QsPjF_tree.jpg?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=1055&q=80"
comments: false
courtesy: '<span>Photo by <a href="https://unsplash.com/@johannsiemens?utm_source=unsplash&amp;utm_medium=referral&amp;utm_content=creditCopyText">Johann Siemens</a> on <a href="https://unsplash.com/@johannsiemens?utm_source=unsplash&amp;utm_medium=referral&amp;utm_content=creditCopyText">Unsplash</a></span>'
read_time: 15
---

When I first moved from Subversion things seemed a lot confusing with a bunch of commands to run everytime mechanically for a brief period. Thats how I got introduced to it anyway, with a text file that said do this & do that & finally do this with every changes you do (Damn, I hated being a bot :rage3:).

But things seemed logical when I started understanding it conceptually. This post will help readers (like me :wink:) avoid some hiccups & would serve as a [Primer](https://www.merriam-webster.com/dictionary/primer) for Git.
> a short informative piece of writing

We will asssume git is installed on your computer. If you're unsure, just open up a terminal & enter `git` to check if that runs else follow this [article](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git).

##### :broken_heart: Spoiler Alert
Just before we dive in, this post is a really long one...

## :surfer: Round 1, Scouting
We will start by setting up a git repository locally performing a series of steps which we will digest eventually. 

###### :bulb: While we are at it, just focus (:eyes:) on the command names & think briefly what it means literally.

Say for example, `git init`, `git` happens to be start of everything related to git, next we have `init` which seems  (indeed) to be a short of `initialize` that means setting up something.

- Create a directory for your codebase
    ```bash
    mkdir ~/my-repo
    ```
-  Initialize the git repository
    ```bash
    cd my-repo
    git init
    ```
- Add code
    ```bash
    touch somefile.js
    echo "console.log('Hello Git');" >> somefile.js
    ```
- Now check your changes using this command. It should indicate these as `untracked` changes. It also shows current `branch` is master.
    ```bash
    git status
    ```
- Now add (`stage`) your changes. Do not worry about this, we will come to this later.
    ```bash
    git add somefile.js
    ```
- Run status command now. It should now indicate these as `uncommitted` changes.
    ```bash
    git status
    ```
- To finalize (`commit`) your changes, run the commit command. Do add a short meaning full message with it.
    ```bash
    git commit -m "my first committed js file"
    ```
- Run the `status` command again. You should see no changes being shown. This indicates commit is done.
- Run `log` command to list all the events (commits) happened so far.
    ```bash
    git log
    ```
- The last step now will be `push` the finalized changes to repository so that others can use them.
    ```bash
    git push origin master
    ```

## :mag: Round 2, Scrutinize
So far we came across a lot jargons. Let's list them down first & then understand each one of them:
- Git Repository
- Branches
- State of changes
    - Untracked / Tracked
    - Unstaged / Staged
    - Uncommitted / Committed
- Adding changes
- Committing changes
- Commit history
- Pushing / Pulling changes


## :dart: Round 3, Detailing each step
### Git Repository
The first thing to start with is **git repository**. A repository is some place where you safely place all your files (your codebase) & share among your team. Just like a folder but additionally it also keeps a history of all changes.
> Who did What & When

This repository can be on your `own` computer or a `remote` computer (server). GitHub, GitLab, BitBucket are some examples of remote git repository providers.

The strongest concept of git is the ability to commit your changes locally which is helpful to minimise missing or losing any changes.
> Remember to commit your changes at every logical end point with a meaningful message.

The first step we did was initializing the repository using `git init` command. This will also create a `master` branch for us.

### Branches
> The state of your codebase is a Tree, a branch of that tree is Branch.

Branch is like a tree branch. It's a snapshot of the codebase where you define a starting point & then do your changes.

Say we had a `master` branch, then we were needed to develop a feature related to sign in. So we should start from `master` then develop feature from it. Technically you do this, cut a feature branch from master branch & then move on.

```bash
git checkout master # switch to master branch
git branch feature_sign_in # create a new branch
git branch # lists local branches
git checkout feature_sign_in # switch to new branch
```

### Changes
Changes are the modifications we do to the codebase. These include file additions, deletions & updates.

Git classifies these changes as:
- Untracked changes - The newly addded files are interpreted as Untracked changes because Git does not know any version history of it.
- Unstaged changes - The modifications done to a file fall under this. These are **tracked** changes that Git knows about. These are also the changes that are not yet finalized.
- Staged changes - The modifications that are finalized fall under this one. These too are **tracked** changes that Git knows about. These are yet to be committed.
- Committed changes - Finalized modifications that are committed to branch. These too are **tracked** changes that Git knows about. These are yet to be committed.

Now if we recall our earlier steps, we added some file (untracked change) then added it to git (staged change) then committed our changes (committed change).

### Commits
Git has a fundamental of committing locally. So whatever we commit is always local unless we push them to repository.
Only then others will be able to use the latest code.

:bulb: Push is a term used in context of remote repository, right now we created a local repository that is not shared with anyone.

You commit you code with following command:
```bash
git commit -m "some message"
```
To view a historic commits, you can use log command:
```bash
git log
```

### Push & Pull
When we have remote git repository, we come across the terms `push` & `pull`. If we go by their literal meaning, `pull` means we are fetching new changes while `push` means we are sending new changes.

While doing push / pull operation we also have to mention from what `remote origin` we have to fetch the changes.
What this means is, you can have one codebase that is maintained at multiple remote git repositories.

- So lets take an example, we have a codebase that has 2 remote repositories, say, staging & production. We check the number of repositories by using this command:
    ```bash
    git remote -v
    ```
- To pull changes from one of the remote repository:
    ```bash
    git pull staging master # git pull <remote-origin> <branch-to-pull>
    ```
- To push changes to one of the remote repository:
    ```bash
    git push production release_2 # git push <remote-origin> <branch-to-push>
    ```

##### :tada: And that was it, hope this post helped you prime yourself for Git Repositories.

:speech_balloon: In case you have any query, any suggestion to improve on, please file me an [issue](https://github.com/shiptwo/shiptwo.github.io/issues) noting the post URL.