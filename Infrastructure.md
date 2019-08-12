# Course Infrastructure FAQ/Tutorial
This document provides a basic overview of the course infrastructure and responses 
to some frequently asked questions.

# `git` and GitHub
`git` is a *version control* system, helping you track different versions of
your code, synchronize them across different machines, and collaborate with
others. [GitHub](https://github.com) is a site which supports this system,
hosting it as a service. We will be using both `git` and GitHub to submit assignments in this course. If
you don't know much about `git`, we *strongly recommend* you to familiarize
yourself with this system; you'll be spending a lot of time with it!

There are many guides to using `git` online -
[here](http://git-scm.com/book/en/v1/Getting-Started) is a great one to read.

## Repositories
The purpose of Git is to manage a project, or a set of files, as they change over time. Git stores this information in a data structure called a repository. Repositories can be local (stored in a folder on your machine) or remote (stored in github). `git` provides a set of utilities to synchronize these repositories. There are three main repositories that you should care about: (1) your local `course-projects` repository, (2) your github repository tied to your instructional account `berkeley-cs186/xyz.git`, and (3) the staff course respository `berkeley-cs186/course.git`. Your local repository houses the project files locally on your machine. Your instructional account repository is how you share your homework solutions with course staff. The staff course repository is where course staff stage the appropriate homework skeleton code and tests. 

## Common Tasks
Homework 0 is designed to *initialize* these repositories. Be careful about re-running those instructions as it may lead to overwriting existing data. These following tasks assume that you have already successfully completed homework 0. It also assumes that your instructional account name is `xyz`.

### Creating a New Local Repository
These steps create a new local repository. The basic tool that we will use is `git-clone`, which clones a repository into a newly created directory, creates remote-tracking branches for each branch in the cloned repository, and creates and checks out an initial branch that is forked from the cloned repository's currently active branch. You will use `git-clone` to make a copy of *your instructional github repository* and then synchronize this copy with the staff repository to keep it up-to-date.

First, open your terminal and at the prompt type in the following command:
```
$ ls -ld course-projects
```
This command tests to see if you already have a `course-projects` repository. If you do the result of the command will look something like this:
```
drwxr-xr-x  6 vagrant  vagrant  204 Sep  6 11:51 course-projects
```
If you have a `course-projects` directory, you should first rename it up before proceeding:
```
$ mv course-projects course-projects.backup
```
You can still access your old files through the `course-projects.backup` folder.

Next, once you have confirmed that, you can clone the repository from github:
```
$ git clone https://github.com/berkeley-cs186/<xyz>.git course-projects
```
This creates a local repository in a new folder called `course-projects` that is a clone of your instructional repository.

The next step is to synchronize this repository with the staff repository. First, enter the newly created directory:
```
$ cd course-projects
```
Then, run the following command: 
```
$ git remote add staff https://github.com/berkeley-cs186/course.git
```
This adds a reference to the staff course repository. Next, you need to fetch the files from the staff repository:
```
$ git fetch staff master
```
Finally, you have to merge the staff repository with your local repository:
```
$ git merge staff/master master
```

### Branching
A branch in `git` is simply a pointer to a version of the repository. Branches allow you to setup a working copy that you will modify, while keeping a pristine copy of the course code that can be easily synchronized with the staff repository. 

All of these commands will require first entering your local repository:
```
$ cd course-projects
```

To see all of the branches in your local repository, run:
```
$ git branch --list
```

Your *current* branch should be listed in green. To switch branches, run:
```
$ git checkout <branch_name>
```

To create a new branch and switch to it, run:
```
$ git checkout -b <new_branch_name>
```

Before every homework assignment, you should create a new branch based off the master branch in the repository:
```
$ git checkout master
$ git checkout -b <hwN>
```

### Commiting and Pushing
Once you create a branch for your homework assignment, then you can begin to edit the files. The purpose of `git` is to provide version control so you should quickly and frequently commit your changes to the repository. To do so, first run the command:
```
$ git add <filename>
```
This stages the designated file for a commit, then run:
```
$ git commit -m <string describing the commit>
```
*Note: * this only commits the code to the local repository. This helps you with version control locally but will not submit your results.

Committing frequently is useful because it allows you to rollback unwanted or undesired changes. You can look up previous commits by running:
```
$ git log --abbrev-commit
```
Each commit is identified a 7 letter hash string. Running the command:
```
$ git reset <hash>
```
will reset your local repository to that commit. You may be tempted to use the option `--hard`, please be careful doing so and read through the git tutorial above to understand what it does.

Every so often you should synchronize your local code with your instructional github repository. This is how course staff know that you have completed your assignment. First, commit all uncommitted code. Then, run:
```
$ git push origin <hwN>
```
This pushes your currently commited code on your current homework branch to the course repository. 
To confirm that your code has properly pushed, you can visit the github web interface at https://github.com/berkeley-cs186/xyz. 
Pushing frequently is a good idea. This backs up your files to your instructional github account. For example, if your VM gets corrupted or fails, you can still recover your latest pushed copy.

# Course Virtual Machine
VirtualBox is a general-purpose full virtualizer for x86 hardware, targeted at server, desktop and embedded use. Download and install VirtualBox from: <https://www.virtualbox.org/wiki/Downloads>. The virtualbox website has installation instructions for Windows, Macos, and Linux. The course staff created a virtual machine and have exported as a .ova file. This file contains all the information needed to create the same instance on your computer.

## Common Problems
1. *Virtual Machine will not boot due to virtualization settings after installation.* A common problem that many students have is that the VM will note boot due to disabled BIOS options. To fix this, restart your laptop and enter the BIOS configuration (usually by pressing some key during the boot process). Then, find a setting that looks like "Intel Virtualization" or something similar. Make sure this setting is enabled. Save and reboot your machine. Once booted, open VirtualBox and edit the VM configuration make sure you change the operating system to Ubuntu 64-bit.

2. *Virtual Network disconnected* If you are moving between wifi hotspots (e.g., in Soda hall) sometimes the virtual machines network connection will fail. If this happens, restart the virtual machine. Please remember to save your files!

3. *How to shrink down a bloated VMDK.* This post describes how to shrink a bloated virtual machine that is taking up too much space <https://www.howtoforge.com/how-to-shrink-vmware-virtual-disk-files-vmdk>.

4. *How to avoid VMDK corruption* The limit for the disk size of your virtual machine is very large: 40GB.  You may not actually have 40 GB available on your machine. Make sure that you don't use up more space than is on your machine. The best solution is to push to your instructional repository as frequently as possible.

