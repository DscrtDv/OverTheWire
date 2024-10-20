# Bandit Level 27 → Level 28
## Level Goal

There is a git repository at ssh://bandit27-git@localhost/home/bandit27-git/repo via the port 2220. The password for the user bandit27-git is the same as for the user bandit27.

Clone the repository and find the password for the next level.

Commands you may need to solve this level
> git

### Solution

make temp dir to clone repo
```
git clone ssh://bandit27-git@localhost:2220/home/bandit27-git/repo
cd repo
cat README
Yz9IpL0sBcCeuG7m9uQFt8ZNpS4HZRcN
```