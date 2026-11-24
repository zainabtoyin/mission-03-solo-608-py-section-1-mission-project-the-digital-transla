# Tier 4: Data Translator

## The customer information

- Customer name: Victor
- Age: 30
- Account balance: 150000.50
- Account active: Yes

## Identify the data

| Information | What kind of information is it? | Why it needs its own representation |
|---|---|---|
| Victor | Text (a name, made of characters) | It is a label, not a quantity. You cannot do arithmetic on a name. |
| 30 | Whole number | It is a quantity that can be compared and calculated with (for example, "is the customer over 18?"). |
| 150000.50 | Decimal number | It is a quantity with a fractional part (the .50). Money needs exact handling. |
| Yes | True/false state | It answers a yes/no question. It only has two possible states: active or inactive. |

**Why the computer must tell these apart:** "Victor" and 30 are different kinds of information. If the computer mixed them up, it could try to add a name to a number, or treat the amount 150000.50 as plain text that cannot be calculated with. Each piece of data needs the right representation so the computer knows how to treat it.

## Going one level deeper: how is it represented digitally?

```
Real-world information
        |
Data representation
        |
Numerical / digital representation
        |
Binary data (0s and 1s)
        |
Stored by the computer
```

### Text: "Victor"
Each letter is given a number by a character code (for example, ASCII or Unicode). That number is then stored in binary.

| Character | Code number | Binary |
|---|---|---|
| V | 86 | 01010110 |
| i | 105 | 01101001 |
| c | 99 | 01100011 |
| t | 116 | 01110100 |
| o | 111 | 01101111 |
| r | 114 | 01110010 |

### Whole number: 30
Stored directly as a binary number: 30 = 00011110.

### Decimal number: 150000.50
Stored using a number format that can hold a decimal point (floating-point, or a fixed-decimal format for money). It is also converted into 0s and 1s, but in a format that records both the digits and where the decimal point goes.

### True/false: Yes
Stored as a single binary value: 1 means true (active) and 0 means false (inactive).

**Key idea:** Not every piece of information is stored in the same format. But everything is eventually stored as binary, and the computer must know *which representation* each set of bits uses.

## Reasoning Challenge: what if the balance is stored incorrectly?

**Situation:** Instead of 150000.50, the system interprets the stored data as a completely different value.

**What could happen to the customer's account:**

- **The balance is too high.** If 150000.50 is read as 15000050 (the decimal point is lost), Victor appears to have about 15 million. He could withdraw or spend money that does not exist, and the bank loses money.
- **The balance is too low.** If it is read as 1500.50, Victor sees much less than he really has. His payments are declined, he cannot withdraw his own money, and he loses trust in the bank.
- **The balance is unreadable.** If a number is read as text, calculations fail, so the bank cannot add deposits or subtract withdrawals correctly.
- **Errors spread.** Wrong balances lead to wrong interest, wrong statements, wrong reports, and possible legal problems.

**Lesson:** The computer cannot "see" that a number looks wrong. It only follows the representation it was given. If the stored data is interpreted incorrectly, every calculation that uses it will be wrong. That is why data representation matters.

## Objective

**Data is information represented in a form that a computer can store, process, and communicate.**