This is my notes through [Codecademy PHP Course](https://www.codecademy.com/learn/php)

# Introduction to PHP

## Meet PHP

PHP can do all sorts of things:
- Evaluate data sent from a browser
- Talk to databas
- Send and receive cookies
- Build dynamic webpages
- ...

PHP code can be inserted inside HTML, in a `<?php ?>` tag:

```php
// index.php
<p>
  <?php // PHP code goes inside this tag
  $welcome = "Hello World"; // semicolon at the end of every statements
  echo $welcome;
  ?>
</p>
```

This looks working like JS. However PHP run on the server, not the browser. This means I can access infos on the DB, run server side calculs and tasks and custom build HTML before sending it and.

## Syntax

### Echo

`echo` outputs strings.

`.` concantenate strings in the same way `+` does in JS: `echo '"Hello,"." "."world"."!";`. Looks like `,` works too (to confirm).

`echo 3 * 2;` works too.

`print` looks to do the same job (to confirm)


### Variables

All variables starts with `$`:
```php
$myName = "Camille";
$myAge = 28;

echo $myName; // Camille
echo $myAge; // 28

unset($myAge) // remove the element
```

### Comparisons

`<`, `>`, `<=`,`=>`,`==`,`!=`

`||`

### If statements

```php
<?php
  $age = 21;
  if( $age > 18 ) {
    echo "you can vote"." (but not Marine)";
  }
  elseif("condition" == true){
    echo "yes";
  }
  else {
    echo "should you ?";
  }
?>
```

### Switch statements

There's two ways to create a swhitch:
```php
switch ($i) {
  //case...
}
```

```php
switch ($i):
  //case...
endswitch;
```

Swhitchs works like in JS:
```php
$myNum = 2
  
switch ($myNum) {
  case 0:
    echo 'The value is 0';
    break;
  case 1:
    echo 'The value is 1';
    break;
  case 2:
    echo 'The value is 2';
    break;
  default:
    echo "The value isn't 0, 1 or 2";
}
```

And I can "fall through":
```php
case 1:
case 2:
case 3:
  echo "$i is 1, 2 or 3";
  break;
```

### Arrays

Create an array with `$myArray = array()`.
Access it with `[]` or `{}`.

```php
$array = array("Egg", 783, "Tomato", "Beans", 0);

echo $array[0]; // Egg
echo $array{0}; // Egg

$array[1] = "another value" // modify an array directly

$bar = "foo";
$array[1] = $bar // we can assign a variable (do we assign the variable reference or the variable value ?)

unset($array[1]) // remove the element
```


