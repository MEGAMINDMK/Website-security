filter_var <a href="https://www.w3schools.com/php/func_filter_var.asp">method</a> <a href="https://www.php.net/manual/en/filter.filters.validate.php">types</a><br>
mysqli_real_escape_string <a href="https://www.w3schools.com/php/func_mysqli_real_escape_string.asp">method</a><br>
htmlspecialchars <a href="https://www.w3schools.com/php/func_string_htmlspecialchars.asp">method</a><br>
urlencode <a href="https://www.geeksforgeeks.org/php-urlencode-function/">method</a><br>

# Making links not being displayed when click on link
```
<span data-href="example.php">example</span>
<script src="hideurlfrombrowsertaskbar.js"></script>
```

# Prevent xss javscript 
```
<script type="text/javascript" src="xss.js"></script>
<input id="search" onchange="return trim(this)" class="box">
```

# Disable inspect element
```
<script src="disableinspect.js"></script>
```

# Disbale context menu, dragstart, selectstart
```
<body oncontextmenu="return false" ondragstart="return false" onselectstart="return false">
```

# csrf token prevention
```
<?php include "csrf.php";?> 
<input type="hidden" name="csrf" value="<?php echo $csrf ?>">
```
# salt
```
$password = 'abcdefg';
 $salt = 'anythingyouwant_';
 $pw_hash = md5($salt.$password);
 echo $pw_hash;
 ```

# Password Encryption & Decryption method 1
``` 
// Store a string into the variable which
// need to be Encrypted
$simple_string = "i am megamind";  
// Display the original string
echo "Original String: " . $simple_string . "\n"; 
// Store cipher method
$ciphering = "BF-CBC";  
// Use OpenSSl encryption method
$iv_length = openssl_cipher_iv_length($ciphering);
$options = 0;  
// Use random_bytes() function which gives
// randomly 16 digit values
$encryption_iv = random_bytes($iv_length);  
// Alternatively, we can use any 16 digit
// characters or numeric for iv
$encryption_key = openssl_digest(php_uname(), 'MD5', TRUE);  
// Encryption of string process starts
$encryption = openssl_encrypt($simple_string, $ciphering,
$encryption_key, $options, $encryption_iv); 
// Display the encrypted string
echo "<br>Encrypted String: " . $encryption . "\n"; 
outputs: rFhgIKm0M5e2tutVqyB99A== 
// Decryption of string process starts
// Used random_bytes() which gives randomly
// 16 digit values
$decryption_iv = random_bytes($iv_length);
// Store the decryption key
$decryption_key = openssl_digest(php_uname(), 'MD5', TRUE); 
// Descrypt the string
$decryption = openssl_decrypt ($encryption, $ciphering,
$decryption_key, $options, $encryption_iv);
// Display the decrypted string
echo "<br>Decrypted String: " . $decryption;
outputs: i am megamind
```

# Password Encryption & Decryption method 2
```
$string = "i am pro";
echo $string;
echo "<br>";
$base64_encode = base64_encode($string);
echo $base64_encode; // outputs: aSBhbSBwcm8=
echo "<br>";
$base64_decode = base64_decode($base64_encode);
echo $base64_decode; // outputs: i am pro
```

# Password Encryption & Decryption match method 1
```
$hash=password_hash("rasmuslerdorf", PASSWORD_DEFAULT);
if (password_verify('rasmuslerdorf', $hash)) {
    echo 'Password is valid!';
} else {
    echo 'Invalid password.';
}
```


# Password Encryption & Decryption match method 2
```
$hash = '$2y$07$BCryptRequires22Chrcte/VlQH0piJtjXl.0t1XkA8pw9dMXTpOq';

if (password_verify('rasmuslerdorf', $hash)) {
    echo 'Password is valid!';
} else {
    echo 'Invalid password.';
}
```
