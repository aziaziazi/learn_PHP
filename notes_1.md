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

This looks working like JS. However PHP run on the server, not the browser. This means I can access infos on the DB, run server side calculs and tasks and custom build HTML before sending it.

## Basic syntax
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
    echo "you can vote"." (but don't for Marine)";
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

There's two syntax to create a swhitch:
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

### Loops

#### For

```php
for ($i = 0; $i < 10; $i++) {
  echo $i;
}
```

##### ForEach

```php
$langs = array("JavaScript", "HTML/CSS", "PHP", "Python", "Ruby");

foreach ($langs as $lang) {
  echo "<li>$lang</li>";
}

unset($lang);
```

#### While

As for the switch, there's two syntax for the while loop:

```php
$loopCond = true;

while ($loopCond){
  echo "<p>The loop is running.</p>";
  $loopCond = false;
}
```

```php
$loopCond = true;

while($loopCond):
  echo "<p>The loop is running.</p>";
  $loopCond = false;
endwhile;
```

#### Do / While

`while` check the condition *before* executing the code.
`do`+ `while` check the condition *after* executing the code:

```php
// Useless exemple where $i is printed once.

$loopCond = false;
do {
  echo "<p>The loop ran even though the loop condition is false.</p>";
} while ($loopCond);
echo "<p>Now the loop is done running.</p>";
```

```php
// We will keep flipping a coin as long as the result is heads!
  
$flipCount = 0;
do {
  $flip = rand(0,1);
  $flipCount ++;
  if ($flip){
    echo "<div class=\"coin\">H</div>";
  }
  else {
    echo "<div class=\"coin\">T</div>";
  }
} while ($flip);
$verb = "were";
$last = "flips";
if ($flipCount == 1) {
  $verb = "was";
  $last = "flip";
}
echo "<p>There {$verb} {$flipCount} {$last}!</p>";
```

```php
// Print my favorite beers.

echo "<p>My favorite beers are ";

$favBeers = array("Brussels Calling", "Saison 1858", "Queue de Charrue Brune");
$count = 0;

do {
  $count ++;
  $separation = ', ';
  if ($count+1 == count($favBeers)){
    $separation = ' and ';
  }else if ($count == count($favBeers)){
    $separation = '';
  };

echo $favBeers[$count-1].$separation;
} while ($count < count($favBeers));

echo ". You should try them!";
```

## Functions
### Build-in functions
#### String functions

```php
// returns the lenght of a string.
strlen('camille'); // 7

// returns a piece of the string:
// substr( stringToEvaluate, characterToStartAt, howManyCharacterIWant)
substr("Camille", 0, 3); // Cam

strtolower("Camille"); // camille

strtolower("Camille"); // CAMILLE

// returns the position of a given character. The first parameter is called haystack and the second needle.
strpos('Camille', 'i'); // 3

// returns false if nothing is found
strpos('Camille', 'x'); // false
```

#### Math functions
##### round

```php
// M_PI is a php constant equal to pi.

// returns pi rounded withoud decimals.
round(M_PI);

// returns pi rounded with 3 decimals.
round(M_PI, 3);
```

##### rand

```php
// returns an integer between 0 and getrandmax().
rand();

// returns an integer between 1 and 10.
rand(1,10);
```

#### Array functions

```php
$fav_bands = array();
array_push($fav_bands, "Aphex Twin");
array_push($fav_bands, "Sebastien Tellier");
array_push($fav_bands, "Trentemoller");
array_push($fav_bands, "Tom Waits");
array_push($fav_bands, "Bad Bad Not Good");

count($fav_bands); // returns 5
```

```php
$theArray = array(2, 8, 9, 1, 0);

sort($theArray); // sort the array by alphanumeric number.
rsort($theArray); // reverse-sort the array.
```

```php
// join the array :
// join(glue, array);
join(" and ", $theArray);
```

### Create functions

```php
// define
function aboutMe($name, $age){
    return  "Hello World! ".$name.", you are ".$age." years old right ?";
}
// call
echo aboutMe("Camille", 28);
```

## OOP
### Class
Create a class with `class Myclass`.
Create a property of this class with `public $property`.
Create a method of this class with `public function method`.

Create a new instance with `$instance = new Myclass()`.
Access a property of an instance with `$instance->Property`

```php
class Classname { // create the class
  public $property = "value"; // create a property
  public function myMethod(){ // create a method
    return "the result";
  };
};

$obj1 = new Classname(); // create an instance
echo $obj1->property // access a property. Here, returns "value"
```

### Constructor
To assign values to instances properties, we use the **constructor**.

Use the keyword `__construct` to create the constructor method. Add it some arguments in the parentesis.
Assign the properties like this : `$this->prop1 = $prop1`.

```php
class Classname {
  public function __construct($prop1, $prop2){
    $this->prop1 = $prop1;
    $this->prop2 = $prop2;
  }
}
```

### Build-in methods

Build-in functions that tells informations of a class/object:

- `is_a()` Find out if an object is an instance of a class
- `property_exists()` Find out if an object has a given property
- `method_exists()` Find out if an object has a given method

All three takes two arguments: the **object we're checking** and **class**, **property** name or **method** name as a string
 
```php
class Cat {
  public function __construct($name){
    $this->name = $name;
  }
  public function meow(){
    return "Meow meow";
  }
  public $isAlive = true;
  public $numLegs = 4;
};

$cat1 = new Cat("CodeCat");

echo $cat1->meow()

echo is_a($cat1, "Cat") // True
echo property_exists($cat1, "name") // True
echo method_exists($cat1, "meow") // True
```

### Inheritance

Classes can inherits form other classes with the `extends` keyword.
Parents are called **superclass**.
Childs are called **subclass**.

To override properties and methods, just redefine them in the subclass.

```php
class Shape {
  public $isGeometric = true;
  public $sides = true;
}

class Square extends Shape { // Extends Square from Shape
  public $sides = 4 // redefine sides
}

$mySquare = new Square;
$mySquare->isGeometric // true
```

 If I want to prevent a property/method to be overrided, I can use the `final` keyword just before `public`:

 ```php
 final public $myPropery = "can't be overrided!" // Will product an error if I try to redefine in another class
 ```

### Class Constant
PHP let me set **constants** on a class-by-class basis and each one has his own **scope** (context in which it can be used). Constants **do not** start with `$` but takes `const` as a prefix.
I access a class constant with the scope resolution operator `::`.

```php
class Immortal {
  const alive = true;
}

echo Immortal::alive; // true
```

### Static
The keyword `static` and the scope resolution operator `::` allow me to declare and access class properties and methods without creating instances.

```php
class Person {
  public static $isAlive = true;
}

echo Person::$isAlive; // true
```


*to continue...*
