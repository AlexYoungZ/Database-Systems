# Project 0. Setting up your development environment

Welcome to  CS  186 Spring 2018!  In  this  first  project,  we  will  help  you  set  up  the  development  environment  that  you  will  use throughout the course. Please take this project  seriously—an  improper  setup  can  lead  to subtle bugs in your future  work  in  the  class.   

## Setting  up  your  course  accounts  

This course will use EECS instructional class accounts to manage grades.  All students can create their CS 186 course account at http://inst.eecs.berkeley.edu/webacct.  Let  us  know  if you have  any  issues  creating  an  account.  These usernames  are  of  the  form  **cs186-xyz**  or  **cs286-xyz**  and  you  will  be  given a temporary password. This sets your EECS instructional  account.  
  
We will be using github to serve and manage projects. Please sign up for a github account if you haven’t already: https://github.com.   
  
Git is a free and open source  version  control  software  package.  We  will  be  using  git  quite  a  bit  in  this  course  to  manage projects and homeworks. If  you  are  unfamiliar  with  git,  please  follow  the  tutorial  at:  https://try.github.io  
  
Once you have a EECS inst account and a Github account  follow the  instructions  in  the  following  link.  Remember  to  only enter your three letter account name  ( i.e., what  comes  after the cs186-): https://registration-sp18.herokuapp.com/.  
  
To confirm that your github accounts have been properly set up, first login to github. You should be able to visit https://github.com/berkeley-cs186/<last_three_letters_inst_account>  ( e.g., https://github.com/berkeley-cs186/xyz) . Do not initialize the repository through github! This repository is owned by the organization  berkeley-cs186,  but  you  will  have write  access  to  it.   
  
This is a good checkpoint--please let us know on Piazza ASAP if there are any problems here.  

## Setting  up  the  course  virtual  machine  

VirtualBox is a general-purpose full virtualizer for x86 hardware, targeted at server, desktop and embedded use.  Download and install VirtualBox from:  https://www.virtualbox.org/wiki/Downloads.  The  virtualbox  website  has  installation instructions  for Windows, Macos, and Linux.  
  
Then, download the course VM from the course Google Drive: https://drive.google.com/drive/u/0/folders/1daZEGfIz02w7nExOHvmIEtRgDcjAFBrT 
  
Open VirtualBox and click **File > Import Appliance**. Click on the folder icon and select  the path of the file that you just downloaded.  The  initialization  should  take  about  5-10 mins.   
  
Once the VM is imported, double click on it to power it on. You should be greeted with a terminal and prompted to log in. The  username  and  password  are  both  **vagrant**.  

Next, click  on the terminal icon at the bottom of the desktop.  You will now load your project repository. First, configure your  git  account  by  copying  the  following  commands  into  the  terminal.  Replace <your_email>  and <your_name> with your  email  and  your  name.  

```  
$ git config --global user.email "<your_email>"
$ git config --global user.name "<your_name>"
```

**If you have done the following before and are setting up on a new machine (or again on the same machine), DO NOT RUN THE FOLLOWING AGAIN.** Doing so will reset your repository on GitHub to this course repo and you will delete any code you have on GitHub (including the stuff to be graded). Skip the rest of this section and jump straight to *First Commit* to clone your repo.

Then, you will  clone a “bare” repository in your home directory:  
  
```  
$ cd $HOME  
$ git clone --bare https://github.com/berkeley-cs186/course.git 	  
```  

Enter the “bare” repository:  
 
```  
$ cd course.git  
```
  
Mirror this repository to yours (last three letters). Again, do ***not*** run this more than once.
  
```  
$ git push --mirror https://github.com/berkeley-cs186/<your_inst_account>.git 	  
```
  
Once this is done, you can leave the course.git directory:  
```
$ cd ..
```  
  
You are done! If you visit https://github.com/berkeley-cs186/< your_inst_account>, you will see the basic project skeleton.   

# First  Commit  

Now, we will walk you through your first commit. This will get you familiar with the procedure used to submit homework assignments.  First,  clone  the  newly  created  course  repository:   

```  
$  git clone https://github.com/berkeley-cs186/<your_inst_account>.git course-projects  
``` 

Enter the newly created repository:  

``` 	
$ cd course-projects  	
```
  
For every homework  assignment  and  project,  you  will  create  a new branch that identifies the project. This keeps the version  control  consistent  and  keeps  a  paper  trail of your submissions throughout the semester.  The course staff will use the  master  branch  of  your  repository  to  push  project  infrastructure  updates  and  solutions.  **MODIFY  THE MASTER BRANCH  AT  YOUR  OWN  RISK.**   
  
Before each starting each project run:  

```  
$ git checkout master  
$ git pull  
```

After doing do, create a new branch. Course staff will give you the name of this branch in the  project  description.  For  this homework it is **hw0**:  

```  
$ git checkout -b hw0  
```

In this repository, there  is  a  file hw0/hw0.sql . Open it  up  with  a  text  editor  and  modify  the  file.  Make  sure  to  remove  the TODO  comment. After you are done add this file and  commit  it  to  github:  

```  
$ git add hw0/hw0.sql  
$ git commit -m “my greatest commit”  
```  
**REMEMBER  TO  PUSH  YOUR  CHANGES  TO  GITHUB!!!**  

```  
$ git push origin hw0  
```

# Fill in your Information
Please fill in all of your information on the following Google Form so we can keep track of it for any future homework or grading related conflicts: https://docs.google.com/a/berkeley.edu/forms/d/1DnkCL6_hDFVt1IHw72kS2jFuQDmSzEDZPCOeup_C8ac/edit?usp=drive_web.

# Advanced  Tips  

## Using Docker  

If you are using docker you need to turn off Hyper-V   

## Editing files in the VM  

The  virtual  machine  is running Ubuntu 14.04 with the Xfce  desktop  environment.  The  virtual  machine  ships  with PostgreSQL  9.6 ,  Java  8  ( installed  in ~/jdk1.8.0_131),  Eclipse  Neon ( installed  in ~/eclipse) ,  and  the  community version of IntelliJ IDEA  ( installed in ~/idea-IC-172.3757.52). You can write code  in  the  virtual   machine (recommended) or on your local machine (not recommended), but all code will be tested in the VM.  
  
## Vim Tutorial  

Vim is a lightweight text editor  built  to  make creating and  changing  any  kind of text  very  efficient.  It  is  included  as  
"vi"  with most UNIX systems and with Apple  OS  X.  For  a  tutorial,  visit: http://www.openvim.com/  
  

