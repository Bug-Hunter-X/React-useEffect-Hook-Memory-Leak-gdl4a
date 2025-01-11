# React useEffect Hook Memory Leak

This repository demonstrates a common error in React's `useEffect` hook: forgetting to include a return statement for cleanup functions.  This can lead to memory leaks and unexpected behavior.

## Bug Description

The `MyComponent` uses the `useEffect` hook to log the count whenever it updates. However, it lacks a return statement, which would typically be used to clean up after the effect (e.g., canceling subscriptions or timers).  The lack of cleanup leads to the effect running repeatedly without stopping, potentially consuming significant resources, resulting in a memory leak and even an infinite render loop.

## Solution

The solution is to add a return statement to the `useEffect` function. This return statement should contain a cleanup function. In this specific case, while there are no subscriptions to cancel, the return statement alone ensures the effect runs cleanly on unmount.  This prevents memory leaks and performance issues.

## How to Reproduce

1. Clone this repository.
2. Navigate to the project directory using your terminal.
3. Install dependencies using `npm install`.
4. Run the application using `npm start`.
5. Observe the console logs. You'll see a continuous stream of log messages, demonstrating the uncontrolled effect.

## How to Fix

1. Refer to the `bugSolution.js` file for the corrected code. The fix is simple: add an empty return statement in the `useEffect` hook.
2. The corrected code will only log when the component updates and there won't be any more console logs after unmounting the component.