# Git for Jits

## Intro

Welcome to Git for Jits! A simple lesson plan to help teach you the very basics of Git and what you need to be useful in day to day work life. Git can seem a bit intimidating at first, but, at its core, it's a simple tool for tracking your changes while you work on code that makes it easier to work with other people concurrently.

## Solo Work

The first section of G4J is meant to teach you how Git works and how to use it on your own to manage project versions and histories. While git is meant to be used by multiple people on teams of varying size, knowing how to use it on its own to track changes is a valuable first step.

### Clone

The first command to know is `git clone`. **This command takes a url to a given repository and copies it to your local machine.** When you are working with someone else's project, this is just about always where you will start.

Even when you're starting a project from scratch, oftentimes, you'll find yourself initializing the repo on the web and then simply clone it to your local machine. For this reason, it seemed more practical to start this course with the use of `git clone`.

To get started:

1. Open your command line of choice on your local machine and navigate to whatever folder you keep your repos in
2. At the top of this page, you should see a bright green button that says "<> Code". Click the dropdown and copy the url.
3. In the command line, type `git clone` and paste the url after it like so

```bash
$ git clone https://github.com/dwiv/git4jits.git
```

After a moment or two, you should see the folder appear on your device. Presto! You've successfully pulled the project to your machine! Nice work.

Now let's talk about how to get started so you can push your first changes!

### Branch

Now that you've pulled the repo, let's say you want to get started developing! The first thing you'll want to note is that **after you clone a repo, you will start out on the `main` branch.** This is an important note because `main` is typically the most important branch on a project. It is the one that will tend to have the most permissions and be the most locked down out of the bunch and usually, you will not be able to edit it directly unless you are a senior dev.

Ok, you may be asking, "Well if I can't change anything, what's the point of using Git?" A good question, that's where **branches** come into play!

**A branch is parallel version of the code that allows you to make changes without affecting the code it comes from.** To simplify, a branch is a copy of the `main` code that you can work on as much as you want that exists at the same time as the original. **Any changes you make on a branch will not affect the original code.** You can make as many branches as you want to work on then merge the new changes into another branch later.

That's a lot of words, to be sure so let's see it in action. Head to your command line and type the following to create a new branch:

```bash
$ git branch my-new-branch
```

This should create a new branch. You can check this by running `git branch` this should display a list of all the branches that exist on this project which should include `main` and `my-new-branch`.

Now depending on what command line you're using, you might notice that you're still on `main`. That's odd you just made a new branch, didn't you? You did, but the `branch` command only **creates** the new branch. It doesn't switch you to it. A little annoying, to be sure, but that's all of programming. You need to be explicit with the computers. So let's see how we can go about switching branches in the next section!

### Checkout

When you want to switch from one branch to another, `checkout` is the command for you. So now that you've created a new branch. Let's switch to it!

```bash
$ git checkout my-new-branch
```

A message should pop up that confirms the you have successfully switched branches. Good work! You now know how to move between branches!

Now let's say you also wanted to go back to `main`. How would you do that?

```bash
$ git checkout main
```

Simple as that. It would make life a LOT easier if you could make a new branch **and** switch to it at the same time. Luckily, `git checkout` has a way for us to do just that using the `-b` flag.

So what exactly is a flag and how is it going to make life easier? **A flag is a letter or string that follows a hyphen (or two hyphens) that is used to modify the behavior of a command.** In this case `-b` is a flag that tells the command "create a new branch with this name."

So if you wanted to, you could create another new branch from `main` with the following command:

```bash
$ git checkout -b my-other-new-branch
```

This command would create the new branch automatically and put you on it at the same time. Not a necessary way to do things but good to have in your back pocket.

If you tried this, you can verify it worked as expected by running `git branch` to make sure there are 3 branches now, OR if you are reading this on github, simply refresh the page and make sure the number of branhces changed.

### Commit

Now that you have your own branch, let's say you wanted to actually make some changes. Let's try that out with the example below!

```python

def print_to_ten():
    // This function prints the numbers 1-10


```

**Edit this snippet above to be a python function that prints the numbers 1-10**
When you're done, change the text below to say "I did it!"

**I didn't do it because a for-git-able bum 😭!!**

Once you have changed these things, you are ready to commit your changes. **commit creates a snapsot of your code at that given moment that can be accessed again later in order to allow incremental progress to be captured while working.**

The goal of using commits is to allow all devs to work without fear of losing everything if something breaks. Multiple commits create a history that can be seen on github and act as a sort of save point for code that you can revert to later at anytime.

Now that we have that clear, let's try making a first commit. Enter the following in your command line:

```bash
$ git commit -m "updates the print to ten function to work properly"
```

After you run this, you should see some text display. You can verify this worked by running `git log`. This should show you the commit number and the message you wrote.

#### A Note About Commit Messages

You may have noticed that there is a flag in this command `-m`. As we said earlier, **flags add functionality to the command being run.** In this case the `-m` flag is used to add a message to the commit. **These messages should be a short useful summary of what changes you've made.**

Commit messages are almost always required on teams and should be used to provide concise explanations of work. \*_You should always use the `-m` flag when committing code and always provide a meaningful explanation of your code._

#### Before moving on to the next section

- In the code snippet section from earlier add another function called `print_to_twenty` that prints the numbers from 11-20. Then commit it.
- After that, add another function called `print_to_thirty` that prints the numbers from 21-30 and commit it.
- Run `git log` In your command line to make sure your commits are there.

### Push

If you go to github right now and view your branch, you may notice that despite having made changes, committed them, and checked locally to make sure they were there. What's the deal with that.

Currently, **all your changes are local.** As a result, anyone else that happens to see your branch won't see anything new until you share your changes. To do this, we'll use `git push`. Push uploads your changes to be seen and tracked by anyone with access to your repo. Not just changes you can see locally. Let's give it a try!

When you push a new branch for the first time, you'll need to use the `--set-upstream` flag. `--set-upstream` is used to tell git what branch in the cloud to reference when you `push` and `pull` going forward. This only needs to be done the first time you push a local branch as seen below.

```bash
$ git push --set-upstream origin my-new-branch
```

After this runs, refresh the repo on github and go to your branch. You should see the commit at the top change and the time listed as "now" or however many seconds have passed since you pushed. Congrats! You can share your code with the world now.

A reminder, you only have to use `--set-upstream` the very first time you push a new local branch. after that, all you need to use is `git push`. Let's test that out!

```python
def print_to_40():
    // This function prints numbers from 31-40
```

**Fill in this function, commit, and push it.**

### Add

We're nearing the end of the individual section of this guide. Nice work, jit! The last thing we need to know is how to add new files. Git is pretty dumb and unless you tell it to look for new files in a project, it will only keep track of changes in files that already exist. So how do we get around this? We use `git add`!

To demo this, on your local machine, go into the `src` folder and create a new file called `printers.py`. Go back through this document and collect all the python statements that you've used so far. Paste them into this new doc.

If you tried to run `git commit` now, you'd get the message "There are no staged changes to commit." This is because git doesn't know about your new file, it's not looking for anything to be there. To change this, you can tell git to look for any new files using `git add --all`. This will tell git to look for any new files and add them to the list of things to keep an eye on. This is called **staging** a new file.

Try this yourself by **staging your new file, committing your changes, then pushing them to your branch.**

## 🚧👷‍♂️ Group Work 🚧🏗(UNDER CONSTRUCTION)

### Fetch

### Pull

### Merge

### Conclusion

### Resources
