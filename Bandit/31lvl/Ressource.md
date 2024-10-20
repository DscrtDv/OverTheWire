# Bandit Level 30 → Level 31
## Level Goal

There is a git repository at ssh://bandit30-git@localhost/home/bandit30-git/repo via the port 2220. The password for the user bandit30-git is the same as for the user bandit30.

Clone the repository and find the password for the next level.
Commands you may need to solve this level

> git

### Solution
When navigating the .git folder, I noticed something odd in the packed-refs file, initially gathering hashes from branches and commits.

```
bandit30@bandit:/tmp/tmp.OddbZ3Yjg7/repo/.git$ cat packed-refs 
# pack-refs with: peeled fully-peeled sorted 
acfc3c67816fc778c4aeb5893299451ca6d65a78 refs/remotes/origin/master
84368f3a7ee06ac993ed579e34b8bd144afad351 refs/tags/secret
```
Here we can see that the first hash represents the one and only commit, but theres also this *refs/tags/secret/".
It isn't listed in the git log, I had a hard time identifying what object this hash was representing. I tried checkout on it, treating it as a commit, but no luck. Although when using the command:
```
bandit30@bandit:/tmp/tmp.OddbZ3Yjg7/repo/.git/refs/tags$ git show 84368f3a7ee06ac993ed579e34b8bd144afad351
fb5S2xb7bRyFmAvQYQGEqsbhVyJqhnDy
```
It returned the password to the next level.
According to the manual:


>DESCRIPTION
Shows one or more objects (blobs, trees, tags and commits).
For commits it shows the log message and textual diff. It also presents the merge commit in a
special format as produced by git diff-tree --cc.
For tags, it shows the tag message and the referenced objects.
For trees, it shows the names (equivalent to git ls-tree with --name-only).
For plain blobs, it shows the plain contents.
Some options that git log command understands can be used to control how the changes the
commit introduces are shown.
This manual page describes only the most frequently used options.

A Git blob (binary large object) is the object type used to store the contents of each file in a repository. The file's SHA-1 hash is computed and stored in the blob object. These endpoints allow you to read and write blob objects to your Git database on GitHub. Blobs leverage these custom media types.

[Git objects reference](https://git-scm.com/book/en/v2/Git-Internals-Git-Objects)