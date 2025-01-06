# React 19 useEffect Hook with setInterval Memory Leak

This repository demonstrates a common error when using the `useEffect` hook with `setInterval` in React 19.  Forgetting to include a cleanup function leads to a memory leak, as the interval continues to run even after the component unmounts.  This example shows the problem and its solution.

## Bug

The `bug.js` file contains the erroneous code.  The `setInterval` function is called within the `useEffect` hook without a cleanup function to stop the interval when the component is unmounted. This results in the interval continuously updating the state, even when the component is no longer in the DOM.  This consumes resources and leads to a memory leak over time.

## Solution

The `bugSolution.js` file shows the corrected code. The `setInterval` call returns an ID.  This ID is used in the cleanup function which is returned by `useEffect`.  When the component unmounts, React calls this cleanup function and `clearInterval` stops the interval from running further.