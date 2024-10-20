# Bandit Level 31 → Level 32
## Level Goal

There is a git repository at ssh://bandit31-git@localhost/home/bandit31-git/repo via the port 2220. The password for the user bandit31-git is the same as for the user bandit31.

Clone the repository and find the password for the next level.
Commands you may need to solve this level

> git


### Solution

The readme files contains instruction on how to get the next pass. We have to push a file called key.txt containing the string "May I come in?" to master. After my first attempt failed, I realized there was a .gitignore file including *.txt. After removing that I manage to successfully push the key.txt to the remote repo.

```
remote: ### Attempting to validate files... ####
remote: 
remote: .oOo.oOo.oOo.oOo.oOo.oOo.oOo.oOo.oOo.oOo.
remote: 
remote: Well done! Here is the password for the next level:
remote: 3O9RfhqyAlVBEZpVb6LYStshZoqoSx5K 
remote: 
remote: .oOo.oOo.oOo.oOo.oOo.oOo.oOo.oOo.oOo.oOo.
remote: 

```