---
layout: template
title: Intro to GitHub
sub_title: Git and GitHub 101, from a beginner user to another
---

# 0. Preface

## Disclaimer

**I am not an expert Git user by any means**. I am barely a beginner. I am simply a data scientist who found Git and GitHub confusing at first, had many things explained to them by actual computer scientists, and then tried to explain it to other data scientists. This is simply a summary of what little I know - it's not much, but it's enough to get started if you've never been properly taught how to use these systems.

## Git vs GitHub

While some use these two interchangeably, they are not. Git is *"a version control system that lets you manage and keep track of your source code history"*, while GitHub is *"a cloud-based hosting service that lets you manage Git repositories"* [(Source)](https://blog.devmountain.com/git-vs-github-whats-the-difference#:~:text=GitHub%E2%80%A6-,what's%20the%20difference%3F,help%20you%20better%20manage%20them.). In other words, Git is the core system that can be set up to manage code on any server, while GitHub is a service offered by a specific company to allow you to store your repositories for free, and give you a web interface to manage and share your code.

## Main benefits

In my brief time with Git and GitHub, I found there are two main benefits to using them for your projects:

- **Code history**: instead of having a hundred files labelled "code", "code2", "code_final", "code_final_final" etc. (you know you do it too), using Git to store your updates means you can keep working on the same file without fear of losing the old versions of it. If you screw something up and need to revert it, you can just refer to your repository and go back to the last working version of your project without much trouble.
- **Seamless collaboration**: if you're working with someone else on the same project, GitHub allows all parties to work on different parts of the same file without everyone overwriting each other's work. In fact, when an update is sent off to GitHub, only the bit you changed is updated, meaning that if someone else was working on another part of the file at the same time, their changes won't be lost in the same way they would be if you were just overwriting the shared file.

It's a similar issue as trying to have multiple people write a document together. What's easier, using something like Google Doc that lets everyone make their own changes, or having everyone work on their own version offline and overwrite a commonly shared file every once in a while? 

So whether you're working alone or with others, on an existing project or a new one, it's always good to use Git and put it on GitHub.

# 1. Initial setup

## Create your account & download Git

First of all, [make a GitHub account](https://github.com/) (*duh*). Then, unless you're planning on doing all your edits and updates through the web browser (*don't*), [download Git as well](https://git-scm.com/downloads). It should come with a graphic user interface version (Git GUI) and a terminal version (Git Bash): this tutorial is for using **Git Bash**, which in my opinion is less confusing and probably closer to what you would be asked to use in a more professional setting (if not an IDE, as mentioned in section 5).

## Set up your SSH key

Then, you'll have to set up an SSH key, which in my opinion is the most annoying part but at least you'll only have to do that once per machine you intend to use. This is a **S**ecure **SH**ell key that authorises your machine to interact with your GitHub repos.

(Following steps adapted from [this GitHub tutorial](https://docs.github.com/en/free-pro-team@latest/github/authenticating-to-github/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent#generating-a-new-ssh-key))

1. Open Git Bash, create a new SSH key using this command:

   ```ssh-keygen -t rsa -b 4096 -C "<your github email>"```

2. When asked to *"Enter a file in which to save the key"*, just press Enter, it will use the default file location.
3. When asked for a password, you can either put one (you will be asked to type it every time you're doing something major like pushing to or pulling from the repo), or leave it empty if you don't want one. It's ok to not have one - I have one and I regret it.
4. Start the ssh-agent in the background with this command:

    ```eval $(ssh-agent -s)```
5. Then add your SSH key to the ssh-agent with this commad (will only work if you didn't rename your key something but I haven't even said how to do that so you should be fine):
   
   ```ssh-add ~/.ssh/id_rsa```
6. Copy the key to your clipboard using the command below, or find the .ssh hidden folder, open id_rsa.pub with notepad, and manually copy all of its contents.

    ```clip < ~/.ssh/id_rsa.pub```
7. Finally, [go in your GitHub settings, under SSH and GPG keys](https://github.com/settings/ssh/new) and paste the key in the Key box. Save, and *yay*, you're done!

Now your machine is authorised to communicate with your GitHub account, and everything gets easier from now on (*or does it?*).

# 2. Repository setup

There are two ways to start a new repository:

## Clone an existing repository (creates a new folder)

This is probably what you will find yourself doing most often if you're using Git in a professional context, but it also works if you're working on your own.

0. If the repository you want doesn't already exist (i.e. it's not someone else's), create it by going on your GitHub repositories and [starting a new one](https://github.com/new).
1. Find the repository's URL: if you created the repository, you'll be provided it straight away after giving it a name. If you are already past the initial creation page, or you're looking to clone someone else's repo, find the Code button on the main page, and copy the URL provided under SSH ([see my own repo as an example](https://github.com/alepoptosis/alepoptosis.github.io))
2. In Git Bash, navigate to the directory you want the new folder to be in. In Windows, you can also use the File Explorer, right click on an empty space, and click "Git Bash Here" to make it quicker. Then use the following command:

    ```git clone <repo URL>```

And that's it! You will now have a new folder containing all that the repo contained, and you can push to and pull from it, provided you're the owner or a collaborator.

## Initialise a new repository (from existing folder)

If you already have a folder with a project that you would like to put on GitHub, this is another way to initialise a repository.

1. Create a new repository for it [here](https://github.com/new), like in step 0 above.
2. Navigate to the folder using either Git Bash or Git Bash Here, and run a command to initialise the folder as a Git repository:

    ```git init```
3. Finally, link the folder to the GitHub repository you created in step 1 using this command:

    ```git remote add origin <repo URL>```

And you're set! Again, provided you have the right permissions, that should be enough to get you started.

## .gitignore

More often than not, you won't want everything in your local repository folder to get synchronised with the GitHub repository, and the way to prevent that is to set up a .gitignore file (that's the whole file name, not an extension, it literally needs to be called ```.gitignore```). 

This file sits in your main repository folder, and is filled with rules about which files should be tracked and which ones should be ignored (hence the name). Each file specifies a pattern, and comments can be left to make sure you remember why the heck you did that three months ago.

It's a bad idea for me to try and cover even a fraction of what you can do in a .gitignore file, so [here's the documentation](https://git-scm.com/docs/gitignore), and below I will put an example from one of my repositories. In a professional setting, however, it's rare you'll have to fiddle with this much.

Example: in the code for my dissertation model, I was producing a lot of files like plots, scripts, and csvs that I didn't really need to track, as they would have just cluttered the repo. So my .gitignore file looked like this:

`````````
# ignore everything
*
# but descend into subfolders
!*/
# and whitelist these files
!model.nlogo
!variables.md
!TODO.md
!condor.sub
!experiments.md
!past_results/**
.Rproj.user
!datavis/base_vis.R
!datavis/vary_vis.R
!datavis/metrics_vis.R
!datavis/datavis.Rproj
!datavis/results/**
`````````

Basically, I told github to ignore every file with the initial asterisk, which matches any pattern, and then specified which files to include. If you're going to have to track a lot of files, however, this is going to be a pain so I suggest not ignoring everything.

# 3. Git basics: pull, add, commit, push

Once the repo is set up both on your machine's Git and on GitHub, you'll have to open the Git Bash console in your repository folder in order to interact with it (download new changes, submit your edits etc.).

## git pull

```git pull``` simply downloads (pulls) any change that may have been submitted by another user or machine, and updates your local files so that you can work on their newest version. 

If you're working alone, you'll rarely use this command, but if someone else is editing the code and/or you make some changes to your repo from the web browser, you'll need to do this before you can submit any new updates of your own.

**Note**: if you've made changes to one of your files and are worried that pulling will overwrite them - *don't*! They won't be lost unless the changes you're pulling directly affect your edits, in which case there will be a **merge conflict** that has to be manually resolved.

## git add

So you've made changes to your local file, you've completed a task or you're done for the day or whatever, and so it's time to send them off to GitHub. First thing you do is ```git add```.

The simplest thing to do, and what you'll want to do most times, is ```git add .```, which simply checks every file in your repository and looks for changes. However, if you made changes to multiple files but only want to update one, you can specify the file with ```git add <file name>```.

## git commit

Once you've added the files to be picked up by git, you will commit them using ```git commit -m "<commit message here>"```. If you don't include -m and a string message, a very annoying text editor will pop up which is a pain to exit so be careful. 

The commit message should be short to medium length, and explain the changes you made with the latest edit. Try and make it as clear as possible. Once you added the files, you should commit them straight away.

## git push

The classic meme-worthy command, ```git push``` actually sends off your commits to your GitHub, and you will be able to see them on the website usually mere seconds after you've pressed enter.

**You don't have to push every time you commit.** You can, and there's nothing wrong with that, but there is no need to: you can commit as much as you want without pushing, and all the commits will be pushed together once you run ```git push``` in the Git Bash terminal.

What I tend to do is commit every time I finish a task, and push when I go off for lunch or finish work for the day.

# 4. Branches and pull requests

Another handy feature of Git repositories are branches: I like to think of these are parallel universes for the project, which all start with the basis, but then branch off into different directions.

So far, if you followed this guide, you will have been working on the default repository branch, called ```master```. You can make another branch the default if you wish, but many would advise against it (naming conventions, yada yada). The default master branch will usually contain the latest stable/working version of your project.

However, we've all had that idea, especially when working on code, that you feel will either be a genius solution to all your problems, or irreversibly screw everything up. Without Git, you'd probably make a copy of the file to be safe, just in case, but with Git, you can simply make a new branch and screw that one up instead!

When a branch is created off of master, at first they're exactly the same, so you can edit any file in the branch without fear of not being able to revert it. Then, once you're sure the new changes work, you can merge the branch with master though a **pull request**, or scrap it if your idea was crap after all.

## Create a new branch

This can be done on the GitHub website by going to the main page of your repository and clicking on ```master``` in the top-right corner, and simply typing the new branch name in the text box that appears there.

If you'd rather do this in Git Bash, simply type ```git branch <branch-name>```.

## Change to another branch

Once you created a branch, make sure that the right changes happen to the right branches by selecting the one you need with ```git checkout <branch-name>```. Once you switch to a different branch, your local version of the repository will automatically change if necessary, without you needing to ```git pull``` (unless someone else has been working on the branch you're switching to while you were elsewhere).

You can also create a new branch and switch to it at the same time in Git Bash using ```git checkout -b <branch-name>```.

## Pull requests and merging

If the changes made in a branch are good enough to make it into the working version of your project, you can easily merge those changes with whatever is going on in master by initiating a **pull request**. This will literally be a request for master to pull the changes found in another branch, effectively merging them if no conflicts occur between the two. Usually this shouldn't happen, unless master has had edits of its own.

This is very easy to do on the GitHub website:

1. Click on the branch symbol indicating how many branches there are in your repository to be taken to the full list of branches.
2. Next to each branch, there will be a button to initiate a **pull request**.
3. The next page you allow you to specify which branch you're merging into which other, and it will show you a handy list of all the differences between them.
4. Once you confirm the creation of the pull request, you will be taken to a page where you can merge the two, and add a comment and a description to the merge. Your repository also has a dedicated pull requests tab where you can see all the active ones.
5. Once you're done, you can freely delete the branch you just merged.

Of course, this can be done in Git Bash as well using ```git checkout master``` to move back to the master branch (or whichever branch you want to merge the new branch into), and then ```git merge <branch-name>```, but I personally prefer the web version. In case you don't, [here's some documentation](https://git-scm.com/book/en/v2/Git-Branching-Basic-Branching-and-Merging) on branching and merging in Git. It also contains a more in-depth explanation of how they work if you're feeling particularly curious.

# 5. Integrated Git functionality in IDEs

While using Git Bash is incredibly easy and it's good to know in case you're working on a project with weird IDEs, you should know that a lot of development environments have Git functionalities directly integrated within them.

One example of this that I use myself is Visual Studio Code. It automatically detects your .git folder when you open your project directory, and it allows you to easily see changes, compare file versions, write commits, push them, undo them, change branch etc. If you use a specific IDE a lot, it may be worth looking into whether it can make your life easier by sparing you having to deal with Git Bash.

Having a specific IDE with integrated Git functionality is also the norm for most professional settings, but I find that starting with something like Git Bash helps better understand what happens under the hood.

# Final words

I really enjoy Git and GitHub, even if I understand that I am barely scratching the surface of what I can do, and sometimes I find myself invoking Zeus to smite it all down when it doesn't do what I want it to. But like everything, it's a learning curve, and in the end I like the peace of mind of not only having a traceable history of my code,  but also a window in which to display it, and a backup in case I really end up yeeting my laptop out of a window sometime soon.

The nice thing, for me, is that GitHub doesn't have to be just for code! Since repositories can be used just as well when they're private, nothing stops you from using it to write a novel, keep a recipe book, have a website (such as the one you're reading this on right now), and so on and so forth. It's a simple, accessible way of keeping your projects in check that can be as complicated as you need it to be.

I hope this helped, and feel free to contact me at [@alepoptosis](https://twitter.com/alepoptosis) on twitter if you find any mistakes and/or need any clarirication!



