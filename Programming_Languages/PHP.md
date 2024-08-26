### Description
PHP is a back-end server programming language
To use PHP use the opening and closing PHP tags. 
```
<?php
echo "Hello Worlds";
?>
```
Also ensure that all statements end with a semicolon ; to illustrate the end of the statement.
### Data Types
string : which consist of multiple characters
integers : includes numbers
boolean : false(0) or true(1)
float : numbers with decimal numbers
### Variables 
To declare variables use the dollar sign followed by the variable name.
```
<?php
$name = "Gard Alson";
echo name;
?>
```
There are two type of variables namely :
* user-defined variables
* super global variables
***user-defined variables*** these are variables that are declared by the user such as show below.
```
<?php
$name = "Gard Alson";
echo name;
?>
```
***super global variables*** these are variables that are in built within the programming language.
```
$_REQUEST[""];
$_POST[""];
$_GET[""];
$_SERVER[""];
$_COOKIE[""];
$_SESSION[""];
$_FILE[""];
```
each of the above super global has it's own function.

### Concatenation of variables and strings

```
$name = "Linux Ubuntu"
echo "Hello there Mr. " . $name; 
```

## Updating data in the database from website

```
UPDATE tableName SET columName = $varialbeName, columName = $varialbeName,   WHERE id = $variableName;

//submit data
//use prepeare statement
//bindParam

```



### SESSIONS
sessions is a unique way for a browser to identify the client. Usefull many clients/users for your website.
To use session use the following syntax.
```
<?php
    session_start()
?>
``` 

Setup config.php file used for setting the session paramets:
```
<?php
    init.set("session.use_only_cookies", 1);
    init.set("session.use_strict_mode", 1);

//setting session parameters
session_set_cookie_params([
    "lifetime"=>1800,
    "domain"=>"localhost", //set the domain of your website, godaddy, mylifepathway
    "path"=>"/",
    "secure"=>true, //ensure connection is htttps (secure only)
    "httponly"=>true // ensure no scripting can be performed on the client side
]);

session_start(); // add the below function to enhance security of the session
session_regenate_id(true); //regenerate a new id for the current id, add security as attackers stolen id are not used
```

// checks if session is regenerated and if not regenerate. if regenerated check if it's greater than the given interval, if greater regenerate session_id.

```
session_start();
$interval = 60 * 30;
if (!isset($_SESSION["last_regeneration"]))
{
    //false execute below
    session_regenerate_id(true);
    $_SESSION["last_regeneration"]  = time();
}else
{
    $interval = 60 * 30;

    if (time() - $_SESSION["last_regeneration"] >= $interval)
    {
        session_regeneration_id(true);
        $_SESSION["last_regeneration] = time();
    }
}