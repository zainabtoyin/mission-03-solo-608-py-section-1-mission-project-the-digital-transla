# Tier 2: Field Exercise, Algorithm Thinking

## The problem

> "Withdraw money from an ATM."

This is a **problem**. It says what we want, but not how to get it. A computer cannot act on it until we turn it into an algorithm.

## The algorithm

**Overall goal:** Withdraw money

**Starting condition:** The ATM is switched on, idle, and showing the message "Please insert your card."

**Rule that applies at every step:** If the customer presses "Cancel", or does nothing for 30 seconds, stop the transaction, return the card, and go back to the idle screen.

### Part A: Card

**Step 1:** The customer inserts their card.

**Step 2:** The ATM reads the card (chip or magnetic stripe).
- *Why:* The ATM needs to know whose account this is.

**Step 3:** If the card cannot be read, show "Card cannot be read. Please try another card," return the card, and end.
- *Why:* A dirty, damaged, or upside-down card must not be allowed to continue.

**Step 4:** Verify the card. Check that it is a real card, has not expired, has not been reported lost or stolen, and is not blocked.
- *Why:* This stops stolen, expired, and fake cards.

**Step 5:** If the card fails verification, show "This card cannot be used." Return the card (or keep it, if the bank has marked it stolen), and end.

### Part B: PIN

**Step 6:** Set `pin_attempts = 0`.

**Step 7:** Ask the customer to enter their PIN. Show each digit as `*` on screen.
- *Why:* The PIN proves the person holding the card is the owner. Hiding the digits protects it from people looking over the shoulder.

**Step 8:** Check the PIN against the bank's records. Send it encrypted.

**Step 9:** If the PIN is correct, go to Step 12.

**Step 10:** If the PIN is incorrect, add 1 to `pin_attempts`.

**Step 11:** If `pin_attempts` is less than 3, show "Incorrect PIN. Try again," and go back to Step 7. If `pin_attempts` is 3, block the card, show "Card blocked. Contact your bank," keep the card, and end.
- *Why:* Limiting attempts stops a thief from guessing the PIN.

### Part C: Withdrawal request

**Step 12:** Show the menu. The customer selects "Withdrawal."

**Step 13:** Ask the customer to choose the account type (for example, Savings or Current).
- *Why:* One customer can have several accounts, and the ATM must know which one to use.

**Step 14:** Ask the customer to enter an amount.

**Step 15:** Check that the amount is valid. It must be above zero, a multiple of the smallest note the ATM holds, and not above the daily withdrawal limit.
- If it is not valid, show the reason and go back to Step 14. After 3 invalid tries, cancel the transaction.
- *Why:* This catches nonsense input such as 0, -500, or 1,234.

### Part D: Checks before giving cash

**Step 16:** Ask the bank for the available balance.

**Step 17:** If the amount is greater than the available balance, show "Insufficient funds." Offer two choices: enter a smaller amount (go back to Step 14) or cancel (go to Step 28).
- *Why:* The bank must never let a customer take money that is not in the account.

**Step 18:** Check that the ATM has enough cash, and the right notes, to pay out the exact amount.

**Step 19:** If the ATM does not have enough, show "This ATM cannot dispense that amount." Offer a smaller amount (go back to Step 14) or cancel (go to Step 28).
- *Why:* The customer's account must not be charged for money the machine cannot give.

### Part E: Completing the transaction

**Step 20:** Place a hold on the amount in the customer's account (reserve it, but do not finalise it yet).
- *Why:* This stops the same money from being spent twice while the ATM is still counting out the cash.

**Step 21:** Count out the notes and dispense the cash.

**Step 22:** Check that the cash was really dispensed (the ATM sensors confirm the notes went out).

**Step 23:** If the cash was not dispensed, or only part of it was, **release the hold** on the account, record the fault, show "Transaction could not be completed. You have not been charged," print a slip, and go to Step 28.
- *Why:* If the ATM fails halfway, the account must return to exactly how it was before.

**Step 24:** Update the account. Turn the hold into a final debit and calculate the new balance.

**Step 25:** If the account update fails after cash was given, record the transaction in the fault log for the bank to fix (reconciliation), and tell the customer to contact the bank.
- *Why:* The money has already left the machine, so the bank needs a record to correct the account.

**Step 26:** Ask "Do you want a receipt?" If yes, print one showing the date, amount, and new balance.

### Part F: Finish

**Step 27:** Show "Please take your cash."

**Step 28:** Return the card.

**Step 29:** If the card is not taken within 30 seconds, pull it back into the machine for safety and record this.

**Step 30:** If the cash is not taken within 30 seconds, pull it back into the machine, reverse the debit, and record this.

**Step 31:** Clear all customer information from the screen and memory. Go back to the idle screen.
- *Why:* The next customer must not see anything belonging to the last one.

## Think About Failure

| What goes wrong | What the algorithm does | Step |
|---|---|---|
| The card cannot be read | Show a message, return the card, end | 3 |
| The PIN is incorrect | Allow retry, up to 3 attempts. On the 3rd failure, block and keep the card | 10 to 11 |
| The amount is greater than the balance | Show "Insufficient funds." Offer a lower amount or cancel | 17 |
| The ATM does not have enough cash | Show a message. Offer a lower amount or cancel. The account is not charged | 19 |
| The transaction cannot be completed | Release the hold, restore the account, record the fault, tell the customer, return the card | 23 and 25 |

## Flow overview

```
Insert card -> Read card -> Verify card -> Enter PIN -> Check PIN
-> Select withdrawal -> Choose account -> Enter amount -> Check amount
-> Check balance -> Check ATM cash -> Hold funds -> Dispense cash
-> Confirm dispensed -> Update account -> Receipt -> Return card
```

Each arrow can instead lead to an error path (message, then return card, then end).

## Problem -> Algorithm -> Program

- **Problem:** The goal. "Withdraw money from an ATM." It says *what* we want.
- **Algorithm:** The solution procedure. The 31 ordered steps above, including decisions ("if the PIN is wrong...") and failure handling. It says *how* to solve the problem, in a way that is not tied to any programming language.
- **Program:** The algorithm written in a programming language such as Python, so a computer can run it. We have not done this part yet. The algorithm is the plan that the program will follow.

**In my own words:** An algorithm is the thinking done *before* the code. If the algorithm has a gap, such as no step for a wrong PIN, the program will have the same gap, and the machine will not know what to do.