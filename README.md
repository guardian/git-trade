# git-trade
A demo repo for documenting and playing with various git features

## Git settings
The starting point for my git settings comes from 
[Scott Nonnenberg](https://blog.scottnonnenberg.com/better-git-configuration/). 
I didn't adopt everything, but it's a great starting point.

Some highlights are:
 - GPG signing
 - glog: shortcut to a colourful log rendition 

## Command line tools
[`git-radar`](https://github.com/michaeldfallen/git-radar) is super convenient 
for seeing the status of a repo on the command line. There are also lightweight
variants. This shows your current branch and an overview of status and stash. 

[`hub`](https://hub.github.com/) allows you to add a number of GitHub specific
commands to git such as `git pull-request` to open a PR from the command line.

## Merging vs. Rebasing
It is my opinion that when you are working on a feature branch and want to pull
in latest master you should rebase instead of merge.

I recommend that you set `ff = only` to ensure you don't accidentally merge 
(that's in Scott's settings too).

When you are doing rebasing you'll be re-writing the remote branch in a way
that violates the immutable properties that we get with merging. You should:
 - be aware of this
 - proceed with care if you're not the only person working on a branch
 - use `git push --force-with-lease` instead of `git push --force` (you might
   want to add an alias to .gitconfig - I have `pushf = push --force-with-lease`)

## Resolving conflicts
When git fails to deal with conflicts for you, it can be error prone and hard
work. There are plenty of tools to make it easier. Simon uses intelliJ. You can
set it up as a mergetool using the command line (see [here](http://brian.pontarelli.com/2013/10/25/using-idea-for-git-merging-and-diffing/)) 
but that doesn't work particularly well - it's typically easier to use it when 
you have the project open.

## Interactive rebasing
A great pull request is one that tells a story. A great story is one that has
a compelling narrative arc that doesn't jump around all over the place all of
the time. Frequently you'll want to make a change that really belongs in an
earlier commit. Interactive rebasing is the way to easily achieve this.

For example, if you want to merge a few commits together you should:
 - make all of your commits 
 - ensure your workspace is clean 
 - identify a parent commit that is earlier than any commit you want to re-write
 - run `git rebase -i <parent-commit-ref>`

You are provided with an editor in which you can make your changes. It is 
more or less self-documenting. I generally use `squash` and `fix-up` as well
as taking advantage of the ability to re-order.