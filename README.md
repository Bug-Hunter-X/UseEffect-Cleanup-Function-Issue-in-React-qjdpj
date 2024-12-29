# React useEffect Cleanup Function Issue

This repository demonstrates a common issue with the cleanup function in React's `useEffect` hook. The problem lies in how the `clearInterval` function is used to stop the interval timer when the component unmounts.  Incorrect usage can lead to memory leaks.

## Bug Description

The provided `MyComponent` uses `setInterval` to update a counter every second. The `useEffect` hook includes a cleanup function (`clearInterval`) to clear the interval when the component unmounts or updates. However, this cleanup might not always be called under certain conditions, leaving the interval running in the background which leads to memory leaks.

## Solution

The solution involves ensuring the `clearInterval` function is correctly called in all cases, even when the component unmounts unexpectedly or before the initial render, by calling `clearInterval` only if `intervalId` is defined.   This ensures the interval is stopped before setting the new one to prevent race conditions.

## How to Reproduce

1. Clone this repository.
2. Run `npm install` to install dependencies.
3. Run `npm start` to start the development server.
4. Observe the counter in the browser.  Notice that if you quickly remount or unmount the component, the memory leak may not show up immediately, but over time and repeated actions, this will affect performance.
