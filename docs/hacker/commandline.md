# The command line

=== "Visual"
    <iframe width="560" height="315" src="https://www.youtube.com/embed/2PGnYjbYuUo" end=120 frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

=== "Kinesthetic"
    If you want to get a hands on free guide, but don't want to have to download a terminal emulator, try this guide:

    [https://www.learnshell.org/](https://www.learnshell.org/)

## Getting around

To get around in the terminal, you can use the `cd` command.
Usually, when you open your terminal, the directory you're in is called your **home directory**.

The home directory differs on operating systems and your user.
On Linux and macOS, it's `/home/<username>`. On Windows, it's `C:\Users\<username>`.

Throughout this guide, we will shorten the home directory to `~/`.

To go into a different path, run `cd`, and then the path.
This can be a **relative path** or an **absolute path**.

#### Relative paths vs. absolute paths

**Relative paths** are paths that are *relative* to the directory you are currently in.
    - Example: if I was in `~/trans`, and ran `cd rights`, I would end up in `~/trans/rights`.

On the other hand, **absolute paths** are just the full path that you wish to go to.
    - Example, if I was in, `~/human`, and I wanted to go to `~/rights`, I could run `cd ~/rights`, and go there straight away.

##### Path tricks

In paths, `..` is a shortcut for previous directory, and `.` for current directory.
    - Example: `~/a/../b/./file` resolves to `~/b/file`.

**Try it yourself**: What does `~/one/three/.././../one/././../two` resolve to?

