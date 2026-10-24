<!-- Documentation for the command "gcd": Geoffrey -->
<!-- Please fill in a function description (inputs, outputs, logic) and input validation -->

#Description
The Greatest Common Divisor (GCD) is the largest positive integer that divides two numbers without a remainder. In instances where 0 is both of the numbers the result is undefined. If one number is zero then the GCD is the other number.

#Function Logic

The function starts by checking for zeros and exiting early if one or more are present.
If not, a remainder variable is used to store the result of number one modulus number two.
If this remainder is 0 then the function returns the current value of number 1, if not number one is replaced by number two, and number two is replaced by remainder value. The process then repeats until the remainder is zero.

As defined in the requirements, only positive integers are valid inputs.

# Function
```kotlin

fun gcd(num1: Int, num2: Int): String {
    // handle 0 and negative input edge cases
    if (num1 == 0 && num2 == 0) {
        println("Greatest Common Divisor for 0 is undefined.")
        return "Undefined"
    }
    else if (num1 < 0 || num2 < 0) {
        return "Negative numbers are not valid inputs."
    }
    else if (num1 == 0 || num2 == 0) {
        if (num1 == 0) {
            return num2.toString()
        }
        else {
            return num1.toString()
        }
    }
    else {
        var a = num1
        var b = num2

        // gcd logic - replace larger number with smaller number and smaller number with modulus until modulus equals zero
        while (b != 0) {
            val remainder = a % b
            a = b
            b = remainder
        }

        return a.toString()
    }
}
```
