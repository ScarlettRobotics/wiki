# Git
Git is what is known as a version control system. It allows for multiple people to work together on a single project, syncronizing changes, and merging changes to a central copy of the code.

To get started with git:
1. Install git on your computer
+++Windows
Install [git-scm](https://git-scm.com/)

Launch the file and follow the graphical installation steps. There are a lot of options, but the defaults should be fine for you.
+++MacOS
run `git --version` in your terminal. If you don't already have it installed, a prompt will appear to install it. SImply follow the on-screen instructions.
+++Linux
Install the `git` package using your package manager.

Debian (and derrivatives): `sudo apt install git`
Arch Linux (and derrivatives): `sudo pacman -S git`
Fedora (and derrivatives): `sudo dnf install git-all`
LFS & Gentoo: You're on your own
+++

2. Clone the git repository for the team code. This changes every year. If you are unsure as to the repo url, ask the code team head.

`git clone <url> (location)`. Note that `<url>` is required, while `(location)` is optional

3. The code is now on your computer. You can now open the code in Intellij Idea

[!ref](intellij.md)