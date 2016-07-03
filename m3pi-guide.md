# Line Following robots challenge

On this table there should be a robot, this is the "m3pi" with a small computer slotted on top.

## How to program the robot

### Loading up the compiler
A compiler is a way of converting code (something a human can read) into something the computer can read.

The model of board you're using now has an online compiler (these are really rare!)

https://developer.mbed.org/compiler

### Login details

You can sign in with:

username: (the name of your robot)

password: correct-horse-battery-staple

### Loading the project

There should be a project named `sr-m3pi-(your robot name)`, which should contain a few files. You should start working in `main.cpp`. The other files are libraries to manage interfacing with the robot base.

### Putting code on the robot

To put code on the robot, simply click 'compile' in the compiler. After a few seconds it should ask where to save the compiled file. Simply plug the mbed into your laptop and it should show up as a USB stick, choose to save into the USB stick. 

### Running the robot

Unplug the robot, all the lights should turn off. To run the program just turn on the robot! press the button on the top next to the screen, and it should start running the code. (You can also press the small circular button on the mbed to restart the program)

## Programming

This section will give you a fast tour of the basics of programming in C++, you should skim this for differences between it and languages you are familiar with.

### Comments 
Comments are not executed by the code, they are just for you to understand what is going on.

There are two types of comments, single- and multi-line. 

    // this is a single line comment

    /* this is a 
     * multi-line comment
     */

### Functions

Functions are pieces of code you can define and call repeatedly. They can take 0 or more
parameters. Your program must contain a `main` function in order to run. A basic program
might look like the following:

    #include "mbed.h" // include the library for access to the mbed methods
    #include "m3pi.h" // include the library for access to the robot base

    m3pi m3pi; // initialise the m3pi class

    int main() { // define the main method
        
        // Your code goes here...
    }

The general syntax for defining a function is as follows. This program returns a number cubed.

    int cube(int n) {
        return n * n * n;
    }


## How To Guide: Moving

The following line can be used to set the robot moving forward.

    m3pi.forward(speed);

Replace `speed` with a number between 0.0 and 1.0. Motors will not change until you tell them to! To stop, you should use `m3pi.forward(0)`.

### Set individual motor speeds

    m3pi.left_motor(speed);

and

    m3pi.right_motor(speed);

can be used to set the speeds of the two motors separately. By settings the speeds to be different, the robot will move in different directions; for example, if the left motor is set to be faster than the right motor, the robot will turn towards the right.

### Rotate left or right on the spot

Use one of these two lines to rotate on the spot either left or right:

    m3pi.left(speed);
    m3pi.right(speed);

Replace `speed` with a number between 0.0 and 1.0.

## How to: read from the light sensors

At the start of your program, add:

    m3pi.sensor_auto_calibrate();

This will calibrate the light sensor, to allow it to work as effectively as possible for
the rest of the program.

    float position_of_line = m3pi.line_position();

`position_of_line` will now contain a decimal (float) value in the range -1.0 to 1.0 inclusive. It could be any value between -1 and 1! -1.0 means the line is on the left or cannot be found, 1.0 means the line is on the right.


## How to: use `if` statements

`if` statements allow you to have conditions about when code runs. The syntax is as follows:

    if (boolean_condition) {
        // code if condition is true
    } else {
        // code if condition is false
    }

## How to: use loops

There are two types of loops, while loops and for loops. Both are types are shown below,
and both print the numbers 0 to 9.

    int i = 0;
    while (i < 10) { 
        m3pi.printf("%d", i); // print i
        i++; // increment i by 1
    } 


    for (int j = 0; j < 10; j++) {
        m3pi.printf("%d", j); // print j
    }

## How to: use the LCD screen

The LCD screen is a 2x8 display. You must first move the cursor to a point on the screen, 
and then print to it.

    m3pi.locate(0, 1); // move the cursor to the start of the second line (the arguments are (x, y))
    m3pi.printf("bees"); // print "bees" on the display