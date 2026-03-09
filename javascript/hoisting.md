# Hoisting

- Hoisting is JavaScript’s compile-time behavior where declarations are registered before execution, but values are not “loaded” upfront.

#### JavaScript runs in two phases for every scope (global or function):

1️⃣ Creation phase (before any line runs)

JS scans the code

Registers identifiers (names) in memory

2️⃣ Execution phase

Runs code top to bottom

Assigns values when it reaches assignments.
This pre-scan + registration is what we call hoisting.

## Let and const Hoisting

- Declaration is hoisted
- NOT initialized
- Lives in the Temporal Dead Zone (TDZ)


## Functions (important distinction)
- Function declarations → fully hoisted
- They are hoisted with their body.

        sayHi(); // ✅ works
        
        function sayHi() {
        console.log("Hi");
        }

## Function expressions 
- → behave like variables
 - sayHi is hoisted as undefined, not the function.

            sayHi(); // ❌ TypeError
            var sayHi = function () {
            console.log("Hi");
            };