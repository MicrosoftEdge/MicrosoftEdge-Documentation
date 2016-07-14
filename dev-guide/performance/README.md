# Performance features

## Animation Timing API

The [Animation Timing API](./animation-Timing-API) provides a smoother and more efficient way to create animated webpages by calling the animation frame when the system is ready to paint the frame. This helps you avoid overdrawn animations, wasted CPU cycles, and unnecessary power usage.

## Efficient Script Yielding

Use [`setImmediate`](./efficient-script-yielding) to solve the problems of using `setTimeout` by addressing the core performance problem without negatively impacting power consumption. Flush the browser event queue and receive an immediate callback without the minimum delays enforced by `setTimeout`.
 
## Navigation Timing API

The [Navigation Timing API](./navigation-Timing-API) makes it easy to measure the real-world speed and performance of websites and locate problem areas that need tuning. 

## Page Visibility API

The [Page Visibility API](./page-Visibility-API) provides a means for developers to determine the current visibility of a document (or whether the page is in focus) and be notified when the visibility changes.

## Prerender and prefetch support

[Prerender and prefetch support](./prerender-and-prefetch-support) enables content to download before it is needed so that resources are instantly available when the user wants them.

## Resource Timing API

The [Resource Timing API](./resource-Timing-API) allows web applications to access network timing information regarding how long it takes for resources to load in a document.

## User Timing API

The [User Timing API](./user-Timing-API) enables developers to accurately measure the length of AJAX requests, report on performance, and create benchmarks for JavaScript code using high precision timestamps.
