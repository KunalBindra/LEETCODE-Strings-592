# LEETCODE-Strings-592
Let's go through the provided Java code for the `Solution` class step by step to understand how it works for the `fractionAddition` function.

### Code Explanation

1. **Initialization**:
   - The initial value of `A` is set to 0, and `B` is set to 1. This represents the fraction 0/1.
   - The `expression` string, which represents a series of fractions to be added (e.g., "1/3-1/2+1/6"), is read using a `Scanner`. The delimiter for the scanner is set to `/` or the position just before a `+` or `-` sign. This allows splitting the expression into individual numbers for the fractions.

2. **Fraction Addition Logic**:
   - The loop processes each fraction in the input expression one at a time. For each fraction, the numerator (`a`) and the denominator (`b`) are extracted.
   - The new numerator `A` and denominator `B` after adding each fraction to the result are calculated using the formula:
     \[
     A = A \times b + a \times B, \quad B = B \times b
     \]
   - This formula comes from the standard method of adding fractions:
     \[
     \frac{A}{B} + \frac{a}{b} = \frac{A \cdot b + a \cdot B}{B \cdot b}
     \]
   - After calculating the new numerator and denominator, the greatest common divisor (GCD) is calculated using the `gcd` method to simplify the fraction.

3. **GCD Calculation**:
   - The `gcd` method computes the greatest common divisor of two integers using a recursive approach based on the Euclidean algorithm.

4. **Return Result**:
   - Finally, the simplified result in the form "A/B" is returned as a string.

### Dry Run Example

Let's dry run this code with an example input.

#### Example Input
```
expression = "1/3-1/2+1/6"
```

#### Dry Run Steps

- **Initial Values**:
  - `A = 0`, `B = 1`

- **First Iteration (Processing "1/3")**:
  - `a = 1`, `b = 3`
  - `A = A * b + a * B = 0 * 3 + 1 * 1 = 1`
  - `B = B * b = 1 * 3 = 3`
  - GCD of `1` and `3` is `1`.
  - Simplified fraction: `1/3`

- **Second Iteration (Processing "-1/2")**:
  - `a = -1`, `b = 2`
  - `A = A * b + a * B = 1 * 2 + (-1) * 3 = 2 - 3 = -1`
  - `B = B * b = 3 * 2 = 6`
  - GCD of `-1` and `6` is `1`.
  - Simplified fraction: `-1/6`

- **Third Iteration (Processing "+1/6")**:
  - `a = 1`, `b = 6`
  - `A = A * b + a * B = (-1) * 6 + 1 * 6 = -6 + 6 = 0`
  - `B = B * b = 6 * 6 = 36`
  - GCD of `0` and `36` is `36`.
  - Simplified fraction: `0/1`

- **Final Result**:
  - The result is "0/1".

### Conclusion

The function `fractionAddition` works as expected to add a series of fractions given in the form of a string, handling both positive and negative fractions and simplifying the result to its lowest terms.
