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

## Browsing History


## Rewriting History


## Branching


## Collaboration


## Check Understanding


## Additional Resources

