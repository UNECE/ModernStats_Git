---
title: "Setting up Git"
teaching: 5
exercises: 0
questions:
- "How do I set up Git?"
objectives:
- "Configure basic settings in Git"
keypoints:
- "Use `git config` with the `--global` option to configure a user name, email address, editor, and other preferences once per machine."
- "Use `--local` in place of `--global` within a repository to set repository specific changes."
---

Before we start using Git for the first time on a new computer, there are some things we need to set up. In this lesson, we will:

- Add a name and email address
- Set the text editor used for writing commit messages
- Understand the difference between `--global` and `--local` configuration
- View/confirm configuration settings

We will be using Git Bash, the command line interface for Git.

## Configure Name and Email

An important first step in using Git is adding your name and email. This information will be attached to [commits](https://unece.github.io/ModernStats_Git/05-track_changes/index.html), [branches](https://unece.github.io/ModernStats_Git/09-collaborating/index.html), and other changes you make in the future. This identifiability and accountability for code changes is one of the key benefits to using Git.

At the Git Bash prompt, enter the following, substituting your full name for the name in quotation marks after `user.name` and your email for the email address following `user.email`.

```bash
$ git config --global user.name "Jane Doe"
$ git config --global user.email "doe_jane@agency.gov"
```

Your situation may vary, but if you are writing code in your official capacity and using an agency repository, you will most likely want to use your official email address and the one associated with your account on GitHub, GitLab, or other code sharing site.

## Configure Text Editor

> This is optional. By default, Git Bash will use the Vim text editor.

There are many different Git clients and ways of interacting with Git on your computer. Some clients have a full user interface that you use for selecting files to stage for commits and authoring commit messages. Others, like Git Bash, have a command line interface so when you want to write a lengthy commit message, it needs to call up a text editor.

:::::::::::::::::::::::::::::::::::::::::  callout

### Different Ways to Author Commit Messages

As you will learn in [a later lesson](https://unece.github.io/ModernStats_Git/05-track_changes/index.html), once you make updates to your code, you will want to make a snapshot of those updates called a commit and provide an informative message that describes what was changed. This message can be short and be written on the command line (e.g., `git commit -m "Update README.md"`). Sometimes however, you will want to write a longer, multi-line commit message. You can do this by entering `git commit` on the command line. This will bring up the text editor you have configured as your default.

::::::::::::::::::::::::::::::::::::::::::::::::::

The default text editor for Git Bash is Vim which has a reputation for being difficult, especially for new users. So you may want to change to something easier to use or something you are more familiar with (e.g., your favorite text editor).

To switch to one of the following editors in the tables below, you can use the associated configuration commands.

The nano text editor is packaged with Git Bash and Notepad is included in the Windows operating system.

| Editor                                | Configuration command | 
| :-----------                          | :------------------------------ |
| nano                                  | `$ git config --global core.editor "nano -w"`                      | 
| Notepad (Win)                         | `$ git config --global core.editor "c:/Windows/System32/notepad.exe"`                      | 

The text editors below are not available by default, but you may be available to you. Setup for these is more complex because it requires providing a filepath to the program executable which may not be the same for everyone.

| Editor                                | Configuration command | 
| :-----------                          | :------------------------------ |
| Notepad++ (Win, 64-bit install)       | `$ git config --global core.editor "'c:/program files/Notepad++/notepad++.exe' -multiInst -notabbar -nosession -noPlugin"`                      | 
| Sublime Text (Win, 64-bit install)    | `$ git config --global core.editor "'c:/program files/sublime text 3/sublime_text.exe' -w"`                      |
| VS Code                               | `$ git config --global core.editor "code --wait"`                      | 

If you ever want to switch back to Vim as the default, you can run the following command.

| Editor                                | Configuration command | 
| :-----------                          | :------------------------------ |
| Vim                                   | `$ git config --global core.editor "vim"`                      | 

:::::::::::::::::::::::::::::::::::::::::  callout

### Exiting Vim

Vim is surprisingly difficult to exit from. If you wish to exit a session without saving your changes, press <kbd>Esc</kbd> then type `:q!` and hit <kbd>Enter</kbd> or <kbd>↵</kbd>.
If you want to save your changes and quit, press <kbd>Esc</kbd> then type `:wq` and hit <kbd>Enter</kbd> or <kbd>↵</kbd>.

::::::::::::::::::::::::::::::::::::::::::::::::::

## `--global` vs. `--local`

In the code samples above, we have used the `--global` flag. These are the settings Git will use for all repositories on your computer. As your use of Git becomes more complex, you may wish to have different configuration settings for different repositories. This is when you might use the `--local` flag. `--local` allows you to set configuration for specific repositories.

To set local configuration, open Git Bash and navigate to the repository you want to configure. You can then use the commands above, but substitute `--local` for `--global`.

For example, if you want to set a different name or email address for a specific project, you can do so with commands like those below.

```bash
$ git config --local user.name "Jane R Doe"
$ git config --local user.email "janedoe@example.com"
```

These settings will override the `--global` configuration settings for that repository only.

## View/Confirm Configuration

You may wish to check your configuration settings.

To see all configuration settings, you can use the following command. If you are in a repository, this will show all global and local configuration settings.

```bash
$ git config --list
```

To view global settings only (*Note:* This command can be run anywhere):

```bash
$ git config --global --list
```

To view local settings only (*Note:* This has to be run while in a repository):

```bash
$ git config --local --list
```

To view specific settings, include the setting name. For example, to view the email address configuration setting:

```bash
$ git config user.email 
```

## Other Configuration Settings

There are other, optional configuration settings you may wish to change. Review Git documentation and consult with others on your team about other settings.

{% include links.md %}