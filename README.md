# Git Workshop MADS Semester Data Exploration

## Lesson goal

The student uses version control software in a data science project to record progress and to collaborate with others.

## Prerequisites

- Create an account on https://github.com if you don't already have one.
- Install git software. In this workshop we'll be using GitHub Desktop. This is a graphical wrapper around the git commandline application. You can download it from: https://github.com/apps/desktop


## Introduction: what is git and what problems does it solve?

Git is **version control software**. Version control software is software that lets you track changes to files. You tell git which files you want to track and from then on every time you make changes to these files git will record which changes you have made.

That's it.

While the concept ("git tracks changes to your files") is simple, in practice this simple concept turns out to be very powerful. If you have software that knows which changes you have made, you can use that same software to **undo** changes you have made when it turns out they were a bad idea. No longer do you need to create dozens of files with names like "pythonscript.1.py", "pythonscript.2.py", "pythonscript.2.new.py" and worse - just let git take care of it! It doesn't matter how many changes you make and how ill-advised those turn out to be: if git knows about them, you can easily rewind your single "pythonscript.py" to a known working state if it turns out you want to discard modifications you have made to it.

Git can not only track modifications *you* have made to *your own* files, however. It can also track modifications to files that you work on with other people. This will come in handy when you start working together with others in your data science projects.

In this hands on workshop, you will learn how to work with git. We will use the GitHub Desktop tool, though the basic concepts also work with the command line git client.

## Part 1: basic git use

### 1.1. Creating a new repository and committing our first changes

1. First we need to tell git where it can find the files for which it has to track changes. To do this open GitHub Desktop and click the button labeled "Create a New Repository on your local drive". A "repository" is simply a directory of files that git knows about.
2. Enter a "Name" for your repository (directory). Keep it simple and short and do not use spaces, quotation marks or other non-alphabetic characters other than - (minus) and _ (underscore).
3. Click on the "Choose..." button next to the "Local path" input and navigate to the folder where you want to store your new repository / directory.
4. Leave all the other inputs as they are. Click the "Create repository" button.
5. GitHub Desktop goes to work. When it is done it will great you with a window that prominently displays the text "No local changes". Which makes sense because we haven't made any files yet, let alone change them.
6. Before we continue, let's open the repository directory we just created in your file explorer. On Windows you will see it contains a directory named .git (dot git) and a file .gitattributes. These are where git stores the history of all the changes you make. On Linux or on a Mac, files that have a name that starts with a period are hidden by default. You can only see them by navigating to them using the terminal. Since we should leave the directories in question to git, this is ok for now. Just be aware that a repository is simply a directory that contains a subdirectory for storing changes that is called .git.
7. Create a new plain text file (.txt) in your new git repository. Type some text into the file. For example:
```
This is a text file.

The line above this line is empty.
```
8. Save the text file.
9. Return to GitHub Desktop. You will see it has detected that you created a new file. It also knows what is inside it.
10. We want to tell git that this (a new text file with some content) is a change that we would like to record. As it turns out, git doesn't simply monitor all the files in your repository, blindly recording any and all changes you make to them. Instead, it is smart enough to let *you* be the one to decide what is a change that is worth tracking and what is not (can you explain why this is a smart thing to do?). Recording changes is called **committing** them (to the archive containing changes). Click the button labeled "Commit to main".
11. The GitHub Desktop window changes to reflect the fact that you just committed some changes. It tells you: "No local changes", which is, of course, correct.
12. Click the button labeled "History". You will see a list of changes made to your repository. The first change is named "Initial commit": this is GitHub Desktop's way of saying you made a new, empty repository. Above that in the list of changes is the change you made yourself: the creation of the text file.

### 1.2 Making further changes and adding files

1. Most repositories contain more than one file. Go to the folder that contains your repository and create a new text (.txt) file. Enter some text in in. DO NOT COMMIT YOUR CHANGES YET!
2. Return to GitHub Desktop. Click on the button labeled "Changes". Note it has detected you created a new file.
3. Go back to the first file you created and make some changes to it.
4. Return to GitHub Desktop again and click on the button labeled "Changes" to view the list of changes. Git should now have noticed two changes to your repository: the first is the second file you created in step 1 and the second is the changes you made to the original file in step 3.
5. Next to each of the two changes is a checkbox. When the checkbox is marked this means GitHub desktop will commit the change when you next click the "Commit to main" button. Uncheck the checkbox next to the change for the new file you created in step 1.
6. You will have noticed an input above the "Commit to main" button that contains the text "Summary (required)". This input will contain text that describes the changes you have made for the new commit. GitHub Desktop can automatically create this text for you, but this automatically generated text is normally not very helpful ("Created file ..." or "Changed file ..."). It's often better to create your own summary. Enter your own summary in the text field (for example "Modified original file to see what would happen") and click the "Commit to main" button.
7. The modification to the original file is removed from the list of changes while the creation of the second file is still listed as a change. To see what was changed exactly click the "History" button and then click on the change you just committed. In the right part of the window you will see the text you removed (if any) on a light red background and any text you created on a light green background. Next to every line of text is a line number so you can tell exactly which lines are changed.
8. Go back to the list of changes that have not been committed yet. We want to commit the creation of the second file. Make sure to place a checkmark next to the new file, enter a summary (called a "commit message") and click "Commit to main".

### 1.3 Rolling back changes

1. The true strength of a version control system is of course that it can let you undo changes. GitHub Desktop can do this for you. Let's undo the changes to the original text file. However, it would be nice if the second file is kept. In other words: we want to undo an earlier change but keep one of the later ones. Click the "History" button and right click the commit that contains your changes to the original file. Select the option "Revert changes to commit".
2. A new commit appears at the top of the list. It's called "Revert (whatever the original commit was called)".
3. Click the "Changes" button. You will see there are no changes.
4. Open the original text file in a text editor. You will see the changes you have made to it have been reverted.

### 1.4 Git tracks files, not directories

1. Git tracks changes in files, not in directories. To show that is is true, create a new subdirectory in your repository.
2. Return to GitHub Desktop. Notice it has detected "No local changes". It is impossible to commit creation of a new, empty directory as a change.
3. Create a new text file in your new directory and add some text to it.
4. Return to GitHub Desktop. It has detected the addition of a new file, specifically a file in the subdirectory you created in step 1.
5. Commit the change.


## Interlude: Jupyter notebooks

If you can run Jupyter notebooks locally, be sure to try tracking changes in them using git:

1. Add an empty text file to your git repository. Turn it into a a Jupyter notebook file by renaming the extension of a .txt file to .ipynb.
2. Edit the Jupyter notebook. Add a code cell that outputs something. `print("Hello")` suffices. Save the notebook file BUT DO NOT RUN ANYTHING.
3. Open GitHub Desktop. Notice it has detected the new notebook file. Commit your changes.
4. Now **run** the notebook. Your code should output "Hello" (if your code was `print("Hello")`). Save it.
5. Return to GitHub Desktop. Notice there have been quite a few changes in your notebook file, even though all you did was run a single line of code. Pay particular attention to the line that reads "execution_count". Apparently Jupyter notebooks track how often a code cell is executed.
6. Commit your changes.
7. Run the code in your notebook again. Pay particular attention to the fact that nothing appears to have changed: your notebook contains a single code block and a line containing the output of that code - which hasn't changed. Save your notebook.
8. Return to GitHub Desktop yet again and notice the line containing execution_count has changed even though nothing, really, has changed. Think about what this means for doing data science work using Jupyter notebooks and tracking the changes in git.

## Part 2: Collaborating with other users

So far we have used git to track changes in files we have stored on our own computer. While this is very useful, git can also help you track changes in situations where you're working on a single file or single project together with somebody else (in fact, this is what it was specifically made for).

In the second part of this workshop we will make our code available to others to work with and make some changes to their code.

### 2.1 Pushing and pulling.

1. First we need to make our code available to others. To do this, we must *publish* our repository. "Publishing" means "making it available for others to download from the internet". Click the "Publish repository" button in the main GitHub Desktop interface. In the dialog that appears, uncheck the option "Keep this code private" (you want others to be able to make changes to your code) and click "Publish repository" to upload your repository to https://github.com .
2. Open https://github.com in your browser and navigate to the page that contains all your repositories. There may be a link to it on the GitHub homepage. If there isn't, you can open it by clicking on your profile image and selecting the "Your repositories" option from the menu. You will see a list of all your repositories. The repository you just uploaded should be at the top.
3. Click the name of your repository and verify that it contains all your files. You can click on the file names to see what they contain and if you did the interlude "basic git use (single user) with Jupyter notebooks you will find that GitHub can display Jupyter notebooks as well.
4. https://github.com , in fact, allows you to make changes to files right on the website. Click on the name of one of the text files you created and then click on the pencil icon to edit it. Make some changes and click the "Commit changes..." button. Add a commit message or accept the default and click the "Commit changes" button.
5. There are now changes to your files on https://github.com  that have not been made to the files on your computer. We need to somehow transfer them over. To do this, we need to load them from https://github.com into GitHub Desktop. 
6. Loading changes from the internet into your local files is a two step process: first we need to let GitHub Desktop *know* something has changed online and *then* we need to tell it to *load* those changes. To do the first, click the button labelled "Fetch origin". When GitHub Desktop is done fetching, the "Fetch origin" button changes into a button labelled "Pull origin". A button labelled "Pull origin" also appears in the main area of the GitHub Desktop window.
7. Now that GitHub Desktop knows there are changes in the online version of your files, we need to load these changes. Loading changes from a remote server is called "pulling" (and the remote server is called the "origin"). Click the "Pull origin" button, either the one in the main area of the GitHub Desktop window or the one at the top of the window. When this is done, the "Pull origin" button disappears.
8. Verify that the changes you made on https://github.com have appeared in your local files.

Congratulations! You have just made your first git repository available to the world at large and made changes to it on two different machines!

Note: in a real situation you may not want your code to be available for everyone to download from the internet. In that case you can set up a git server of your own that you only make available to people you trust. How to do this is way, way beyond the scope of this workshop, however. A reasonable alternative is to sign up for a paid GitHub account that lets you share private repositories with specific people (for free accounts private repositories can not be shared with anyone else).

### 2.2 Collaborating on the same repository

Now that your repository is available online, at https://github.com , you can work on it with others. For this part of the tutorial you will need to team up with a partner. You will be editing each others' files.

1. First you will need to download your partner's repository. Ask your partner to give you the link on https://github.com to their repository. Then click the "Current repository" button. A button labeled "Add" appears. Click it and select the option "Clone repository" (to "clone" a repository is to make a local copy of a repository). Click the button labeled "URL" in the dialog and enter the link you have been given in the "URL" input field. Click "Clone".
2. GitHub Desktop makes a local copy of your partner's repository. Open it in your file explorer and make a change to one of the files.
3. GitHub Desktop shows you something has been changed. Commit your changes. Notice the warning message that says you are not allowed to push changes to the online repository that belongs to your partner. Ignore it and perform your commit.
4. Now click the "Push origin" button. Again you will see a message that this is impossible. Your partner will need to give you permission to work on their repository. Ask your partner to do this and click the "Cancel" button.
5. Meanwhile you should give your partner permission to work on *your* repository. Do this by opening your repository on https://github.com and click on the "Settings" option near the top of the page. Click on the "Collaborators" link.
6. Click on the button "Add people" and then ask your partner for their username on https://github.com . Enter this username and click "Invite collaborator". Then click the button "Add \<your partner\> to this repository". Note your partner has now been *invited* to the repository. They will still need to accept the invitation before they can start contributing. Wait for them to accept the invitation. It has been sent to their email address. They will need to click the "accept" link in that email and then click the "Accept" button on the https://github.com page it leads to before they are actually added as a contributor.
7. When your partner has also added you to *their* repository and you have accepted their invitation return to GitHub Desktop and click the "Push origin" button again. This time your changes are uploaded ("pushed") to their repository on https://github.com.
8. Open their repository on https://github.com and navigate to the file you changed. Notice the file now contains both their edits and yours. If you click the button labeled "Blame" you can see which user made which change in the file.

**Note**: you will notice the "Current repository" button leads to all the repositories that you have stored locally (that GitHub Desktop knows about). If you click the repository you want to work with, it will be loaded in the main GitHub Desktop window so you can view changes, commit changes and pull and push your changes to the origin (ie. https://github.com).

**Note**: when you try to click the "Push origin" button while you do not have permission to make edits in a repository you are given the option to "fork" the repository. To fork a repository is to make a copy of it. This copy will remain linked to the original repository so you can continue to pull changes that are made to it. Similarly you can ask the owner of the original repository to copy your changes to their repository using something called a "pull request". Forking and pull requests are advanced topics, however, that are beyond the scope of this workshop.

## Part 3: When things go wrong

Now that you are collaborating with other users, we are opening ourselves to the risk that multiple users simultaneously make changes to the same file. Luckily git is very clever about combining changes, but sometimes there really isn't anything it can do when two or more changes have been made that conflict with each other. In such cases you will have to fix these so-called "merge conflicts" yourself.

For this part of the workshop, you will once again work with a partner on the same repository.

1. First of all make sure both of you have the latest version of the repository by pulling the latest changes.
2. Now each of you should make a change to the same line of the same file. Maybe add your first name to the first line of the same file - that usually works.
3. Commit your changes but do **not** push your changes yet until **both** of you have committed your changes.
4. Now attempt to push your changes. The first person to push their changes will succeed, of course.
5. The second person will be told, by GitHub Desktop, to pull from the origin (if you do not see this message, simply attempt to push - GitHub Desktop will quickly figure out there are changes that need to be pulled).
6. A dialog appears telling you there are conflicts that need to be resolved (confusingly it may state the conflicts are resolved before it figures out that, no the conflicts need to be resolved manually).
7. At this point, the option "Open in editor" is likely grayed out because you have not configured an editor for your GitHub Desktop application. This is inconvenient because now you cannot actually resolve the conflict.
8. Instead you will need to open the conflicting file in a text editor. You will notice the conflicting edits are surrounded by lines that start with greater than or lesser than symbols. It is fairly obvious where the conflicting changes are (and it's probably easier to find them yourself than it is to decribe this in writing). Find them and resolve them somehow. When you are done, remove the lines that mark out the conflicts until you have a version of the file your partner and you are both satisfied with.
9. When you save the file, GitHub Desktop will notice you have resolved the conflict. Click the "Continue merge" button. It's possible clicking this button does not work in some versions of GitHub Desktop. In that case stop the GitHub Desktop application and start it again. Then click the "Continue merge" button. "Continue merge" will create a new commit for the changes you made.
10. Open the list of changes by clicking the History button. You will find the changes you made in step 8 have automatically been added to the list of commits.
11. Click the "Changes" button and then push the changes by clicking the "Push origin" button.
12. Optionally your partner can pull the latest changes and verify that the conflicts have, indeed, been resolved.

**Note**: in this workshop your file only contains a single conflicting change. However, in practice merge conflicts often contain multiple conflicting changes, sometimes in multiple files. You will have to resolve all of these changes before you can continue.

**Note**: it may be useful to set up a default editor for GitHub Desktop. This allows you to resolve conflicts straight from the GitHub Desktop program.

**Note**: Jupyter notebooks are very prone to merge conflicts. If you collaborate on a notebook with a partner and both of you run the same code, the line that contains information on when the code was last run, will conflict. Unfortunately there really isn't an easy solution for this. You will have to be very, very careful when collaborating on data science projects and it's probably best if each collaborator works in their own notebook file.

