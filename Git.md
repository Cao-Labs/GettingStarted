# Git

Git is a version control tool that Cao Labs uses to keep all of our code up to date


## Downloading and Installation
#### Download
[Git Downloads](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git)
* If you are on windows, you will also have to install [Git Bash (for windows)](https://gitforwindows.org/), this will allow you to run the git commands. You will have to run all git commands through this program

#### Setup
[Official Git setup docs](https://git-scm.com/book/en/v2/Getting-Started-First-Time-Git-Setup)

This is the document I am following, really the only thing you need to do is setup your identity.

1. `git config --global user.name "Your Name"`
1. `git config --global user.email "youremail@email.com"`


## Common git workflow

### Getting the Code

This is how you will get the code onto your machine.

1. Navigate to your the directory you want the code to live. *Do not create a folder for the code, git will do this for you*
1. `git clone https://github.com/Cao-Labs/project_name.git`
1. `cd dir_name`
1. Just to be safe (you don't need to do this, but it makes me feel better) `git pull`

*If you do not have access to a repository, please talk to Dr. Cao or Kyle Hippe*

### Contributing to the code

1. Write your code
    1. Any time you want to see what can be put into the repository, type `git status` <br />
    **Output**
    ```
    (base) > $ git status                                                                                 [±main ✓]
    On branch main
    Your branch is up to date with 'origin/main'.

    Changes not staged for commit:
      (use "git add <file>..." to update what will be committed)
      (use "git checkout -- <file>..." to discard changes in working directory)

    	modified:   README.md

    Untracked files:
      (use "git add <file>..." to include in what will be committed)

    	Git.md

    no changes added to commit (use "git add" and/or "git commit -a")
    ```
1. Sync the changes with the upstream repository: `git pull`
1. Add the files you have changed (you don't have to add every file, just the ones that are for this feature): `git add filename1.file filename2.file etc`
1. Make a commit `git commit -m "A descriptive message that tells us what this feature is"`
1. Push to upstream repo: `git push`

### Merge conflicts

A merge conflict happens when you try to push something and another person makes a change to the same file. If you are the second person to push to the repository you will get a merge conflict. Here is how you deal with that

* If you push without a pull first this is what you will see
    ```
    To https://github.com/Cao-Labs/GettingStarted.git
     ! [rejected]        main -> main (fetch first)
    error: failed to push some refs to 'https://github.com/Cao-Labs/GettingStarted.git'
    hint: Updates were rejected because the remote contains work that you do
    hint: not have locally. This is usually caused by another repository pushing
    hint: to the same ref. You may want to first integrate the remote changes
    hint: (e.g., 'git pull ...') before pushing again.
    hint: See the 'Note about fast-forwards' in 'git push --help' for details.
    ```

* This is what you see when you pull
    ```
    (base) > $ git pull                                                                                  [±main ●▴]
    remote: Enumerating objects: 5, done.
    remote: Counting objects: 100% (5/5), done.
    remote: Compressing objects: 100% (2/2), done.
    remote: Total 3 (delta 1), reused 3 (delta 1), pack-reused 0
    Unpacking objects: 100% (3/3), done.
    From https://github.com/Cao-Labs/GettingStarted
       9764a02..7eefe8e  main       -> origin/main
    Auto-merging README.md
    CONFLICT (content): Merge conflict in README.md
    Automatic merge failed; fix conflicts and then commit the result.

    ```

* The file will now look like this if you open it in an editor:
    ```
    <<<<<<< HEAD
    Other Change
    =======
    Change1
    >>>>>>> 7eefe8e079f649bfc93c992c565512d7f1cd3ee4
    ```

    The line under HEAD is the change that is already in the repository, the line above the hash code (7eefe...) is the change from your commit.

    Decide which change to accept by deleting the other line and the dividers git adds. The ouput should be something like this:

    ```
    Change1
    ```

* Once you have fixed the change, add the file and commit again, this time with a message about what the conflict was and what change you have accepted. Once this is done, push again.
