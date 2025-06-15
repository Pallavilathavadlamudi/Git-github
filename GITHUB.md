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

        $git configure --global user.name "<enter your user name>
        $git configure --global user.email "<enter your email here>

# General Git Features

1. Initializing Git

        $ git init

    Once you initialize Git in a folder, Git starts tracking it for changes. It creates a hidden directory (called .git) inside that folder to store all the information it needs to manage version history.

2. Staging files/Adding files to git repo

    Staged files are the ones that are prepared and ready to be committed to your project’s repository.

    * When you add files to a brand-new Git repository, they start out as untracked—meaning Git isn't monitoring them yet.  To start tracking these files, you need to stage them by adding them to the staging area.

        $git add <filename with extension>

    Staging all the files in a folder

        $git add --all 
        $git add -A

    They stage:
    All new, modified, and deleted files in the entire working directory.
    They include changes in all subdirectories.

        $git add .
    
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

        $git commit -m <enter your message>

4. Git commit without stage

    when making minor changes, going through the staging area may feel unnecessary. In such cases, you can commit your changes directly, without staging them first.

        $git commit -a -m <enter your message>

# Git Branching

    In Git, a branch is an independent version of your project. It lets you work on new features or fixes separately from the main branch (often called main or master).
    
    Branches help you develop and experiment without affecting the main project. Once you're done, you can merge your branch back into the main one.
    
    You can also switch between branches to work on different tasks without them interfering with each other.

1. Making a new branch

        $git branch <name of branch>

2. Checking all available Branches

        $git branch

3. Switching to other Branches

        $git checkout <branch name>

4. Making a new branch and directly switching to it

        $git checkout -b <branch name>

5. Deleting a Branch 

        $git branch -d <branch name>

6. Merging two Branches

    It's recommended to switch to the master branch before merging any other branch into it. This ensures you're merging changes into the most up-to-date version of the main project.

        $git merge <branch name>


# Working with github

    First, create a GitHub account so you can make remote repositories.
    Then, create a new repository on GitHub, which will be used to upload files from your local project.
    
    * A local repository is the one stored on your own computer.
    * A remote repository is hosted on a remote server, like GitHub, GitLab, or Bitbucket.

<img src = "https://github.com/Pallavilathavadlamudi/Git-github/blob/main/Assets/githibrepo.png" >