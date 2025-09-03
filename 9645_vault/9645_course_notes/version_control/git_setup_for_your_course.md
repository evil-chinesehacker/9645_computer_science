
## Installing homebrew
*Install `homebrew` by running the following commands in your terminal.*

``` shell
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

---
## Using homebrew to install Git, Github CLI and Obsidian
*Use homebrew to install Git, Github CLI and Obsidian.*

``` shell
brew install git
brew install gh
brew install obsidian
```

## Forking the Master repository
- Make an account for GitHub using your school Microsoft email address.
- Log into GitHub in your browser.
- Visit https://github.com/Kellett-School/9645_computer_science
- Click `fork` then click `create fork`.
- Open your forked version of the repository.

## Creating your local copy of the forked repo
- Back in your terminal, use `cd` to navigate to the folder where you are storing your Computer Science work this year.
- Back on the GitHub website, click on the green Code button and choose GitHub CLI copy the `gh repo clone` command and paste this into your terminal and run the command.
- `cd` into the new repository.
- Make a copy of the `student_notes` subdirectory following this naming format: `firstname_surname` you can use the following command:
``` shell
cp -r student_notes firstname_surname
```
*replace firstname_surname with your actual firstname and surname!*

- `cd` into the `firstname_surname` subdirectory.

## Opening with Obsidian
- Now, open the **Obsidian** app.
- Choose the option to **Open folder as vault** and choose the `9645_vault` folder you cloned from GitHub.
- On the left hand side you will find the **explorer panel**.
- Inside the `firstname_surname` subdirectory, make a new note and call it something like `my_first_note`

## Setting your git username and email
- Go back to your terminal and run the following commands:

``` shell
git config --global user.name yourusername
git config --global user.email youremail@yourdomain.com
```

## Pushing your changes via obsidian's git plugin
- go back to Obsidian
- click on the git tab
- add the changed files with the add all button
- change the default commit message if you like
- commit the change
- press the push button
- 
*Well done*! You have finished the set up of Git, Obsidian & GitHub - this will be the backbone of your workflow for A Level CS.


## Stage, Commit and Push
You will use these commands **throughout** each lesson. This will allow you to push your local changes to the cloud (GitHub) so that a) your teachers can access your work and b) you can sync your work between multiple devices as necessary.

The three commands are `stage`, `commit` and `push`

**`stage`** - register local changes that have been made to files
*alternatively* you can use **`add`** instead of **`stage`** to add files to a commit, both work the same way. You can also use a dot `.` to represent all e.g. `git stage .` means stage all changes for commit.
**`commit`** - save these changes to the git working tree (add a message to describe what you changed)
**`push`** - upload the changes to the server.

``` shell
git stage .
git stage <name of the file you just created>
git commit -m "made my first note" 
git push
```

## Updating from the master repo

Another thing that you will be told to do is update your repository by downloading updates from the origin repository - this will allow your teachers to distribute work to you.

To set this up to always merge the changes from the upstream server, run this command:

``` shell
git config pull.rebase true
```

### Adding an upstream
*if you did not use the gh command to clone your repository you may need to do this*

We need to ensure we can still access the course notes in case your teachers update these notes and add new content, this means we need to add the original git repository as a remote called 'upstream' like this:

``` shell
git remote add upstream https://github.com/Kellett-School/9645_computer_science.git
```

### Pulling a teacher's changes from the master repo
Now, whenever you are prompted - run this command to download your teacher's new changes:

``` shell
git pull upstream main 
git pull
git push
```



