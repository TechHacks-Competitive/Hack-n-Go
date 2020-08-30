# Version Control w/ Git

Version control is a crucial tool for anyone taking part in a hackathon.
Without VCS, working with others would be close to impossible.
By far the most popular VCS out there is Git.
Git is special that in that it is completely decentralized and follows a branching model, allowing for near-flawless collaboration.

Guide available in two verions:

=== "Visual"
    <iframe width="560" height="315" src="https://www.youtube.com/embed/SWYqp7iY_Tc" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

=== "Kinesthetic"
    > Start your own repo, often times, the best way to learn is by going out and doing it.

    > Learn from experience, that's how we all did it. We didn't have any of those fancy guides on how to start, we sorta knew what to do from trial and error.

    > Your mission is to create a 'Hello-World' repository on Github and commit and push and pull changes.


## Setting up Git

Git is available on all major platforms (Windows/MacOS/Linux/Unix).
Head over to the official download page at <https://git-scm.com/downloads> and select the option for your desired platform.

Once Git is installed on your system you'll need to set your global username and email.
This information will be cryptographically tied to all commits you make.

```bash
# Set your global Git username
git config --global user.name  "John Smith"

# Set your global Git email
git config --global user.email "johnsmith@example.com"
```

## Your First Repo

To begin using Git you first must create a Git repository.
You can either turn an existing directory into a Git repo or create a new Git repo.

```bash
git init example
```

The following command created a Git repo named `example` in the current working directory.
If we run `#!bash tree -L 1 -a example` we will see that the `example` directory now has a `.git` folder in it's root.

```bash
$ tree -L 1 -a example
example
└── .git
```

The actual git repo is stored inside of the `.git` folder.
Don't mess around with the `.git` directory unless you know what you are doing.
The root of the `example` directory will be our working directory.

To start a project you'll need to create a initial commit.
Lets echo "Hello World" to a README file.

```bash
echo "Hello World" > README.md
```

Then lets stage the file to be committed and write our first commit.

```bash
git add README.md
git commit -m "Initial commit"
```

To see the commit history run `#!bash git log`.
It will then open the repo commit history in your system pager (most likely `less`).

## Adding a Remote

Lets say you want to collaborate with someone.
You some way to share your work.
This is where Git remotes come in.

To add an existing remote you'll need to get your remote upstream url.

```bash
git remote add origin git@remote:example.git
```

Here we are adding a remote called `origin` at the address `git@remote:example.git`.

To push your existing work to this remote you'll need to run `#!bash git push`.

```bash
git push origin master
```

Here we are pushing our local branch `master` to the remote `origin`.

## Cloning a Repo

Sometimes projects already exist, so you'll need to actually get work from the upstream.
Thankfully Git streamlines this process and it is really easy to clone existing repos.

```bash
git clone git@remote:example.git
```

What the following command will do is clone the `example` repo to a directory called `example` in the current working directory.
Now if you were to `#!bash cd` into the `example` directory you would see all the latest work on the `master` branch (or whatever the main upstream branch is).

## Branching & Merging

Software development is almost never linear in the real world.
Often times you end up with multiple programmers working on the same files at the same time or maybe changes are experimental.
Either way, Git allows to branching to let you work in your own little isolated environment.

```bash
git checkout -b new-feature
```

The following command creates a new branch called `new-feature`.
This branches history is now independent of the `master` branch, but still has parent commits on the `master` branch.

Lets create a new commit where we append something to `README.md`.

```bash
echo "Goodbye Cruel World" >> README.md
```

If we check the status of the Git repo with `#!bash git status` we will see that `README.md` has changes that are unstaged.
Once again, stage the file and create a new commit.

```bash
git add README.md
git commit -m "commit 2"
```

Now if we checkout our `master` branch with `#!bash git checkout master` and cat out `README.md` with `#!bash cat README.md` we will see that the line "Goodbye Cruel World" does not exist.
To merge our changes on the `new-feature` branch we run a `#!bash git merge`.

```bash
git merge --no-ff new-feature
```

What the command does is create a merge commit, the `--no-ff` flag tells git to make an explicit merge commit, this will make viewing history a lot more easy.

## Pushing/Pulling Work

Before pushing your work to a Git remote it is a good idea to see if there are any updates on the upstream branches with `#!bash git fetch`.
If there are any commits not in your local repo, Git will actually *require* you to pull in the changes with `#!bash git pull`.

To push your work to a Git remote simply run `#!bash git push origin master`.
This will push your `master` branch to the remote's `master` branch.
You can also set `origin` as the default push target for the `master` branch as to save yourself some typing.
Run `#!bash git push --set-upstream origin master`.
From now on you will be able to push to origin with just `#!bash git push`.

## Taking it Further

These are of course only the basics.
Like most tools, the best way to learn is to just use it and figure it out along the way.
To learn more read the [Pro Git Book 2nd Edition](https://git-scm.com/book/en/v2), free to read on the official homepage of the Git project.
