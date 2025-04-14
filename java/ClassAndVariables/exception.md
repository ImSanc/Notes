## Exception
- An exception is an error that happens in code.
- Some types of errors can be predicted and named.


### Catching an exception
- An exception is caught first by creating a code block around the code that gets the error.
- This is done by try statement code block.


### try statement
- The try statement actually has two code blocks 
- The first is declared directly after the try keyword, and this code block ends, and is followed by the declaration of the catch keyword
- The catch keyword includes the declaration of variables, in parentheses , and then has its own code block.

        try{
            //statement that might get errors
        } catch (Exception e){
            //code to 'handle' the exception
        }