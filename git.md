# git memo


### initialize a project, in an new empty directory

```bash
git init
```


### check the status

```bash
git status
```


### add a file to the staging area, so that git can track changes in it

```bash
git add <filename1> [<filename2> ...]
```


### select only modifications you want to add in a commit

```bash
git add --patch [<filename> ...]
```


### check the differences between the working directory and the staging area

```bash
git diff <filename>
```


### use git log to see differences between your branches

```bash
git log --oneline <your-branch>..remote/<branch>
```

```bash
git log --oneline dev..origin/dev
```


### commit changes (-m is for commenting the commit)

Comments must be :

- in quotation mark
- written in present tense
- brief, < 50 characters

```bash
git commit -m "Complete first line of dialogue"
```


### show commits chronologically

```bash
git log
```


### See the HEAD commit

commit you are currently on is known as the HEAD commit. In many cases,
the most recently made commit is the HEAD commit.

```bash
git show HEAD
```


### Discards changes in the working directory

```bash
git checkout HEAD <filename>
```


### Reset the file in the staging area

*to be the same as the HEAD commit*
This does not discard file changes from the working directory, it just
removes them from the staging area

#### unstages file changes in the staging area:

```bash
git reset HEAD <filename>
```

##### changes you did after (remember HEAD is the most recent commit)

```bash
git reset <shasum>
```

### which branch am I on

```bash
git branch
```


### create a new branch (no withe space in branch's name)

```bash
git branch <new_branch>
```


### switch to the new branch

```bash
git checkout <new_branch>
```

### include all the changes made to the <new_branch> ON the master branch

```bash
git merge <new_branch>
```

trough this, you update master with the changes made on "new_branch"
(master is the receiving branch)

while merging, if 2 files are in conflict each other in 2 branches, ex:


```bash
<<<<<<< HEAD
master version of line
=======
fencing version of line
>>>>>>> fencing
```

**edit the conflictual file**

deleting what's needed (git marks too !), then

```bash
git add <filename>
```


### delete a branch:

```bash
git branch -d <branch_name>
```


### clone a repository

git will call the remote_location as "origin"

```bash
git clone <remote_location> [<clone_name>]
```


### see a list of a Git project's remotes:

```bash
git remote -v
```


### see changes made to a file, every commits about this file only

```bash
git log --follow <file>
```


### show the commits on branchA that are not on branchB

```bash
git log branchB..branchA
```


### show the diff of what is in branchA that is not in branchB

```bash
git diff branchB...branchA
git diff <SHA> <another SHA>
```


### show any object in Git in human-readable format

```bash
git show [SHA]
```


see if changes have been made to the remote and bring the
changes down to your local copy:
(This command will not merge changes from the remote into your local
repository. It brings those changes onto what's called a remote branch)

```bash
git fetch
```


Even though new commits have been fetched to your local copy, those
commits are on the origin/master branch. Your local master branch has
not been updated yet, so you can't view or make changes to any of the
work that's benn added.

To integrate changes done on master/origin to our local/master, we need
to merge (don't forget to be in the right directory !):

```bash
git merge origin/master
```


Now that you've merged origin/master into your local master branch,
you're ready to contribute some work of your own. The workflow for Git
collaborations typically follows this order:

1. Fetch and merge changes from the remote
2. Create a branch to work on a new project feature
3. Develop the feature on your branch and commit your work
4. Fetch and merge from the remote again (in case new commits were made while you were working)
5. Push your branch up to the remote for review

Steps 1 and 4 are a safeguard against merge conflicts, which occur when
two branches contain file changes that cannot be merged with the git
merge command.

```bash
cd my-local repo
git branch <branch_name>
git checkout <branch_name>
vim <file_name>
git add <file_name>
git commit -m "changes made"
git push origin <branch_name>
```


now, the owner of the origin repo can review the changes you made, and merge or not



## The seven rules of a great Git commit message

[chris.beams.io](https://chris.beams.io/posts/git-commit/)

1. Separate subject from body with a blank line
2. Limit the subject line to 50 characters
3. Capitalize the subject line
4. Do not end the subject line with a period
5. Use the imperative mood in the subject line
6. Wrap the body at 72 characters
7. Use the body to explain what and why vs. how


### Exemple de commit message


```bash
Summarize changes in around 50 characters or less

More detailed explanatory text, if necessary. Wrap it to about 72
characters or so. In some contexts, the first line is treated as the
subject of the commit and the rest of the text as the body. The
blank line separating the summary from the body is critical (unless
you omit the body entirely); various tools like "log", "shortlog"
and "rebase" can get confused if you run the two together.

Explain the problem that this commit is solving. Focus on why you
are making this change as opposed to how (the code explains that).
Are there side effects or other unintuitive consequences of this
change? Here's the place to explain them.

Further paragraphs come after blank lines.

- Bullet points are okay, too
- Typically a hyphen or asterisk is used for the bullet, preceded
  by a single space, with blank lines in between, but conventions
  vary here

If you use an issue tracker, put references to them at the bottom,
like this:

Resolves: #123
See also: #456, #789
```


### Deuxieme exemple (vrai commit)


```bash
# https://github.com/bitcoin/bitcoin/commit/eb0b56b19017ab5c16c745e6da39c53126924ed6


commit eb0b56b19017ab5c16c745e6da39c53126924ed6
Author: Pieter Wuille <pieter.wuille@gmail.com>
Date:   Fri Aug 1 22:57:55 2014 +0200

   Simplify serialize.h's exception handling

   Remove the 'state' and 'exceptmask' from serialize.h's stream
   implementations, as well as related methods.

   As exceptmask always included 'failbit', and setstate was always
   called with bits = failbit, all it did was immediately raise an
   exception. Get rid of those variables, and replace the setstate
   with direct exception throwing (which also removes some dead
   code).

   As a result, good() is never reached after a failure (there are
   only 2 calls, one of which is in tests), and can just be replaced
   by !eof().

   fail(), clear(n) and exceptions() are just never called. Delete
   them.
```



## How to create and apply a patch with Git

[www.devroom.io](https://www.devroom.io/2009/10/26/how-to-create-and-apply-a-patch-with-git/)

** Before you start **

To make creating patches easier, there are some common git practices you
should follow. It’s not necessary, but it will make your life easier.
If you fix a bug or create a new feature – do it in a separate branch!
Let’s say you want to create a patch for my imdb gem. You should clone my
repository and create a new branch for the fix you have in mind. In this sample
we’ll do an imaginary fix for empty posters

```bash
git clone git://github.com/ariejan/imdb.git
cd imdb
git checkout -b fix_empty_poster
```


Now, in the new "fix_empty_poster" branch you can hack whatever you need to fix.
Write tests, update code etc. etc.
When you’re satisfied with all you changes, it’s time to create your patch.
FYI: I’m assuming you made a few commits in the fix_empty_poster branch and
did not yet merge it back in to the master branch.



### Creating the patch

```bash
git format-patch master --stdout > fix_empty_poster.patch
```


This will create a new file fix_empty_poster.patch with all changes from the
current (fix_empty_poster) against master. Normally, git would create a
separate patch file for each commit, but that’s not what we want. All we need
is a single patch file.
Now, you have a patch for the fix you wrote. Send it to the maintainer of the
project …



### Applying the patch

… who will apply the patch you just sent! But, before you do that, there are
some other steps you should take.
First, take a look at what changes are in the patch. You can do this easily
with git apply


```bash
git apply --stat fix_empty_poster.patch
```


Note that this command does not apply the patch, but only shows you the stats
about what it’ll do. After peeking into the patch file with your favorite
editor, you can see what the actual changes are.

Next, you’re interested in how troublesome the patch is going to be. Git allows
you to test the patch before you actually apply it.


```bash
git apply --check fix_empty_poster.patch
```


If you don’t get any errors, the patch can be applied cleanly. Otherwise you
may see what trouble you’ll run into. To apply the patch, I’ll use git am
instead of git apply. The reason for this is that git am allows you to sign off
an applied patch. This may be useful for later reference.


```bash
git am --signoff < fix_empty_poster.patch
Applying: Added specs to test empty poster URL behaviour
Applying: Added poster URL as part of cli output
```


Okay, patches were applied cleanly and your master branch has been updated. Of
course, run your tests again to make sure nothing got borked.
In you git log, you’ll find that the commit messages contain a “Signed-off-by”
tag. This tag will be read by Github and others to provide useful info about how
the commit ended up in the code.

That’s all folks!
