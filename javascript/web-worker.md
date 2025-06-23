
## Web Worker

A Web Worker is a feature in JavaScript that allows you to run scripts in the background, on a separate thread, 
so your web page (main thread) stays smooth and responsive — even during heavy computations.

- 1. Key Idea:
JavaScript runs on a single thread — so when a task takes a long time (e.g. big loops, data parsing, image processing), the browser can freeze or become unresponsive.
A Web Worker fixes that by running the heavy code outside the main UI thread.

- 2. Pros
  - 1. Summing large numbers or running loops
  - 2. Processing large files (CSV, JSON, XML)
  - 3. Image or video processing
  - 4. Real-time analytic
  - 5. Background syncing or calculations in dashboards

- 3. Limitations 
  - 1. No access to the DOM
  - 2. Must be served over http:// or https:// (not file://)
  - 3. Communication is async — needs postMessage and event handlers
  - 4. Same-origin policy applies (can't load cross-origin scripts)

#### Example
  ```ts
  // worker.js
  self.onmessage = function(e) {
    let total = 0;
    for (let i = 0; i <= e.data; i++) total += i;
    self.postMessage(total); // Send result back
  };
  ```

  ```ts
    // main.js
    const worker = new Worker("worker.js");
    worker.postMessage(1000000000); // Start heavy task

    worker.onmessage = function(e) {
      console.log("Result:", e.data); // Use result
    };

  ```