source code shoes

<?

include "includes/secret.inc";

    if(array_key_exists("submit", $_POST)) {
        if($secret == $_POST['secret']) {
        print "Access granted. The password for natas7 is <censored>";
    } else {
        print "Wrong secret";
    }
    }
?>

Simply go to includes/secret.inc and input the secret

bmg8SvU1LizuWjx3y7xkNERkHxGre0GS