# Big Ideas Lab Git Instruction and Best Practices


## Table of Contents
1. [Why?](#why?)
2. [General Workflow](#general-workflow)
    1. [Setting up SSH key](#setting-up-ssh)
    2. [Cloning the Project](#clone-the-project)
    3. [During Development](#development)
    4. [Rebasing and Teamwork](#rebasing)
    5. [Best Practices](#best-practices)
3. [Structuring your README](#structuring-readme)
4. [Code Styling](#code-styling)

## Why?
There are many reasons why version control systems are critical to the success of most software and digital projects. As data scientists and researchers, version control systems such as Git serves similar purposes as a traditional lab notebook - **track experiments, enhance teamwork, improve reproducability, and safeguard our main intellectual output.** 

### For Yourself
One major benefit of version control is to keep a working copy of your code at different times.

**Scenario 1:** You have a working copy of your current codebase 👍. You decided to make some changes in hope to improve your results. After couple hours of work, you find yourself creating more problems then improvements. And what's even worse? You forgot how to get back to your working copy 🫠! If you commited your working copy previously, this will be no problem at all as you can just revert back to that commit.
> Commiting frequently also allows you to have more confidence in trying new things, since you won't be worried about corrupting your current progress.


**Scenario 2:** If someone were to ask you to explain your thought process behind a piece of code that you haven't seen in a while, it is likely that you also forgot what exactly happened 🤔. Frequent commits along with good commit messages can help you remember what you worked on. 

**Scenario 3:** You might be asked about what you have worked on this week 🙀. Your commit history is the easiest way to show your track record for specific tasks. It is also a easy medium for the reviewer to digest. 

### For Your Team

**Scenario 1:** Many times you need to view the commit history of a project in order to understand what tasks has been previouly completed, so that you don't reinventing the wheel. This is also applicable for understanding what has been attemped in specific tasks.

**Scenario 2:** A well structured README can help bring your team on the same page. All members can agree on the usage of different scripts, the virtual envrionemnt, the variable naming convention, and more...

**Scenario 3:** Using feature branches allows you to better share tasks across your team without worrying too much about dependencies and code conflicts. It also provides you a chance to review intermediate code and results before they are included in the final version.

### For the Community

A well structure repository allow readers to easily understand your throught process and faciliatates reproducible research. 

## General Workflow
The instructions below were adopted from a standard feature branch workflow that you can read more about in this [article](https://www.atlassian.com/git/tutorials/comparing-workflows/feature-branch-workflow). This workflow is adjusted to work with the typical team size and collaboration needs in the lab, but feel free to adopt a variation if it fits your project goals better. 

### Term Definitions
* **Main Branch** | Central branch that contains the latest bug-free version of your software.
* **Feature Branches** | Contains the feature that you are currently working on.

### Setting up SSH
SSH is the secure and default way that we will access and write data to the GitHub repository. If you don't have a SSH key set up on your machine, you can find detailed instructions in the following pages:

1. [Generating a SSH key](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent)
2. [Adding SSH key to GitHub](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/adding-a-new-ssh-key-to-your-github-account)
3. [Test your connection](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/testing-your-ssh-connection)

### Clone the Project
1. On your local machine, navigate to the directory where you want to store the project. 
> **Note:** Make sure that your parent directory does not have git initiated from another project. A good separation from your other tasks are recommended.
2. In that directory, clone the repository with `git clone <project-url>`.

3. Follow setup instructions on the project specific README.
> **Note:** This typically includes setting up virtual environments and project specific packages. 

### Development
1. Check your current branch with `git branch`.
> **Note:** If this is your first time cloning the project, you should be on the main branch. 
2. Check whether you are up to date with the remote branch with `git status`.
3. Create your feature branch with `git branch <feature-name>`.
4. Checkout to your feature branch with `git checkout <feature-name>`.
5. Once you finish a modular section of your code, add your files to the staging area with `git add <filename>`.
6. Commit your changes with `git commit -m "<commit message>"`.
7. After every working session, push your code to the remote repository with `git push`.
> **Note:** If this is your first time pushing your feature branch to the remote, you might need to setup the remote repository. Use `git push -u origin <feature-name>` instead. 
8. Once you are fully completed with your feature branch, start a pull request and select a reviewer. 

### Rebasing
Whenever a feature branch from your teammate was merged into main through a pull request, you will have to rebase the feature brances you are currently working on. 

<p align="center">
<img src="https://i.stack.imgur.com/VmHt6.png" width="400px"></img>
</p>

1. To perform rebase, run the following command on your feature branch `git pull --rebase origin main`.
2. If there are merge conflicts, resolve them and then re-stage your files with `git add <filename>`.
3. Run `git rebase --continue` to complete rebase (Note: Do NOT run `git commit` during rebasing).
4. When rebase is completed, run `git push --force-with-lease` to push your local branch to remote. (Note: NEVER run `git push --force` or `git push --force-with-lease` on the main branch)

## Best Practices

### Feature Branch Naming
Feature branch names should describe the main feature that you are adding and are relatively short (< 4 words). Words should be lower-case and separated by `-`. 

> **Note:** If you find that you can't think of a feature name for your functionality, this is a sign that you might want to split your functionality into smaller, simpler features. 

* Examples:
    - `svm-evaluation`
    - `peak-detection`
    - `update-readme`
    - `target-class-histogram`
* Counter Examples:
    - `Dr.R_Auth`
    - `RandomForest`
    - `my-entire-project`

### Commiting
Your should commit frequently. Typically a commit can happen after you finish a modular piece of code or after a working session. A good way to know when to commit is to see whether you can summarize what you did in a sentence. 

Your commits should include a descriptive commit message (1-2 sentences) that helps to track what you have completed both for the team and for yourself. 

* Examples:
    * "Constructed the forward method for the baseline CNN model" 
    * "Applied fourier transform on signal segments and stored the results"
    * "Created a text field component and added basic styling"
* Counter Examples:
    * "pd.read_csv()"
    * "Wrote some code yeah" 

### Merging Your Features
* Selected a reviewer in your pull request so that no unreviewed code gets merged into the main branch. 
* Remember to send an announcement to your team after your feature branch is merged. This way your teammates will know when to rebase their branches. 

### Merge Conflicts
The easiest way to deal with merge conflicts are not to create them. This means communicating well with your fellow teammates so that you are not editing the same scope of program in your respective feature branches. Resolving merge conflicts are typically very situational, so if you encounter a situation not described below, please contact us!

## Structuring README

## Code Styling