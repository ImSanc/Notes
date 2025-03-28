## Local variables 
- A local variable is called local because it is available for use by the code block in which it was declared.
- It is also available to code blocks that are contained by a declaring block.


    {
        //starts on outer block - for example a method block
        int firstVariable = 5;
        int secondVariable = 10 ;
    
        if(firstVarable > 0) { //flow statement block starts inner block
        
            //Inner block code has access to outer block's variables
            System.out.println(secondVariable);
        }
    }


## Scope
- Scope describes the accessibility of a variable.
- "In scope" means the variable can be used by an executing block or nested blocks
- "Out of scope" means the variable is no longer available and cannot be used.


## When are Local variables in Scope?
- Local variables are always out of scope for the outer blocks or the containing blocks they are declared in.

        public static void aMethod(boolean aBoolean) {
            if( aBoolean ) {
                int myCounter = 10; //myCounter is local to this if block 
            }
        
            System.out.println(myCounter); // myCounter is out of Scope here
        }


## Scope Best practice
- It is considered best practice:
- To declare and initialize variables in the same place , if possible.
- And to declare variables in the narrowest scope possible.

## Declaring variables in a switch statement block
- However, the switch statement is different from the if-then-else statement blocks


    public static void maine( String[] args){

    int value = 1;
    switch (value ) {
        
        case 1: 
            int i = 10;
            break;
        default: 
            i = value;      //This is ok
            System.out.println(i);      //This is ok
            break;
    }
    System.out.println(i);  // ERROR:  i is out of scope outside of the switch
    }

- Another example 
    
        public static void aMethod(int value){
            
            switch(value) {
                case 1 :    
                   System.out.println(i); //this is not Okay , i is declared below 
                   break;
                case 2 :
                    int i = 10 ;
                    System.out.println(i);  // this is ok
                    break;
            
                default:
                    i = value;  //This is ok
                    System.out.println(i); // This is ok
                    break;
            }
            System.out.println(i); // ERROR: i is out of scope outside the switch
        }

#### Note: In addition to local variables, we can set up data to be defined and used as part of a class or an object.

1. Instance Variables (Object-level)
- These are declared inside the class but outside any method. Each object (or instance) of the class gets its own copy.

      public class Person {
         String name; // instance variable
    
         public void sayName() {
            System.out.println("My name is " + name);
         }
      }

2. Static Variables (Class-level)
 - These are declared with the static keyword. They belong to the class, not any one object, so all objects share the same variable.

        public class Car {
        static int numberOfWheels = 4; // class variable
        }