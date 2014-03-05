# Informative git prompt for bash and fish
[![CodeShip](https://www.codeship.io/projects/9ae74330-8697-0131-49f1-3e77f06cd138/status)

This prompt is a port of the "Informative git prompt for zsh" which you can
find [here](https://github.com/olivierverdier/zsh-git-prompt)

A ``bash`` prompt that displays information about the current git repository.
In particular the branch name, difference with remote branch, number of files
staged, changed, etc.

(an original idea from this [blog post][]).

`gitstatus.sh` added by [AKS](http://github.com/aks).

## Examples

The prompt may look like the following: 

![Example prompt](gitprompt.png)

* ``(master↑3|✚1)``: on branch ``master``, ahead of remote by 3 commits, 1 file changed but not staged
* ``(status|●2)``: on branch ``status``, 2 files staged
* ``(master|✚7…)``: on branch ``master``, 7 files changed, some files untracked
* ``(master|✖2✚3)``: on branch ``master``, 2 conflicts, 3 files changed
* ``(master|⚑2)``: on branch ``master``, 2 stash entries
* ``(experimental↓2↑3|✔)``: on branch ``experimental``; your branch has diverged by 3 commits, remote by 2 commits; the repository is otherwise clean
* ``(:70c2952|✔)``: not on any branch; parent commit has hash ``70c2952``; the repository is otherwise clean

##  Prompt Structure

By default, the general appearance of the prompt is::

    (<branch> <branch tracking>|<local status>)

The symbols are as follows:

- Local Status Symbols
  - ``✔``: repository clean
  - ``●n``: there are ``n`` staged files
  - ``✖n``: there are ``n`` unmerged files
  - ``✚n``: there are ``n`` changed but *unstaged* files
  - ``…n``: there are ``n`` untracked files
  - ``⚑n``: there are ``n`` stash entries
- Branch Tracking Symbols
  - ``↑n``: ahead of remote by ``n`` commits
  - ``↓n``: behind remote by ``n`` commits
  - ``↓m↑n``: branches diverged, other by ``m`` commits, yours by ``n`` commits
- Branch Symbol:<br />
  	When the branch name starts with a colon ``:``, it means it's actually a hash, not a branch (although it should be pretty clear, unless you name your branches like hashes :-)

## Install

1. Clone this repository to your homedir
   e.g. ``git clone https://github.com/magicmonty/bash-git-prompt.git .bash-git-prompt``
2. Source the file ``gitprompt.sh`` from your ``~/.bashrc`` config file
3. Go in a git repository and test it!

## Configuration

1. You can use ``GIT_PROMPT_START`` and ``GIT_PROMPT_END`` to tweak your prompt

2. The default colors are defined within ``gitprompt.sh``, but may be
   overridden by copying ``git-prompt-colors.sh`` to your home directory at
   ``~/.git-prompt-colors.sh``.  This file may also be found in the same
   directory as ``gitprompt.sh``, but without the leading ``.``.

3. The current git repo information is obtained by the script `gitstatus.sh` or
   `gitstatus.py`.  Both scripts do the same thing, but the bash script is a
   tad more quick, and is used by default.  If you prefer the python script
   (possibly because you have enhanced it), simply delete or change the name of
   ``gitstatus.sh``.

4. You can define ``prompt_callback`` function to tweak your prompt dynamically.

```sh
function prompt_callback {
    if [ `jobs | wc -l` -ne 0 ]; then
        echo -n " jobs:\j"
    fi
}
```

5.  You can get help on the git prompt with the function ``git_prompt_help``.
    Examples are available with ``git_prompt_examples``.

**Enjoy!**

[blog post]: http://sebastiancelis.com/2009/nov/16/zsh-prompt-git-users/
