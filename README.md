# git-trade
A demo repo for playing with various git features

# Merging vs. Rebasing
It is my opinion that when you are working on a feature branch and want to pull
in latest master you should rebase instead of merge.

# Resolving conflicts
When git fails to deal with conflicts for you, it can be error prone and hard
work. There are plenty of tools to make it easier. Simon uses intelliJ. You can
set it up as a mergetool using the command line (see [here](http://brian.pontarelli.com/2013/10/25/using-idea-for-git-merging-and-diffing/)) 
but that doesn't work particularly well - it's typically easier to use it when 
you have the project open.