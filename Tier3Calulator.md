# Tier 3: Input -> Processing -> Output (The Simple Calculator)

## The model

```
INPUT  ->  PROCESSING  ->  OUTPUT
```

A program receives information (input), performs instructions on it (processing), and produces a result (output).

**Values used:**
- number_1 = 20
- number_2 = 5

## Calculator design

### 1. Addition

| Part | Answer |
|---|---|
| Input | 20 and 5 |
| Processing | Add the two numbers: 20 + 5 |
| Output | 25 |

### 2. Subtraction

| Part | Answer |
|---|---|
| Input | 20 and 5 |
| Processing | Subtract the second number from the first: 20 - 5 |
| Output | 15 |

### 3. Multiplication

| Part | Answer |
|---|---|
| Input | 20 and 5 |
| Processing | Multiply the two numbers: 20 x 5 |
| Output | 100 |

### 4. Division

| Part | Answer |
|---|---|
| Input | 20 and 5 |
| Processing | Divide the first number by the second: 20 / 5 |
| Output | 4 |

### Overall logic of the calculator

**Step 1:** Receive number_1.

**Step 2:** Receive number_2.

**Step 3:** Receive the operation the user wants (add, subtract, multiply, or divide).

**Step 4:** Check that both inputs are valid numbers. If not, show a message and ask again.

**Step 5:** Perform the chosen operation on the two numbers.

**Step 6:** Show the result to the user.


## Reasoning Challenge: what if number_2 = 0?

**Input:** number_1 = 20, number_2 = 0

**Processing attempted:** 20 / 0

**What happens:** Division by zero is **impossible**. There is no number that you can multiply by 0 to get 20, so the answer is undefined. If the program tries it anyway, it will usually crash or give an error, and the user gets no useful result.

**What a well-designed program should do when an input makes the operation impossible:**

1. **Check before processing.** Before dividing, test whether number_2 is 0.
2. **Do not perform the division** if it is 0.
3. **Show a clear message** in plain language, for example: "Error: You cannot divide by zero. Please enter a different second number."
4. **Let the user try again** instead of crashing or showing a wrong answer.
5. **Keep working for the other operations.** 20 + 0 = 20, 20 - 0 = 20, and 20 x 0 = 0 are all fine, so only division needs this check.

**Improved logic for division:**

```
IF number_2 is 0:
    show "Cannot divide by zero" and ask for a new number
ELSE:
    output number_1 / number_2
```

**Lesson:** A good program does not only handle the normal case (20 / 5). It also plans for inputs that make the operation impossible, and handles them safely.