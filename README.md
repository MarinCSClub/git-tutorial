# Git Tutorial

## What is Git?
Git is the most popular version control system in the world. A version control system records the changes made to our code over time in a form of a database called a repository. We can look at the project history to see who has made what changes. Git also allows us to easily revert our project back to an earlier state if things go wrong.

Git is what's called a distributed version control system. This means that when collaborating, each team member will have a copy of the project with its full history on their computer. Even if the server storing or projects in the cloud were to go down, we can still synchronize our work with others.

Because of its popularity in the industry, Git is an essential skill to have as a software developer. We should be able to effectively use it to track project history and collaborate with others.

## Git vs GitHub
Sometimes there is confusion with the difference between Git and GitHub. Essentially, Git is the whole version control system that was described in the previous section, while GitHub is just a hosting service for our Git repositories. You can think of it kind of like Google Drive or Dropbox for code. GitHub does, however, provide us with some very useful tools for collaborating on projects which we'll get into later.

## Join GitHub
If you don't already have a GitHub account, you should [create one](https://github.com/join) before we start.

## Instillation
First we should check if Git already installed by running the command in your terminal:
```
git --version
```
If you see a version number, Git is already installed and you can skip the next steps about instillation.

### How to install:
1. Download the Git installer from the [downloads page](https://git-scm.com/downloads).
2. Run the installer on your computer, allowing it the necessary permissions.
3. Select the default installation settings all the way through the instillation process, except for the default editor which you should select as Visual Studio Code.
4. Once complete, run the command above again to verify that Git installed successfully.

If you are on Windows, a new shell program called Git Bash will have install along with Git. You should use this as your shell program from now on.

## Configuring Git
Prior to working with Git, we should do a small amount of configuration. In order to let Git know who we are, which is displayed with any changes we make in the repository, we will use the following commands

Add your name:
```
git config --global user.name "<your name>"
```
Add your email:
```
git config --global user.email <your email>
```

## Your first repository
Let's first use the terminal to navigate to a directory where you want to store your first repository. You can do so with this command:
```
cd <directory>
```
It doesn't really matter where you put this, but I'd recommend creating a programming or repos folder somewhere that is easily accessible.

Inside of the directory where you will be storing your repositories, use the command
```
mkdir <folder name>
```
to create a folder for your first repository. Then, navigate into the new folder with the cd command.

### Initializing a repository

To initialize a repository in the current folder, run:
```
git init
```

We should now add some files to our project. You can add some content to a file at the same time as creating it like this:
```
echo hello > file1.txt
```
Let's use this command again to make a second file:
```
echo print("Hello world") > main.py
```

Now that we've added some new content to our repo, let's check the status of our working directory:
```
git status
```

You'll notice that both of the files that we just created are in red and listed as "untracked," which means that they have not yet been added to the staging area. The **staging area** is where we put files that will be a part of our next commit.

You can also add the -s flag ```git status -s``` to get a condensed version of the status.

### Staging files
We can add individual files to the staging area
```
git add <file name>
```
or we can add all files from our working directory
```
git add .
```

Let's use the latter command to add both of the files we just created to the staging area. You'll notice that if you run ```git status``` again, the files will now be in green and say that the changes are ready to be committed, which means that they are in the staging area. 

Now instead of creating a new file, let's modify an existing an existing one. We'll add onto file1:
```
echo world >> file1.txt
```

If you run ```git status``` once again, you will see that file1.txt will show up as modified. At this point, we have changes in our working directory that have not yet been added to the staging area. We can use ```git add .``` to add the changes to the staging area, and then all changes will be ready to commit.

### Committing Changes
We now have a snapshot of our changes in the staging area that we want to commit to permanently store them in our git repository. We can do this with the following command:
```
git commit -m "<description>"
```
Your description should be a message that describes what this snapshot represents.

#### Committing best practices:
- Try not to make your commits too big or too small.
- Commit often, but not excessively.
- Each commit should represent a logically separate feature.
- Use meaningful commit messages.

### Ignoring files
Sometimes there are files that we have stored locally that we don't want to save to a repository. These could be things such as build files, logs, dependencies, files with sensitive information, etc. We can tell Git to not include these types of files but putting their name or file extension in a file called ".gitignore". To create one, run the following command in the root of your repository:
```
touch .gitignore
```
You can add new files to .gitignore my editing the file in your text editor of choice or by appending to the file by piping the echo command:
```
echo <file name> >> .gitignore
```

If a file is already in the staging area before you add it to .gitignore, you will have to manually untrack it:
```
git rm -r --cached <file name>
```

### Connecting to a remote repository
We first need to [create a repository](https://github.com/new) on GitHub that we can establish a remote connection with.

Once you've done that, copy the https link to the repository. We will use that with the following command in the local repository we made on our computers:
```
git remote add origin <link to repo>
```

Now after we make sure we have committed all the changes we want to add to the remote repository, we can push those changes:
```
git push <remote name> <branch name>
```
The push command assumes origin for remote name and the current branch for branch name, so we can just use ```git push``` without the other arguments for now.

## Browsing History
In this section, we will be going over some useful commands for when you are browsing the history of your project.

It can be very useful to view a full history of our projects and get data about each commit. To do so, we can use the command
```
git log
```
This will display a detailed description of each commit which you can scroll though with the up / down arrows, got to the next page with space, or quit with q.

Much of the time, this much information all being displayed at once can be a bit overkill, so we will want a condensed version. We can do so with the --oneline flag. ```git log --oneline``` This is the version of the log command that you will likely be using most often.

If you'd like to view all the changes that were made in a specific commit, you can use the diff command:
```
git diff <commit id>
```
You can get the commit id from the oneline log.

It is also possible to get a list of all files that were changed using the diff command by using the --name-status flag: ```git diff --name-status```

If you end up needing to restore a deleted file, that is possible with the checkout command. This command on it's own will restore your working directory to a previous state, but we can use it to select just a single file that we want brought back. Here is the how you would do that:

First we want to find all commits that have touched the file we want restored. Once again, we will use the log command, but also pass the file name to it separated by --
```
git log --oneline -- <file name>
```
We now checkout the file from the most recent commit shown in that log
```
git checkout <commit id> <file name>
```
We can now commit the file just like we would any other changes.

If we end up needing to restore the whole project to a past commit, that is possible too. We can run
```
git reset --hard <commit id>
```
You should only do this if the history you are reverting has not been shared with others.

### * More information coming later *