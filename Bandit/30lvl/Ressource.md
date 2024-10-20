# Bandit Level 29 → Level 30
## Level Goal

There is a git repository at ssh://bandit29-git@localhost/home/bandit29-git/repo via the port 2220. The password for the user bandit29-git is the same as for the user bandit29.

Clone the repository and find the password for the next level.
Commands you may need to solve this level

> git

### Solution

When catting the README file for the first time, we can see "no password in production".
If we list the local branches
```
git branch
```
We can only see the origin, although when listing the remote branches, we can find some others.
```
bandit29@bandit:/tmp/tmp.UDUlYsfSXR/repo$ git branch -r
  origin/HEAD -> origin/master
  origin/dev
  origin/master
  origin/sploits-dev
bandit29@bandit:/tmp/tmp.UDUlYsfSXR/repo$ git checkout origin/dev 
bandit29@bandit:/tmp/tmp.UDUlYsfSXR/repo$ git status
HEAD detached at origin/dev
nothing to commit, working tree clean
bandit29@bandit:/tmp/tmp.UDUlYsfSXR/repo$ cat README.md 
# Bandit Notes
Some notes for bandit30 of bandit.

## credentials

- username: bandit30
- password: qp30ex3VLz5MDG1n91YowTv4Q8l7CDZL
```