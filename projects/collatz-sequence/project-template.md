"""
THE COLLATZ SEQUENCE

Description:

Write a function named collatz() that has one parameter named number. If
number is even, then collatz() should print number // 2 and return this value.
If number is odd, then collatz() should print and return 3 * number + 1.

Then write a program that lets the user type in an integer and that keeps
calling collatz() on that number until the function returns the value 1.
(Amazingly enough, this sequence actually works for any integer—sooner
or later, using this sequence, you'll arrive at 1! Even mathematicians aren't
sure why. Your program is exploring what's called the Collatz sequence, some-
times called "the simplest impossible math problem.")

Remember to convert the return value from input() to an integer with
the int() function; otherwise, it will be a string value.

Hint: An integer number is even if number % 2 == 0, and it's odd if
number % 2 == 1.

Output:

The output of this program could look something like this:
Enter number:
3
10
5
16
8
4
2
1

Input Validation:

Add try and except statements to the previous project to detect whether the
user types in a noninteger string. Normally, the int() function will raise a
ValueError error if it is passed a noninteger string, as in int('puppy'). In the
except clause, print a message to the user saying they must enter an integer.

Tips:

* Test with small numbers like 3, 5, or 7 to verify your logic works correctly
* The modulo operator (%) is essential for checking if a number is even or odd
* Your function must both print AND return the calculated value in each case
* Input validation prevents crashes when users enter non-numeric text
* The sequence always eventually reaches 1, no matter what positive integer you start with

Source:

Sweigart, Al. Automate the Boring Stuff with Python: Practical Programming for Total Beginners. 2nd ed., No Starch Press, 2019.
"""



# 0. SETUP

# TODO: Define the collatz() function with one parameter called number


# TODO: Create the function signature: def collatz(number):



# 1. CORE LOGIC

# TODO: Check if number is even using the condition number % 2 == 0


# TODO: If even, calculate the result using number // 2


# TODO: Print the result of the even calculation


# TODO: Return the result of the even calculation


# TODO: Handle the else case for when number is odd


# TODO: If odd, calculate the result using 3 * number + 1


# TODO: Print the result of the odd calculation


# TODO: Return the result of the odd calculation



# 2. INPUT HANDLING

# TODO: Display the prompt "Enter number:" to the user


# TODO: Use input() to get user input and store it in a variable


# TODO: Convert the input string to an integer using int()


# TODO: Store the converted integer in a variable called number



# 3. LOOPING

# TODO: Create a while loop that continues as long as number != 1


# TODO: Inside the loop, call collatz(number) and store the return value


# TODO: Update the number variable with the returned value


# TODO: The loop will automatically stop when number becomes 1



# 4. INPUT VALIDATION

# TODO: Wrap the input() and int() conversion in a try block


# TODO: Add an except ValueError clause after the try block


# TODO: In the except block, print the message "You must enter an integer"


# TODO: Optionally, use a while loop to keep asking until valid input is received



# 5. TESTING

# TODO: Test with the example input of 3


# TODO: Verify the output sequence: 3 → 10 → 5 → 16 → 8 → 4 → 2 → 1


# TODO: Test with an even starting number like 10


# TODO: Test with invalid input such as "puppy" to check error handling


# TODO: Test with edge case input of 1 (should terminate immediately)


# TODO: Test with a larger number like 27 to verify longer sequences work



# 6. OPTIONAL ENHANCEMENTS

# TODO: Add a step counter variable initialized to 0 before the loop


# TODO: Increment the counter by 1 each time collatz() is called


# TODO: After the loop ends, print "Reached 1 in X steps"


# TODO: Allow the user to test multiple numbers without restarting the program


# TODO: Add a maximum iteration limit (e.g., 1000) to prevent infinite loops for edge cases

