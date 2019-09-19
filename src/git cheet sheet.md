# Git cheat sheet


## git pull

## git push

## git commit

## git add

This will tell git about files so that it will track the changes, it can also be used to add specific files to a commit without adding everything.

```bash
$ git add <files> ...
```

Can specify the files by using

- the file name
- a glob to match a set of files (ie. *.txt will match all files ending in .txt)
- all the files in the working directory (.)


## git clone

this will get a local version of the repository to work on

```bash
$ git clone <url> [name]

```

## git status



## git merge

## git checkout

## git branch

## git reset ?

## git revert ?

## git restore (new) ?

## git switch (new)

## git rebase


Reapply all of the commits from one branch onto the top of another branch. This is useful if you want to move your feature branch commits to the after falling behind master.

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