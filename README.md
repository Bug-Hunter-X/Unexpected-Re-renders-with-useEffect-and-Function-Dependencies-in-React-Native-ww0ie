# Unexpected Re-renders with useEffect and Function Dependencies in React Native

This repository demonstrates a common React Native bug related to the `useEffect` hook and function dependencies.  Incorrectly including a function in the dependency array leads to unexpected re-renders. 

## Bug Description
The `useEffect` hook is used to perform side effects.  When a function is added to the dependency array, React compares the reference of the function on each render.  Since a new function object is created on every render, this comparison always fails, causing the effect to run repeatedly, leading to potential performance issues or infinite loops.

## Solution
To fix this, avoid passing the function directly to the dependency array.  Instead, use a value that does not change between renders.  If necessary, create a memoized function using `useCallback`.