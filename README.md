# Git Tutorial

## What is Git?


## Git vs GitHub


## Join GitHub
If you don't already have a GitHub account, you should [create one](https://github.com/join) before we start.

## Instillation
First we should check if Git already installed by running the command in your terminal:
```
git --version
```
If you see a version number, Git is already installed and you can skip the next steps about instillation.

### How to install:
1. Download Git from the [downloads page](https://git-scm.com/downloads).
2. Run the installer on your computer, allowing it the necessary permissions.
3. Select the default installation settings all the way through the instillation process, except for the default editor which you should select as Visual Studio Code.
4. Once complete, run the command above again to verify that Git installed successfully.

If you are on Windows, a new shell program called Git Bash will have install along with Git. You should use this as your shell program from now on.

## Configuring Git
Prior to working with Git, we should do a small amount of configuration. In order to let Git know who we are, which is dispalyed with any changes we make in the repository, we will use the following commands

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
It doesn't really matter where you put this, but I'd reccommend reating a programming or repos somewhere that is easily accessable.

Inside of the directory where you will be storing your repositories, use the command
```
mkdir <folder name>
```
to create a folder for your first repository. Then, navigate into the new folder with the cd command.

To intitialzie a repository in the current folder, run
```
git init
```


## Browsing History


## Branching


## Collaboration


## Additional Resources

