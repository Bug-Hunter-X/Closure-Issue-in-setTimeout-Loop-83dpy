# JavaScript Closure Issue in setTimeout Loop

This repository demonstrates a common issue with closures in JavaScript's `setTimeout` function within loops.  The expected behavior is to log numbers 0 through 9 with a one-second delay between each. However, due to the way closures work in JavaScript, all logs will output the final value of `i`, which is 10.

## Bug Description

The problem lies in how the `setTimeout` callback function captures the variable `i`.  It doesn't capture the value of `i` at the time of each iteration; instead, it captures the reference to `i`. By the time the `setTimeout` callbacks finally execute, the loop has already completed, and `i` is 10.

## Solution

The solution involves using an immediately invoked function expression (IIFE) to create a new scope for each iteration, effectively capturing the value of `i` at that specific moment.  This ensures each callback has its own private copy of `i`.