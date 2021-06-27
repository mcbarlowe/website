---
title: "Hello World"
date: 2019-04-17T23:22:23-04:00
draft: false
---

Ok Java is a little different than R or Python in that in order to run any code you
have to first create a `class` object. I haven't yet written a tutorial on classes
and inheritence which form the basis of Object Oriented Programming.

If you're trying to learn Java coming from Python or R this fact will be very disorienting
as you can't can't just type some lines and run them at the command line. In Java you have
to create a `class` first and then create a `main` method which will run the lines of code
you want after you compile the code.

Each class must be stored in its on file as well. This means that everytime you want to
create a new class you have to create a new file **that has the same file name as the
class name**. The file name also has to end in `.java` just like all Python scripts
have to end in `.py`. It's a lot to take in that I will explain further in my tutorial on
installing Java, but as of right now let's just write a simple `Hello World` program.

```Java
// Java uses camelCase for its naming conventions. Awful I know.
// unlike Python, Java doesn't care about whitespace so you can
// structure your code however you want as each line ends with a
// semicolon.
public class helloWorld {

    // the main method will always look like this
    public static void main(String[] args) {
        //Look at all that just to print. Also don't forget your semicolon!
        System.out.println("Hello World");
    }
}
```

Now your program is ready to compile so save it as `helloWorld.java` and then type
at the command line `java helloWorld.java` and the output will be `Hello World`.
