# PySAL Sprint Tutorial

This tutorial is intended to teach people how to contribute to open source
 projects using the using the ``git`` command line tool and Github.

## Outline

1. What you need to get comfortable with
1. What you can contribute
1. What you need
1. How to create development environments
1. Working with git and github
1. How to contribute code
1. PySAL Overview


## Contributing: what you need to get comfortable with

1.   Working at the command line.
1.   Issue workflow on Github.
1.   Making changes and recording them using git.
1.   Good coding practices (testing frameworks, styling tools, restructured text and documentation generators).

Do you need to be here? No if you are already comfortable with the first
3 items!

## What you can contribute

List of ideas, requiring more and more technical knowledge of the
package in question:

- Documentation improvements
- Tutorial review/improvements
- Example review
- Example creation
- Add unit tests (driven by test coverage analysis)
- Fix a bug
- Tutorial creation
- Implement new features
- Review other people\'s PR
- Close old issues not relevant anymore
- Triage issues

Three pieces of advice:

-  Your own needs are the best driver for open source contributions.
-  If you don't know what to do, look for issues tagged `easy` or `good-first-issue`
-  If you don't know what to do, ask maintainers what would be the most helpful.

## What tools you needs
* A python aware code editor. There are many free options: Visual Studio Code, Pycharm,
  Canopy, Spyder, emacs, vi(m), ....
* An account on `github.com`.
* The `git` tool. OSX: Install Xcode command line tools.
  Windows: https://git-scm.com/download/. Linux: use your package manager
  (`yum`, `apt-get`, ...).
* [ssh keys on github](https://docs.github.com/en/github/authenticating-to-github/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent)
* A tool to quickly create and manage light development environments (conda).


## conda environments

1. Download [miniconda](https://docs.conda.io/en/latest/miniconda.html)
2. `conda create -n dev`
3. `conda --info envs`
4. `conda activate dev`
3. `conda --info envs`

Anything you add with `conda install` will now only be in the `dev` environment.

Try: `conda install -c conda-forge libpysal`


## Git 

### Working Locally

- `git init` to create repository
- `git add 'file_name'` to add file to tracking
- `git commit -m 'commit message'` to commit changes/tracked files
- `git checkout -b 'branch_name'` to create new branch
- `git checkout 'branch_name'` to switch between branches
- `git branch` to view current branch

### Merging branches

When you are satisfied with work in a working branch, you might want to merge the changes into the 'main' branch. Make sure you are in the main branch, and then `git merge 'branch_name'`. To delete the nowmerged branch, `git branch -d 'branch_name'`


### Working with remotes

#### Pushing your local repository to a new remote
Once you're satisfied with changes made to your local repository, you might want to push it up to GitHub. 
1) create a new repository on github.com
2) copy and paste the command from the creation page: `git remote add origin 'url-ending-in.git'`
3) push (after setting up keys) using `git push -u origin main`
4) when setting up keys, you want to make sure you add the repository URL starting with `git@:` instead of `https://`


We will examine how to work with an existing remote below in the typical workflow.

### When things go wrong with git

Git is an incredibly powerful tool to manage code, but it is pretty easy
to mess up. It is ok, everyone messes up with `git`. The good news is,
you can (almost) always recover from a mess up. If you have an issue,
pause, think, google, find a git guru!

Here are a few tricks to get out of common situations:

 -   You have made a mess and want to erase all un-committed code (ALL
     FILES):

         git reset --hard HEAD

 -   You have made a mess in only 1 file:

         git checkout HEAD -- filename

 -   You have committed too quickly, and want to include more files, or
     redo your commit message:

         git reset --soft HEAD^

 -   You don\'t like where you are going and decide you want to go back
     in time, to a precise commit, look for the commit hash with:

         git log

     and then reset to that point:

         git reset --hard <HASH>

     You can also go back in time without loosing your work since then,
     just to check things out:

         git checkout <HASH>

 -   You have pulled main or a collaborator\'s work and now have a
     conflict? Open the conflicted file in an editor, and merge lines
     manually. Then:

         git add filename

     to mark it as resolved. Your branch is back to being ready to be
     committed.

 -   You would like to pause your work in progress without committing
     to do something else or switch to another branch that has
     conflicts:

         git stash

     When you are done, and want your changes back:

         git stash pop

     Note that you can stash multiple times. States are stored on a
     stack (FILO).

## How to contribute code?

### The typical workflows

1.  Identify a work item you want to contribute. **Think small**.
2.  Create a ticket for your work item **if it doesn\'t already
    exist**.
3.  Assign the ticket you are working on to yourself so others know it
    is work in progress.
4.  Go to the package\'s Github repository. Fork it into your account
    where you have push rights. If you are contributing to a package
    you have push rights for, you might skip this step. Discuss with
    your project lead/repository owner.
5.  Clone your fork locally (or the package\'s repository directly if
    you have push rights and are allowed to push branches to it
    directly):

        git clone https://github.com/<USER NAME>/sprint_tutorial_pysal

    (Whichever repository you clone will represent a \"remote\" and be
    called \"origin\". A remote is a repository you can pull from.
    `git` allows multiple remotes to be defined on your local checked
    out code, in case you want to pull and push to/from different
    locations.)

6.  Create a new development environment (if not already done). Build
    the project into your dev environment. Run the test suite.
7.  Branch off to a new branch for your work item:

        git branch fix/bug_name
        git checkout fix/bug_name

    or in a single step:

        git checkout -b fix/bug_name

    (If a \"commit\" can be defined as a specific state of the source
    code you are working with, a branch can be defined as a series of
    commit about your targeted work. On your machine, `git` can track
    any number of branches, allowing you to work, in parallel, on any
    number of distinct tasks.)

8.  Make sure you are in the expected branch:

        git branch

9.  Do work. **STAY FOCUSED** and only address the work item you
    selected. Otherwise review will be hard(er), therefore delayed,
    and your PR is likely to be rejected.
10. Review what has been done with:

        git status
        git diff file1.py

11. When a set of changes represents a valuable step toward your goal,
    commit:

        git commit -m "TEST: add unit test to show the bug" file1.py file2.py ...

    Or make a more complete commit message using an editor:

        git commit file1.py file2.py ...

    and write the commit message in the editor `git` uses.

12. Don\'t forget to include or update unit tests to make sure your
    work doesn\'t break in the future. Remember, your most important
    contribution might be your tests! If some code isn\'t unit-tested,
    it is either already broken, and it will be (and no one will know
    about it)! And run the entire test suite to make sure your
    contribution didn\'t break anything.
13. Once you have done everything you want, push your branch to
    Github:

        git push --set-upstream origin fix/bug_name

    or simply:

        git push

14. Go to Github to make a [Pull Request]{.title-ref} (PR) with your
    work. You should see your branch available for a PR in both your
    repo and in the upstream repository that you forked. Select the
    branch you would like to pull your branch into, and add a complete
    description.
15. Check for the result of Continuous Integration (CI).
16. Discuss your work with your reviewer. Implement fixes and
    improvements, and push again to your branch. Your PR will update
    automatically.
17. If the original package\'s main branch gets updated between your
    cloning and the time your PR is merged, you may be asked to merge
    main changes into your branch or rebase your branch onto the new
    one, and resolve any conflict. To that effect, you need to define
    another remote you want to pull changes from, assuming you have
    forked the repo. In that case, the common approach is to define
    the official package repo as a new remote called \"upstream\":

        git remote add upstream git@github.com:sjsrey/sprint_tutorial_pysal

    If the project you are contributing to is ok with merges of
    main, it is easier to do the following:

        git checkout main
        git pull upstream main
        git checkout fix/bug_name
        git merge main
        git push

    If your project requires to rebase:

        git fetch upstream
        git rebase upstream/main

    Note that the commit hash of your current state will be changed,
    so if you have pushed before the rebase, your state will need to
    be \"force-pushed\":

        git push --force

18. Once the PR has been approved, it will be merged in the upstream
    project by someone who has push rights.
19. After merge, there are 3 typical cleaning steps: delete the branch
    on the remote repositories (in Github), update main locally from
    upstream, update main in your own fork and delete the work
    branch locally.:

        git checkout main
        git pull upstream main
        git push origin main
        git branch -d fix/bug_name

20. GOTO 1.




*Portions of this tutorial were adapted from the [Scipy Sprint Tutorial](https://github.com/jonathanrocher/sprint_tutorial).*
