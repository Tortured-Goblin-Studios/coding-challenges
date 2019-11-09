i# Problem 1 - Change

## TL;DR

Implement a program that calculates the minimum number of coins required to give a user change.

## Background

When providing change, odds are you want to minimize the number of coins you’re dispensing for each customer. Fortunately, computer science has given cashiers everywhere ways to minimize numbers of coins due: greedy algorithms.

According to the National Institute of Standards and Technology (NIST), a greedy algorithm is one "that always takes the best immediate, or local, solution while finding an answer. Greedy algorithms find the overall, or globally, optimal solution for some optimization problems, but may find less-than-optimal solutions for some instances of other problems."

What’s all that mean? Well, suppose that a cashier owes a customer some change and on that cashier’s belt are levers that dispense toonies, loonies, quarters, dimes, and nickels. Solving this "problem" requires one or more presses of one or more levers. Think of a "greedy" cashier as one who wants to take, with each press, the biggest bite out of this problem as possible. For instance, if some customer is owed $3.41, the biggest first (i.e., best immediate, or local) bite that can be taken is $2. (That bite is "best" inasmuch as it gets us closer to 0¢ faster than any other coin would.) Note that a bite of this size would whittle what was a $3.41 problem down to a $1.41 problem, since 3.41 - 2 = 1.41. That is, the remainder is a similar but smaller problem. Needless to say, another $2 bite would be too big (assuming the cashier prefers not to lose money), and so our greedy cashier would move on to a bite of size $1, leaving him or her with a 41¢ problem. At that point, greed calls for one 25¢ bite followed by one 10¢ bite followed by one 5¢ bite, at which point we are left with 1¢ remaining. But what should we do about that remaining 1¢? Remember, that since Canada eliminated the penny, we now round up/down to the nearest nickel. Since we only have 1¢ remaining, we round down to 0, and are done. The customer receives one toonie, one loonie, one quarter, one dime, and one nickel: five coins in total.

It turns out that this greedy approach (i.e., algorithm) is not only locally optimal but also globally for Canada’s currency (and also America’s and the European Union’s). That is, so long as a cashier has enough of each coin, this largest-to-smallest approach will yield the fewest coins possible. How few? Well, you tell us!

## Specifications

Write, in a file called `change.rb` in your Assignment 1 repository, a program that first asks the user how much change is owed and then spits out the minimum number of coins with which said change can be made.

Use the `gets.to_f` method to get the user’s input and `puts` method to output your answer. Assume that the only coins available are toonies ($2), loonies ($1), quarters (25¢), dimes (10¢), and nickels (5¢).

We ask that you use `gets.to_f` so that you can handle dollars and cents, albeit sans dollar sign. In other words, if some customer is owed $9.75 (as in the case where a newspaper costs 25¢ but the customer pays with a $10 bill), assume that your program’s input will be 9.75 and not $9.75 or 975. However, if some customer is owed $9 exactly, assume that your program’s input will be 9.00 or just 9 but, again, not $9 or 900. Of course, by nature of floating-point values, your program will likely work with inputs like 9.0 and 9.000 as well; you need not worry about checking whether the user’s input is "formatted" like money should be.

You need not try to check whether a user’s input is too large to fit in a float. Using `gets.to_f` alone will ensure that the user’s input is indeed a floating-point (or integral) value but not that it is non-negative.

If the user fails to provide a non-negative value, your program should re-prompt the user for a valid amount again and again until the user complies.

## Requirements

* Prompt a person to enter an amount of change.

  * If the person enters an invalid value (i.e. not a number or a negative number), re-prompt for a value.

  > Hint: Convert the value from dollars to cents.

* Calculate the number of coins needed.

  * Always use the largest coin possible.

  * Keep track of coins used.

* Print the final number of coins used.

* Also output the number of each coin to dispense.

    * Make sure you adjust your pluralization and punctuation.

### Sample IO

<table>
  <tr>
    <td>Input</td>
    <td>Output</td>
    <td>Console Log</td>
  </tr>
  <tr>
    <td>3.41</td>
    <td>You need to dispense 1 toonie, 1 loonie, 1 quarter, 1 dime, and 1 nickel.
Total coins: 5</td>
    <td>
    
```
How much change is owed? 3.41
You need to dispense 1 toonie, 1 loonie, 1 quarter, 1 dime, and 1 nickel.
Total coins: 5
```
</td>
  </tr>
  <tr>
    <td>1.42</td>
    <td>You need to dispense 1 loonie, 1 quarter, 1 dime, and 1 nickel.
Total coins: 4</td>
    <td>
    
```
How much change is owed? 1.42
You need to dispense 1 loonie, 1 quarter, 1 dime, and 1 nickel.
Total coins: 4
```
</td>
  </tr>
  <tr>
    <td>0.53</td>
    <td>You need to dispense 2 quarters and 1 nickel.
Total coins: 3</td>
    <td>

```
How much change is owed? 0.53
You need to dispense 2 quarters and 1 nickel.
Total coins: 3
```
</td>
  </tr>
  <tr>
    <td>.29</td>
    <td>You need to dispense 1 quarter and 1 nickel.
Total coins: 2</td>
    <td>

```
How much change is owed? .29
You need to dispense 1 quarter and 1 nickel.
Total coins: 2
```
</td>
  </tr>
  <tr>
    <td>1</td>
    <td>You need to dispense 1 loonie.
Total coins: 1</td>
    <td>
    
```
How much change is owed? 1
You need to dispense 1 loonie.
Total coins: 1
```
</td>
  </tr>
  <tr>
    <td>0.02</td>
    <td>You don’t need to dispense change.
Total coins: 0</td>
    <td>

```
How much change is owed? 0.02
You don’t need to dispense change.
Total coins: 0
```
</td>
  </tr>
  <tr>
    <td>

two

-2

2</td>
    <td>



You need to dispense 1 toonie.
Total coins: 1</td>
    <td>

```
How much change is owed? two
How much change is owed? -2
How much change is owed? 2
You need to dispense 1 toonie.
Total coins: 1
```
</td>
  </tr>
</table>


## Source

This problem is based on the [Greedy](https://docs.cs50.net/problems/greedy/greedy.html) problem in Harvard’s CS50 course.
