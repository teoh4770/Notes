# Inactive Tab Throttling + Solutions

This repository explains what is inactive tab throttling in web, show the effect of inactive tab throttling, and possible way to fix this, in my own terms.

## Why should I care?

Create a timer is not as easy as I thought. At first glance, it seems like making a timer would be as simple as adding an interval and putting the logic there. However, the timer of my app slows or stops entirely when I switch to another tab for a while (~30 seconds in this case), lead to unresponsive user interface. I don't want timer to delay when I switch to another tab. I have learnt that this specific issue is called `Inactive Tab Throttling`.

## What is inactive tab throttling in web?

In layman term, browser will save some power(CPU, RAM) for the system while it detects the current tab is inactive. Browser can achieve this by slowing down the heavy running tasks in inactive tabs. 
In exchange of saving resources, the tasks are delay, thus affect the user experience.

Examples of heavy running task
1. Video, Audio Playback
2. Background Animation
3. Timer function like setInterval
4. Network Request
5. ...

## Solution

**Web worker**

> By moving the heavy running process away from the main JavaScript thread to separate thread, we can mitigate the issue by a lot.

A JavaScript API called `web worker` that enables heavy running task to run on the background. It separates the process from the main thread, which should be best handling UI updates. Since it is running on the background, it reduces the impact of `Inactive Tab Throttling` even if the tab is inactive.

```js
// Create a new worker
const worker = new Worker("background-worker.js");

// Send a message to the worker to start processing
worker.postMessage("start-processing");

// Listen for messages from the worker
worker.onmessage = function(event) {
  // ...complex calculation
  console.log("Received message from worker: " + event.data);
}
```

Note
To mitigate the effect even more, we want to make sure the timer states is not depending on the `setInterval` method. We can update the timer states with proper timestamp instead of `setInterval` method updates.

> Use timestamps to correct the timer for errors associated with throttling and adjust for any drift


### Code examples

_The timer state (count) depends on setInterval update._
```js
let count = 0;
let milliseconds = 1000; // 1s = 1000ms

const updateTime = () => {
  **count++;**
  // ...
};

const intervalId = setInterval(updateTime, milliseconds);
```

The timer state (count) depends on the actual timestamp instead of setInterval update.
```js
let count = 0;
let lastTime = Date.now();

const updateTime = () => {
  const currentTime = Date.now();
  **count += currentTime - lastTime;**
  lastTime = currentTime;

  // ...
};

const intervalId = setInterval(updateTime, 250);
// The interval callback runs 4 times per second, allowing for more frequent updates and reducing the impact of `inactive tab throttling` by increasing accuracy.
```


## Reference

[Tab Throttling In Browsers](https://aboutfrontend.blog/tab-throttling-in-browsers/#:~:text=Inactive%20tab%20throttling%20is%20a,and%20Safari%20have%20this%20feature.)
[Overcoming browser throttling](https://medium.com/@adithyaviswam/overcoming-browser-throttling-of-setinterval-executions-45387853a826)
[Inactive Tab Throttling Demo](https://w2or0.csb.app/)
