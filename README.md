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


## Git 

### Working Locally

- `git init` to create repository
- `git add 'file_name'` to add file to tracking
- `git commit -m 'commit message'` to commit changes/tracked files
- `git checkout -b 'branch_name'` to create new branch
- `git checkout 'branch_name'` to switch between branches
- `git branch` to view current branch

### Merging branches

When you are satisfied with work in a working branch, you might want to merge the changes into the 'master' branch. Make sure you are in the master branch, and then `git merge 'branch_name'`. To delete the nowmerged branch, `git branch -d 'branch_name'`


### Working with remotes

#### Pushing your local repository to a new remote
Once you're satisfied with changes made to your local repository, you might want to push it up to GitHub. 
1) create a new repository on github.com
2) copy and paste the command from the creation page: `git remote add origin 'url-ending-in.git'`
3) push (after setting up keys) using `git push -u origin master`
4) when setting up keys, you want to make sure you add the repository URL starting with `git@:` instead of `https://`


#### Forking and cloning

1. Go to the repository for this project https://github.com/sjsrey/sprint_tutorial_pysal
2. Press the `Fork` button in the upper right of the page
3. Clone your repository once the fork is finished


#### Pulling new changes
good habit to `git status` before making commits - it will tell you if your version is behind the master. 
`git pull origin master` will pull new changes (differences only** to update your version.


*Portions of this tutorial were adopted from the [Scipy Sprint Tutorial](https://github.com/jonathanrocher/sprint_tutorial).*
