# Git vs GitHub: Know the Difference

1. Git
    * A version control system (VCS) created by Linus Torvalds.
    * Tracks changes in your code locally.

    Allows you to:
    * Save versions (commits)
    Revert changes
    * Collaborate using branches and merges

    Works offline — no internet needed.

2. GitHub

    A cloud-based platform that hosts Git repositories.
    * Adds features like:
        Remote repository hosting
        Collaboration (pull requests, issues, comments)
        Project management tools
        Actions for automation (CI/CD)
        Owned by Microsoft since 2018
    Think of it as Git + social + cloud tools

In short:

Git is the engine. GitHub is the car with extra features, built around that engine.

# Git Configuration

1. Configuring git for the first time 

        $ git configure --global user.name "<enter your user name>
        $ git configure --global user.email "<enter your email here>

# General Git Features

1. Initializing Git

        $ git init

    Once you initialize Git in a folder, Git starts tracking it for changes. It creates a hidden directory (called .git) inside that folder to store all the information it needs to manage version history.

2. Staging files/Adding files to git repo

    Staged files are the ones that are prepared and ready to be committed to your project’s repository.

    * When you add files to a brand-new Git repository, they start out as untracked—meaning Git isn't monitoring them yet.  To start tracking these files, you need to stage them by adding them to the staging area.

        $ git add <filename with extension>

    Staging all the files in a folder

        $ git add --all 
        $ git add -A

    They stage:
    All new, modified, and deleted files in the entire working directory.
    They include changes in all subdirectories.

        $ git add .
    
    Stages new and modified files in the current directory and below.
    Does NOT stage deleted files outside the current directory.

    | Command         | New Files  | Modified Files | Deleted Files   | Scope                  |
    | --------------- | ---------  | -------------- | -------------   | ---------------------- |
    | `git add -A`    | ✅         | ✅              | ✅              | Entire project         |
    | `git add --all` | ✅         | ✅              | ✅              | Entire project         |
    | `git add .`     | ✅         | ✅              | ⚠️ (not all)    | Current directory down |

3. Git commit with stage

    Commits help record your progress and track changes as you develop your project. Each commit acts like a checkpoint or save point —a moment you can return to if you need to fix a bug or revisit a previous state of the project.
    It's important to include a clear commit message each time, so you know what changes were made and why.

        $ git commit -m <enter your message>

4. Git commit without stage

    when making minor changes, going through the staging area may feel unnecessary. In such cases, you can commit your changes directly, without staging them first.

        $ git commit -a -m <enter your message>

# Git Branching

    In Git, a branch is an independent version of your project. It lets you work on new features or fixes separately from the main branch (often called main or master).
    
    Branches help you develop and experiment without affecting the main project. Once you're done, you can merge your branch back into the main one.
    
    You can also switch between branches to work on different tasks without them interfering with each other.

1. Making a new branch

        $ git branch <name of branch>

2. Checking all available Branches

        $ git branch

3. Switching to other Branches

        $ git checkout <branch name>

4. Making a new branch and directly switching to it

        $ git checkout -b <branch name>

5. Deleting a Branch 

        $ git branch -d <branch name>

6. Merging two Branches

    It's recommended to switch to the master branch before merging any other branch into it. This ensures you're merging changes into the most up-to-date version of the main project.

        $git merge <branch name>


# Working with github

    First, create a GitHub account so you can make remote repositories.
    Then, create a new repository on GitHub, which will be used to upload files from your local project.
    
    * A local repository is the one stored on your own computer.
    * A remote repository is hosted on a remote server, like GitHub, GitLab, or Bitbucket.

<img src = "https://github.com/Pallavilathavadlamudi/Git-github/blob/main/Assets/githibrepo.png" >

1. Cloning a Repository from GitHub to Your Local Machine
    
    You can clone a forked (or any public) repository from GitHub to your local system.
    Cloning creates a complete copy of the repository, including its full commit history and version tracking.

    Get the Clone URL
    Go to the repository on GitHub, click the green “Code” button, and copy the URL provided. 

        $ git clone <copied-URL>
  
    Clone into a Custom Folder Name
    If you want to clone the repo into a folder with a specific name, use:

        $ git clone <copied-URL> <folder-name>

2. Push local repo to github

Connecting Your Local Repo to GitHub
        
    1. Copy the Repository URL
        After creating a new repository on GitHub, copy its URL.
        It will look something like this:
        https://github.com/Pallavilathavadlamudi/Git-github.git
    
    2. Link GitHub Repo to Local Project
        Use this command in your terminal (inside your project folder):

         $ git remote add origin <paste copied URL here>

    This tells Git that you're adding a remote repository named origin and linking it to your local project.

    3. Push Your Local Code to GitHub
        Now, push your local branch (usually master or main) to GitHub and set it as the default upstream branch:

        $ git push --set-upstream origin master
        $ git push 

    4. Check GitHub
        Go to your GitHub repository page — you’ll now see all your local files there!

    5. Pushing Changes After Initial Setup

        After the initial connection is done,

        1. Stage and Commit Your Changes

            $ git add .
            $ git commit -m "Your commit message"

        2. Push to GitHub

            $ git push origin

3. Pushing a New Branch to GitHub
    
        1. Create and Switch to a New Branch

            $ git checkout -b <branch-name>

        2. Check the Branch Status

            $ git status
        
        3. Commit Your Changes
            Commit all modified files in this branch with a message:
            
            $ git commit -a -m "Your commit message"

        4. Push the Branch to GitHub

            $ git push origin <branch-name>

4. Pull changes local repo from github 
 
    git pull is used to bring in the latest changes from a remote repository into your current local branch.
    It’s like doing both a fetch (to get updates) and a merge (to apply them) in one step.

    To pull updates from the remote repository (usually named origin), use:

        $ git pull origin

    This keeps your local project up to date with the latest changes from GitHub.

5. Pull a Branch from GitHub to Your Local Repository:

        1. Check Your Current Branch

            $ git branch

        2. View All Branches (Local + Remote)

            $ git branch -a

        3. View Only Remote Branches 

            $ git branch -r

        4. Checkout the Remote Branch

            $ git checkout <branch-name>

        5. Pull the Latest Changes from GitHub

            $ git pull

        6. Verify the Branch is Now Local

            $ git branch

# Git Undo

1. Git Revert 
    
    ‘revert’ is the command we use when we want to take a previous commit and add it as a new commit, keeping the log intact. First thing, we need to find the point we want to return to. To do that, we need to go through the log. To avoid the very long log list, use the --oneline optionwhich gives just one line per commit showing –

    i. The first seven characters of the commit hash
    ii. The commit message

    Git Revert HEAD :-
    
    We revert the latest commit using ‘git revert HEAD’ (revert the latest change, and then commit). By adding the option --no-edit, we can skip the commit message editor (getting the default revert message).

            $ git revert HEAD --no-edit

    Git Revert to any commit :-
    
    To revert to earlier commits, use ‘git revert HEAD~x’ (x being a number. 1 going back one more, 2 going back two more, etc.)

2. Git Reset

    ‘reset’ is the command we use when we want to move the repository back to a previous commit, discarding any changes made after that commit. First, get the seven characters of the commit hash from the log for the commit that you want to go back for. Then we reset our repository back to that specific commit using ‘git reset commithash’ (commithash being the first7 characters of the commit hash we found in the log)

            $ git reset <commithash>

    Git Undo Reset :-
    
    Even though the commits are no longer showing up in the log, it is not removed from Git. If we know the commit hash, we can reset to it using ‘git reset <commithash>’.

3. Git Amend

    commit --amend is used to modify the most recent commit. It combines changes in the staging environment with the latest commit, and creates a new commit. This new commit replaces the latest commit entirely.

    One of the simplest things you can do with --amend is to change a commit message.
    
            $ git commit --amend -m “<Commit Message>”

        Using this, the previous commit is replaced with our amended one.

4. Git Amend Files 
    Adding files with --amend works the same way as above. Just add them to the staging environment before committing.

# Status of files and log :-
    
        $ git status
    
    File status in a more compact way       
 
        $ git status --short

    Log of a file 
        Log is used to view the history of commits for a repo.

        $ git log
        $ git log --oneline

    Git Help 
        If you are having trouble remembering commands or options for commands, you can use Git help.

        See all the available options for the specific command -
            
            $ git <command> -help

        See all possible commands -
            
            $ git help --all
        
        If you find yourself stuck in the list view, SHIFT + G to jump the end of the list, then q to exit the view.