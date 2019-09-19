# Advanced git


This is a demo repositository used for the Fall 19 GCC presentation on Advanced git usage. 

This repo was originally from the [SOCS Gitlab](https://gitlab.socs.uoguelph.ca/gcc/rebase-test) instance
but was moved here to keep it availible without a Guelph login. 

This repository contains instructions on how to create and add an `ssh key` to gitlab and github in [git-ssh-setup.pdf](git-ssh-setup.pdf). This also contains the [GitHub Cheetsheet](git-cheat-sheet-education.pdf). 



# Test Rebasing

This repo has 3 branches

- master
- another_branch
- new_branch



The `new_branch` does not have any conflicting changes with the `master` branch and 
is where we will start for the rebase.

The `another_branch` has conflicting changes with the file `file.txt` with the master branch and we will rebase 
that one next. 


## How to rebase


To perform the rebase make sure you have checkout the branch that you want to move and that you have a 
local version the other branch as well. (This can be acompleshed by performing a `git checkout` and a `git pull`). 
Then go back to the topic branch and run `git rebase master`, this will reapply the commits to the top of master. 





Reapply all of the commits from one branch onto the top of another branch. This is useful if you want to move your 
feature branch commits to the after falling behind master.

```bash
$ git rebase <branch>
```


```
		   topic
			 v
		 F - G 
		/
A - B - C - D - E
	 			 ^
	 			master
```

If the current branch is `topic` and you run `git rebase master`
then you would get 

```
		   			  topic
			 		   v
		   		  F' - G' 
				 /
A - B - C - D - E
	 			 ^
	 			master
```



## Oh no I have a conflict!!!


If you have a conflict you can run ` git am --show-current-patch` to show where the conflicts are, then open a text
editor and fix the changes. Once the changes are done you can re-add the files using `git add <file>` then resume 
the rebase using `git rebase --continue`. Hurrah it is now fixed!!


Now that you have completed the rebase you will have to push it back to the remote repository. Normally you would 
do a `git push`, but in this case that will fail because a rebase will rewrite the history meaning that all of you
commits are now different than the ones on the server and yours will be rejected. 

You can use the flag `--force-with-lease` to force the push as long as the remote does not have any commits newer 
than the ones in the rebase. 
