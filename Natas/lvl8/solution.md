<?php

$secret = "3d3d516343746d4d6d6c315669563362";

function encodeSecret($secret) {
    return bin2hex(strrev(base64_encode($secret)));
}

function decodeSecret($secret) {
    return base64_decode(strrev(hex2bin($secret)));
}

echo decodeSecret($secret)

?>

Take function encode secret, decode it, input it, boom.


secret: oubWYf2kBq
ZE1ck82lmdGIoErlhQgWND6j2Wzz6b6t