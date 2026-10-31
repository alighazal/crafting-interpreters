# Lox Interpreter

A Java implementation of the tree-walking interpreter from [Crafting Interpreters](https://craftinginterpreters.com/) (jlox).

Supports variables, control flow, functions, closures, classes, `this`, constructors (`init`) and inheritance (`super`).

## Build

```sh
cd lox
mvn compile
```

## Run

```sh
# run a script
java -cp target/classes com.craftinginterpreters.lox.Lox tests/inheritance_super.lox

# interactive REPL
java -cp target/classes com.craftinginterpreters.lox.Lox
```

## Examples

Classes and `this` (`tests/this_and_fields.lox`):

```
class Cake {
  taste() {
    var adjective = "delicious";
    print "The " + this.flavor + " cake is " + adjective + "!";
  }
}

var cake = Cake();
cake.flavor = "German chocolate";
cake.taste(); // The German chocolate cake is delicious!
```

Inheritance (`tests/inheritance_super.lox`):

```
class A {
  method() { print "A method"; }
}

class B < A {
  method() { print "B method"; }
  test() { super.method(); }
}

class C < B {}

C().test(); // A method
```
