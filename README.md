Git Task
==========
A task-driven methodology for using git in marketing driven environments.

The core premise is that features are more important than environments.  Individual task branches can be escalalted through the permanent environments branches independant of one another. If you're team is working on 5 independant features, you can pick and choose which features are merged into which environment.


# Changelog
v 0.0.1
Draft concept for a git workflow that more closesly resembles the structure of work in agencies and non-software based tech teams


## Issues this method attempts to address
 - Decouple code from the environemnt it lives on.
 - Improve ease of escalating individual features and fixes through qa / stage / production.
 - Reduce or remove new feature polution by basing new work off of production code
 - Resolve issues with environemnts falling out of sync.  If a task is edited while on stage, but not merged back down to qa and dev, those edits will be captured in the next task


## Environment Branches
Each branch reflects a server environment
 - Master: The live production code
 - Stage: Client review
 - QA: Internal QA team review
 - Dev: developer environment for testing new code 


## Task Branches
A task can be any change to the codebase: New features, bugfixes, enhancements, etc...
 - Tasks are branched off of Master, so they should always inherit from live production code.  
 - Task branches are long-lived, but not premanent.  
 - Tasks branches are progressively merged into environment branches.
 - Any change in a task branch should merge into 
 - Since tasks branch off of master, any previous task changes that occured at later approval stages should be captured by subsequent tasks


## Basic Workflow
Create a new task branch off of master.
Edit your code, committing as necessary.
When you're satisfied with your work, checkout Dev branch, and merge in the task branch.
If the code checks out, the task branch is then merged into QA for internal testing.
  QA logs issues, modify the code in the task branch and merged back into Dev and QA.
Once cleared and OK'd by stakeholders, the task branch can be merged into Stage.
  If QA logs issues on Stage, resolve in the task branch, and merged back into Dev, QA, and Stage.
After final signoff, the task branch is merged into Master.  The task branch can then safely be deleted from the repo.


![Branches in Git-Task](https://raw.githubusercontent.com/mikeweitz/git-task/master/images/diagram-01.jpg)