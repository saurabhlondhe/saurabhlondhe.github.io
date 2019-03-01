---
layout: post
title:  "Let's start with git"
date:   2019-03-01
desc: "python devolopers tricks and tricks"
keywords: "git,git bash,master,gh-pages,website,blog"
categories: [Linux,Project]
tags: [open source,git,git bash,]
icon: icon-git
---
# An intro git for Beginners 
### Let's talk little bit about why git?
The same guy who created a 'Linux Operating System' Linus Torvalds also created git for Linux kernel development.

While working in a group project we need to keep our code from where other team members can easily access it. keeping them centrally is a good idea but what if someone deleted it by mistakenly. That won't happen but the location where we have kept our code becomes the backbone of our system. If it gets down then we are down. So keeping them centrally may lead to some disasters and solution is to Keep them distributed.

---

### Install git:
The first two things you'll want to do are install git and create a free GitHub account.

-   Installing on Linux
    
    If you are Fedora guy
    ```
    sudo dnf install git-all
    ```

    elif you are debian/ubuntu guy
    ```
    sudo apt install git-all
    ```
    else have a look [here](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git)

-   Installing on Windows

    No commands for Windows so get installer [here](https://git-scm.com/download/win)

---

### Initial configurations

        ```
        $ git config --global user.name "YOUR NAME"

        $ git config --global user.email "YOUR EMAIL"
        ```
### Create local repository

-   Make a folder for your project 

        ```
        $ mkdir testProject
        ```

-   naviagate into folder

        ```
        $ cd testProject/
        ```
    
-   To initialize a git repository in the root of the folder, run the ```git init``` command

        ```
        $ git init
        Initialized empty Git repository in C:/Users/Saurabh Londhe/github/testProject/.git/
        ```

-   git has created a hidden folder in your working directory as ```.git```
    
-   This git folder will have these folders
        ```
        ├───hooks
        ├───info
        ├───objects
        │   ├───info
        │   └───pack
        └───refs
            ├───heads
            └───tags
        ```


### Working with exsisting repo

        ```
        git clone "URL" foldername 
        ```


### Add files into new repo


-   Then you can commit files in that directory into the repo.

        ```
        $ touch test.txt        #creats a file
        ```

        ```
        $ git status
        On branch master

        No commits yet

        Untracked files:
        (use "git add <file>..." to include in what will be committed)

                test.txt

        nothing added to commit but untracked files present (use "git add" to track)

        ```

-   ```Untracked files``` these files are newly created and that need to add using  ```git add 'filename'```

-   the command ```git add``` will add this file into staging area.

        ```
        $ git add test.txt
        ```


    ![Staging Area](/static/assets/img/blog/start_git/staging_area.png)


        ```
        $ git commit -m "message"
        [master (root-commit) 7dbacf2] message
        1 file changed, 0 insertions(+), 0 deletions(-)
        create mode 100644 test.txt

        ```

### Push your commited changes to remote repository

-   ```git push``` will push local commited chnages to remote repository
    
-   we can  can specify branch name to push the changes
        ```
        git push origin <branch name>
        ```

Till now we have created a repo, added content, committed it and successfully pushed to the remote server.

If you still stuck somewhere use following cheat sheet :)

![Staging Area](/static/assets/img/blog/start_git/git-cheatsheet-simple.jpg)

---

Try using git daily becasue more you use git, the more comfortable you'll.

Git for pro will be available soon.