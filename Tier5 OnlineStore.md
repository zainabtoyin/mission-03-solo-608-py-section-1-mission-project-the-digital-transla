# Tier 5: Architecture Challenge, Explain the Whole System

## Scenario

> A customer orders a product from an online store.

## Complete the chain

```
Customer
   |
Application / Program
   |
Instructions
   |
Data Processing
   |
Stored Data
   |
Result
```

## Explaining each stage in the scenario

### 1. Customer input
The customer chooses a product and gives the store information. For example, a customer orders a pair of shoes that costs 50,000 each. The customer provides:

The product: the pair of shoes (price: 50,000 each)
The quantity: how many they want to buy. In this example, the customer wants 2.
The delivery address: where the order should be sent
The payment details: how the customer will pay

All of this is data entering the system. The product price and quantity are used again in stage 4 to calculate the order total (50,000 x 2 = 100,000).

### 2. Application / Program
The online store's app or website receives that data. The **program** is the set of instructions that tells the computer what to do with it. The customer does not see the program; they only see the pages and buttons.

### 3. Instructions
The program runs its instructions in order:
- Identify the product the customer selected.
- Check that the product is in stock.
- Calculate the order total.
- Process the payment.
- Create the order record and update stock.

### 4. Data processing
The computer carries out the instructions on the data and produces new information.

```
Product price: 50,000
Quantity: 2
------------------------
Order total: 100,000
```

The new information (the total of 100,000) did not come from the customer. The program produced it.

### 5. Stored data
The system saves the order so it can remember it later. Stored data includes:
- Customer (name, contact, delivery address)
- Product ordered
- Quantity
- Order amount (100,000)
- Order status (for example, "confirmed" or "shipped")
- Payment status
- Updated stock count

Everything is saved as digital data (binary), using the right representation for text, numbers, and true/false values.

### 6. Result / Output
The system sends a message back to the customer:

> "Order confirmed. Total: 100,000."



## Final Challenge: answers in my own words

**What is the computer doing?**
The computer is the machine that does the work. It runs the program's instructions, calculates the total, saves the order, and sends the confirmation. It does not understand what an "order" is. It only follows instructions and handles data.

**What is the program doing?**
The program is the set of instructions that decides what happens and in what order. It tells the computer to check stock, calculate the total, save the order, and show a confirmation. It turns the customer's request into steps the computer can run.

**What data is involved?**
Input data: product, quantity, delivery details, payment details. Processed data: the order total. Stored data: customer, product, quantity, amount, status. Output data: the confirmation message.

**What instructions are being executed?**
Identify the product, check availability, calculate the total (price x quantity), process the payment, save the order record, update stock, and display the confirmation.

**What is the output?**
"Order confirmed. Total: 100,000."

**What information might need to be stored to remember the order?**
Customer, product, quantity, order amount, order status, delivery address, payment status, and the date and time. Without this, the store would forget the order as soon as the page closed.

**How the concepts connect:**
The customer's input becomes data. The program holds the instructions. The computer executes the instructions to process the data. The results are stored so the system remembers them, and an output is returned to the customer. Each stage feeds the next one.

## Capstone mental model

```
REAL-WORLD PROBLEM -> DATA -> PROGRAM -> INSTRUCTIONS
-> PROCESSING -> STORED DATA -> OUTPUT
```

A computer does not magically know how to solve a real-world problem. A person has to identify the problem, work out the data involved, design the instructions, write them as a program, let the computer process the data, store what must be remembered, and produce a useful result. That is the "digital translator" mindset: turning what a human wants into precise instructions and digital data.

## Final Reflection

> "A computer does not understand the real world directly. It works with representations of information and follows instructions for processing those representations."

**In my own words:** A computer has no idea what breakfast, money, a customer, or an order really is. It only has numbers, text, and true/false values stored as 0s and 1s, and it follows the exact steps it is given. The "understanding" has to be done by a person, who translates the real world into data and instructions first.

**Applying it to each example:**

- **Breakfast:** The computer does not know what "breakfast" means. Every detail (what food, where it is, how much, how to know it is done) had to be spelled out as explicit instructions.
- **ATM:** The computer does not know what "withdraw money" means. A person had to turn the goal into ordered steps with checks, such as verifying the PIN and checking the balance, and plan what happens when something fails.
- **Calculator:** The computer does not know that dividing by zero is impossible in a sensible way. The programmer has to design for it: input, process, output, and a safe response to bad input.
- **Customer data:** The computer does not know that "Victor" is a name or that 150000.50 is money. They are stored as representations (characters, numbers, a true/false value). If a representation is misread, the result is wrong.
- **Online store:** The computer does not know what an "order" is. The program turns the customer's input into data, runs instructions, stores the results, and produces a confirmation.

**Conclusion:** Computers are powerful because they follow instructions exactly, but that is also their limit. Good computing starts with a person who understands the real problem and translates it into clear data and instructions.