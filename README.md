# React Firebase onAuthStateChanged Unsubscribe Issue

This repository demonstrates a common issue when using Firebase's `onAuthStateChanged` in React applications: forgetting to unsubscribe from the listener. This can lead to memory leaks and unexpected behavior.

## The Problem

The `onAuthStateChanged` function returns an unsubscribe function.  If this function isn't called when the component unmounts, the listener remains active, potentially causing memory leaks and continued state updates even when the component is no longer rendered.

## The Solution

The solution involves calling the returned unsubscribe function within the component's cleanup (useEffect) method.  This ensures the listener is properly removed when the component is unmounted. 

## How to reproduce the bug
1. Clone this repo
2. Run `npm install`
3. Run `npm start`
4. Observe the console logs.  Uncomment the problematic code in `bug.js` to see the memory leak. (Check the browser's developer tools to see the effects).