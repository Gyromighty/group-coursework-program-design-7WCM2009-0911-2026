<!-- Documentation for the command "fibonacci": Ashutosh -->
<!-- Please fill in a function description (inputs, outputs, logic) and input validation -->

# Description
The Fibonacci sequence is a series of numbers that begin with 0 and 1, and each subsequent number is the sum of the 2 numbers before it.

It is defined as follows:

$$
F_n = F_{n-1} + F_{n-2}
$$
given
$$
F_0 = 0\\
F_1 = 1
$$

There is also a shortcut that makes it computationally quicker to find a Fibonacci sum up to the index `n`:
$$
\sum_{i=0}^n F_i = F_{n+2} - 1
$$

# Function Logic

The function to compute the Fibonacci term up to the index `n` could work as follows:

- Validate that `n` is a valid input (next section).
- Compute the `(n+2)th` term of the Fibonacci sequence.
- Subtract 1 from it and return the answer.

# Input Validation

The following validations must be performed on the input variable `n`:

- `n` must be a valid number. `readln()` always accepts a string that needs to be correctly converted to a number.
- `n` must be a natural number within the range:
$$
n \in \{1, 2, ...\ \infty\}
$$
- `n` must not be too large to cause either integer overflow on the sum variable, or take a very long time to compute. A suitable limit must be decided. For now the number 100 has been selected.

# Function
The function could be implemented as follows:
```kotlin
import java.math.BigInteger

val MAX_N: Int = 100

/**
 * @param userInput The input string from the user containing the number n
 * @return The Fibonacci sum until the number n
 * @throws IllegalArgumentException When input validation fails
 */
fun computeFibonacciSum(userInput: String) : String {
    // Convert to integer
    val n: Int? = userInput.toIntOrNull()

    // Validate inputs
    when {
        n === null -> throw IllegalArgumentException("The input $userInput is not a valid integer.")
        n < 1 -> throw IllegalArgumentException("The input $userInput is less than 1.")
        n > MAX_N -> throw IllegalArgumentException("The input $userInput is greater than $MAX_N.")
    }

    // We compute up to index n + 2
    val targetIndex = n + 2

    // Use previous and current number to track the series
    var previous = 0.toBigInteger()
    var current = 1.toBigInteger()

    // Compute the (n+2)th Fibonacci number iteratively
    for (i in 2..targetIndex) {
        val next = previous + current
        previous = current
        current = next
    }

    // Return F(n+2) - 1
    return (current - 1.toBigInteger()).toString()
}
```

The input and outputs are both string to work easily with `readln()` and `println()`. 
Integer overflow checks could be added later. For now it has been verified to work until `MAX_N`, but this could be made dynamic.
