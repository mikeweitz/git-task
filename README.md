Git Task
==========
A task-driven methodology for using git in marketing driven environments.

The two dominant git methodologies in practice are focused on either a software 'release' cycle (git flow), or a constant deployment cycle (git hub).  Both are geared towards companies that ship product. The core premise of this approach is attaining feature-independance: where task can be moved through review and into production independant of one another.  

Permanent environment branches are never worked on direcly.  Instead, individual task branches are worked on, then escalalted through the environments branches for various stages of approval.  Tasks are also independant of one another. If you're team is working on 5 independant features, you can pick and choose which features are merged into which environment.


## Issues this method attempts to address
 - Decouple code from the environemnt it lives on.
 - Improve ease of escalating individual features and fixes through qa / stage / production.
 - Reduce or remove new feature polution by basing new work off of production code
 - Resolve issues with environemnts falling out of sync.  If a task is edited while on stage, but not merged back down to qa and dev, those edits will be captured in the next task


## Questions moving forward
  - Should features be merged into master, or should master pull directly from Stage? This is mostly a question of how production code is reviewd. We want to deploy code that's been reviewd 'in browser'.
  - Can a code review system be implemented similar to a 'pull request' where develoeprs do not merge their own features into setage / master?


## Environment Branches
Each branch reflects a server environment
 - Master: Production code
 - Stage: Client review
 - QA: Internal QA team review
 - Dev: developer environment for testing new code 


## Task Branches
A task branch is any change to the codebase: New features, bugfixes, enhancements, etc...
 - Tasks are branched off of Master, so they should always inherit from live production code.  
 - Task branches are long-lived, but not premanent.  
 - Tasks branches are progressively merged into environment branches.
 - Any change in a task branch should merge into 
 - Since tasks branch off of master, any previous task changes that occured at later approval stages should be captured by subsequent tasks


## Basic Workflow
#### New features
Create a new task branch off of master.
Edit your code, committing as necessary.
When you're satisfied with your work, checkout Dev branch, and merge in the task branch.
If the code checks out, the task branch is then merged into QA for internal testing.
  QA logs issues, modify the code in the task branch and merged back into Dev and QA.
Once cleared and OK'd by stakeholders, the task branch can be merged into Stage.
  If QA logs issues on Stage, resolve in the task branch, and merged back into Dev, QA, and Stage.
After final signoff, the task branch is merged into Master.  The task branch can then safely be deleted from the repo.

#### Urgent bugfix
There's no difference in process - create the task, and progressively merge into environment branches.

![Branches in Git-Task](https://raw.githubusercontent.com/mikeweitz/git-task/master/images/diagram-01.jpg)

![Example Commit log in Git-Task](https://raw.githubusercontent.com/mikeweitz/git-task/master/images/diagram-02.jpg)

## To Do
 - Create 'git task' command files installable via NPM
    - git task start [name]: createa new branch off of master called task/[name], push to remote, and set tracking 
    - git task dev|qa|stage|finish: marge a task in it's respective destination branche(s): 
      - dev => dev
      - stage ==> dev and stage
      - qa => qa, stage, and dev
      - finish => master, qa, stage, and dev, then delete the task branch locally, and remove it from the remote


# Changelog
v 0.0.1
Draft concept for a git workflow that more closesly resembles the structure of work in agencies and non-product based tech teams


