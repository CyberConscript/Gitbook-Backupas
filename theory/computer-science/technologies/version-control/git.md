# Git

## Table of content

[Introduction](git.md#introduction-to-git-and-github)

[Installation](git.md#install-git-on-your-windows-local-machine)

[Working with Git](git.md#working-with-git-repository)

[Viewing changes](git.md#viewing-what-was-done)



## Introduction to Git and GitHub

Git is a distributed version control system that is used to manage source code changes while collaborating with others. It allows you to keep track of your code changes, collaborate with others, and keep your code safe. GitHub is a web-based hosting service for Git repositories. It provides a web-based graphical interface and many features for managing Git repositories.

What is Git?

Git is a distributed version control system that is used to manage source code changes. It was created in 2005 by Linus Torvalds, the creator of Linux. Git allows you to keep track of your code changes, collaborate with others, and keep your code safe. It is especially useful for large projects with multiple contributors.

Git is a distributed system, which means that every developer has a copy of the entire repository on their local machine. This allows for quick and efficient collaboration, as developers can work on the same codebase without the need for a central server.

## What is GitHub?

GitHub is a web-based hosting service for Git repositories. It provides a web-based graphical interface and many features for managing Git repositories. GitHub is used by millions of developers and is the most popular platform for open-source projects.

GitHub provides many features for managing Git repositories, including pull requests, issue tracking, and code review. It is a great platform for collaboration, as developers can work on the same codebase and share their changes with others.

How to use Git and GitHub on&#x20;

Using Git and GitHub can seem daunting at first, but with practice, it becomes easier. Here are some basic steps to get started:

### Install Git on your Windows local machine

1. To use Git, you need to install it on your local machine. You can download Git from the official website ([https://git-scm.com/](https://git-scm.com/)). Once downloaded, run the installer and follow the on-screen instructions.
2. Configure your Git username and email: Open the Git Bash terminal (on Windows) or the terminal (on Mac/Linux), and enter the following commands, replacing "your\_username" and "your\_email" with your own information. This is how you tell Git your name and email (particularly before creating any commits). Rather than usernames, Git uses a name and an email address to identify the author of a commit:

```arduino
git config --global user.name "your_username"
git config --global user.email "your_email"
```

3. Verify your Git installation: To verify that Git has been installed correctly, enter the following command in the terminal:

```css
git --version
```

This should output the version number of Git that you just installed.\


## Working with Git repository

A Git repository is the local collection of all the files related to a particular Git version control system and contains a **.git** subdirectory in its root. Git keeps track of the state of the files in the repository’s directory on disk. Git repositories store all their data on your local machine. **Making commits, viewing history**, and **requesting differences between commits** are all local operations that don’t require a network connection.

#### Creating Git rep

To create a Git repository, you can either create a new project or convert an existing project into a Git repository. Once you have a repository, you can start making changes to your code.

1. Navigate to the directory where you want to create the repository.
2. Run the command `git init <name_of_repository>`. This initializes an empty Git repository in the current directory.

When you run `git init` in a directory, it initializes a new Git repository. This means that Git creates a hidden `.git` directory inside that directory, which contains all the necessary files for version control.

Here are some of the files that are created after running `git init`:

1. `.git/HEAD`: This file points to the current branch that you're working on.
2. `.git/config`: This file contains the repository-specific configurations for Git.
3. `.git/description`: This file contains a brief description of the repository.
4. `.git/hooks/`: This directory contains scripts that Git will run before or after certain events.
5. `.git/objects/`: This directory stores all the objects that are created during version control, including files, directories, and commits.
6. `.git/info/exclude`: This file contains a list of files or directories that Git will ignore during version control.

To do anything useful in Git, you first need one or more commits in your repository. Commit is one of the operational keywords for Git. You can perform several operations on your project files and directories without even needing a network connection, such as creating a new file, modifying an existing file, staging files for commit, and creating a new commit. However, some operations like pushing and pulling require a network connection to interact with a remote repository.

Here are some Git operations that you can do without a network connection:

1. `git init`: Initializes a new Git repository.
2. `git add`: Adds changes to the staging area.
3. `git commit`: Commits changes to the local repository.
4. `git branch`: Lists all branches in the repository or creates a new branch.
5. `git checkout`: Switches between different branches.
6. `git diff`: Shows the difference between different versions of a file.
7. `git log`: Shows the commit history of the repository.
8. `git status`: Shows the status of the current working directory.
9. `git reset`: Unstages changes from the staging area.
10. `git revert`: Reverts a commit.



#### Git workflow recipe

When you modify a file in your working directory, Git will not automatically track those changes. Instead, you must add the changes to the index/staging area using the `git add` command. The Git index, also known as the staging area, is a data structure used by Git to track changes made to files in your repository.&#x20;

The index is essentially a snapshot of your working directory, and it stores information about the changes that you have made to the files in your repository. When you run the `git commit` command, Git will take the contents of the index and create a new commit object with that data.

The index provides several benefits, such as allowing you to selectively stage changes to your repository, giving you the ability to review your changes before committing them, and enabling you to create partial commits with only some of the changes made to your repository.

In summary, the Git index is an important part of the Git workflow, as it allows you to stage and commit changes to your repository in a flexible and granular manner. So using this knowledge we can draft how typical Git workflow is constructed from these steps:

1. Creating a Git repository: You can create a Git repository by using the `git init` command in the terminal. This will create a new repository in your current working directory.
2. Adding files to the staging area: After creating the repository, you need to add the files you want to track to the staging area. You can do this by using the `git add` command. For example, to add all files in the current directory to the staging area, use the following command:

```csharp
git add .
```

You can add everything in the current directory and its subdirectories.  Entire directories as arguments instead of files can also be passed.

3. Committing changes: Once the files are added to the staging area, you can commit the changes by using the `git commit` command. Commit is a snapshot of changes made to your repository. For example, to commit the changes with a commit message, use the following command with adding comment using -m:

```sql
git commit -m "Commit message"
```

Each Git commit contains metadata that helps to identify and track changes to the repository. Here's an overview of the metadata that's typically included in a Git commit:

* A unique identifier: Each commit has a unique identifier, which is a 40-character hash value that identifies the commit and distinguishes it from all other commits in the repository.
* The author: The author of the commit is the person who made the changes and created the commit. The author's name and email address are typically included in the commit metadata.
* The committer: The committer is the person who added the commit to the repository. This may be the same as the author, but it could also be someone else who added the commit on behalf of the author.
* The commit message: The commit message is a brief description of the changes made in the commit. It's typically written in the present tense and should provide enough information to understand the purpose of the changes.
* The commit date: The commit date is the date and time when the commit was created. This is typically recorded as a timestamp in the commit metadata.

In addition to this basic metadata, each commit also includes information about the changes made to the repository. This information includes a list of the files that were changed, along with the specific changes that were made to each file. This information is stored as part of the commit object, which allows you to view the changes made in each commit and track the history of your repository over time.

When you create a commit, Git will record the changes you made to the files in your repository, as well as the metadata described above. You can then use this information to track the history of changes to your repository over time. Commits should be kept as small as possible. This allows their message to describe a single change rather than multiple changes that are unrelated but were worked on at the same time. Small commits keep the history readable; it’s easier when looking at a small commit in the future to understand exactly why the change was made.

Committing changes is a critical step in the Git workflow, as it allows you to save your changes and make them a permanent part of your repository's history. It's important to create clear and concise commit messages that describe the changes you've made, so that others can understand the purpose of the commit and its impact on the repository.

4. Pushing changes to a remote repository: After committing changes locally, you can push them to a remote repository (such as GitHub) by using the `git push` command. For example, to push changes to the master branch of a remote repository, use the following command:

```perl
git push origin master
```

5. Pulling changes from a remote repository: To pull changes from a remote repository (such as when collaborating with other people), you can use the `git pull` command. For example, to pull changes from the master branch of a remote repository, use the following command:

```
git pull origin master
```

<figure><img src="../../../../.gitbook/assets/image (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

## Viewing what was done

Viewing the differences between commits in Git is an essential part of understanding the changes made to a codebase over time. By comparing different versions of a file, you can identify which changes were made, when they were made, and who made them. This information can be invaluable when debugging issues or tracking down bugs.

In this article, we will explore the different ways you can view the differences between commits in Git.

### Using git diff

The simplest way to view the differences between two commits in Git is to use the `git diff` command. This command shows the differences between the current state of the repository and a previous commit.

To use `git diff`, first identify the SHA-1 hash of the commit you want to compare to the current state of the repository. You can find this hash by using the `git log` command, which displays a list of all the commits in the repository, along with their hashes.

Once you have the hash of the commit you want to compare, use the following command to view the differences between the current state of the repository and the specified commit:

```php-template
git diff <commit-hash>
```

This command will display the differences between the specified commit and the current state of the repository.

You can also use `git diff` to compare two different commits. To do this, specify the hashes of both commits:

```php-template
git diff <commit-hash-1> <commit-hash-2>
```

This command will display the differences between the two specified commits.

Here are some examples of how to use `git diff`:

Show the changes between the working directory and the index

* ```ruby
  $ git diff
  ```

Show the changes between the working directory and the last commit:

* ```ruby
  $ git diff HEAD
  ```

Show the changes between two specific commits:

* ```ruby
  $ git diff abc123..def456
  ```

Show the changes in a specific file:

* ```ruby
  $ git diff myfile.txt
  ```

Show the changes between the index and a specific commit:

$ git diff --cached def456

Show the changes between two branches:

* <pre class="language-ruby"><code class="lang-ruby"><strong>$ git diff branch1..branch2
  </strong></code></pre>

Show only the names of the changed files:

```css
$ git diff --name-only
```

When you use the `git diff` command, you get a result that shows the differences between two commits, two branches, or a commit and the working tree. The output will display lines that have been added, deleted, or modified between the two compared versions. The result will have a `+` sign in front of the lines that have been added and a `-` sign in front of the lines that have been deleted.

Here's an example of a `git diff` result:

```diff
diff --git a/file1.txt b/file1.txt
index a654321..b654321 100644
--- a/file1.txt
+++ b/file1.txt
@@ -1,3 +1,4 @@
 line 1
-line 2
+modified line 2
+added line 3
 line 4
```

In this example, we can see that `file1.txt` has been modified. The lines with `-` sign indicate that line 2 has been deleted, while the lines with `+` sign show that line 2 has been modified and line 3 has been added. Line 4 remains the same.

The `@@` line indicates which section of the file is being shown in the diff. In this example, it shows that we are looking at line 1-3 (old version) and line 1-4 (new version) of the file.

You can also use various options with the `git diff` command to customize the output, such as `--color-words` to highlight only the changed words, or `--stat` to get a summary of changes.

### Using git log

The `git log` command can also be used to view the differences between commits. By default, `git log` displays a summary of all the commits in the repository, including their hashes, commit messages, and the author and date of each commit.

To view the differences between two specific commits, use the following command:

```php-template
git log <commit-hash-1>..<commit-hash-2>
```

This command will display a summary of all the commits between the two specified hashes, along with the files that were changed in each commit.

1. Open your Git repository in your terminal/command prompt.
2. Type the following command: `git log`
3. Press Enter. This will display a log of all the commits made to the repository, starting from the most recent one.
4. You can use the arrow keys to scroll through the log. Each commit will be displayed in reverse chronological order and will include the following information:
   * commit hash: a unique identifier for the commit
   * author name and email address
   * date and time of the commit
   * commit message: a brief description of the changes made in the commit
5. To quit the log and return to the command prompt, press the `q` key.
6.  You can also use various options with the `git log` command to filter or customize the output. Here are some useful options you can use with the `git log` command:

    * `--oneline`: This option displays each commit on a single line, making the output more compact.
    * `--graph`: This option adds ASCII art depicting the branch and merge history of the repository.
    * `--author`: This option filters the output to show only commits made by the specified author.
    * `--since`: This option filters the output to show only commits made since the specified date.
    * `--until`: This option filters the output to show only commits made until the specified date.

    For example:

    * `git log --author="John Doe"`: displays the commits made by a specific author
    * `git log --since="2 weeks ago"`: displays the commits made within a certain time frame
    * `git log --oneline`: displays a condensed log with only the commit hash and message

Git log can take a revision or path arguments to specify the output history to be shown starting at the given revision or only include changes to the requested paths. Git log can take a --patch (or -p) flag to show the differences for each commit output.

In addition to the `git log` command, there are also GUI-based tools such as Gitk and GitX that allow you to view the Git history graphically. These tools can be useful for visualizing the relationships between commits and branches, and for exploring the history of a project in a more interactive way. Gitk is usually installed with Git but may need to be installed separately. GitX is for OS X.

