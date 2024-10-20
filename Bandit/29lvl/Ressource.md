# Bandit Level 28 → Level 29

## Level Goal

There is a git repository at ssh://bandit28-git@localhost/home/bandit28-git/repo via the port 2220. The password for the user bandit28-git is the same as for the user bandit28.

Clone the repository and find the password for the next level.
Commands you may need to solve this level

> git

### Solution
Clone the repo in the same fashion as the previous level.
Once in the repo, we can cat the README and quickly realize that the password is hidden.
```
bandit28@bandit:/tmp/tmp.OyoXcTiKdd/repo$ cat README.md 
# Bandit Notes
Some notes for level29 of bandit.

## credentials

- username: bandit29
- password: xxxxxxxxxx
```
When using git log, we can see this repo has 3 commits. One original one, a second where the comments that "missing data has been added", and a third current one "fixing the info leak". If we revert the commit using *git checkout {commit_number}* we can probably find the password.

```
bandit28@bandit:/tmp/tmp.OyoXcTiKdd/repo$ git checkout 3621de89d8eac9d3b64302bfb2dc67e9a566decd
Previous HEAD position was 817e303 fix info leak
HEAD is now at 3621de8 add missing data
bandit28@bandit:/tmp/tmp.OyoXcTiKdd/repo$ cat README.md 
# Bandit Notes
Some notes for level29 of bandit.

## credentials

- username: bandit29
- password: 4pT1t5DENaYuqnqvadYs1oE4QLCdjmJ7
```