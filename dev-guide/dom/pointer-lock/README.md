# Pointer Lock (Mouse Lock)

Microsoft Edge (build 10532+) now supports the Pointer Lock API (previously called Mouse Lock) for access to raw mouse movement, locking the target of mouse events to a single element, eliminating limits of how far mouse movement can go in a single direction, and removing the cursor from view. Accessing mouse movement data enables the ignoring of boundaries resulting from screen edges where the cursor can't go beyond, providing proper control for first person or real time strategy games by locking the mouse to a specific HTML element. With the mouse locked, the pointer can be moved all around, and it will never leave the focus of the element, a requirement for many games and 3D model views.

##  Activating Pointer Lock

### requestPointerLock method

The first step in activating the Pointer Lock API is to request that the pointer lock be locked to a target element using the [`requestPointerLock()`](https://msdn.microsoft.com/library/mt560346.aspx) method.

```js
canvas.requestPointerLock()
```

### onpointerlockchange event

After the pointer lock request, the user must give permission, then, upon a successful request, a [`pointerlockchange`](https://msdn.microsoft.com/library/mt560349.aspx) event fires. An Event Listener must be added for `pointerlockchange`, which fires whenever a change in the pointer lock state occurs.

```js
document.addEventListener('pointerlockchange', lockChangeAlert, false);
```

### pointerLockElement property

Use the [`pointerLockElement`](https://msdn.microsoft.com/library/mt560345.aspx) property to retrieve the target element for mouse events under pointer lock state. Inside the `pointerlockchange` callback, a check must be performed to see whether the pointer has been locked or unlocked. Use `document.pointerLockElement` to check if it is equal to the element that pointer lock was requested for. If it is equal, the pointer successfully locked to the element, if not, the pointer was unlocked.

```js
function lockChangeLog() {
  if(document.pointerLockElement === canvas) {
    console.log('The pointer is now locked');
    document.addEventListener("mousemove", mousemoveCallback, false);
  } else {
    console.log('The pointer is now unlocked');
    document.removeEventListener("mousemove", mousemoveCallback, false);
  }
}
```

The `lockChangeLog` function above checks whether the `pointerLockElement` property is `canvas`. If so, a message is sent to the console that "The pointer is now locked" and an event listener is attached, using the `mousemove` event, to handle mouse movements with the `mousemoveCallback` function. If not, the message will read "The pointer is now unlocked" and the `mousemove` event listener is removed.

### mousemove event

The [`mousemove`](https://msdn.microsoft.com/library/ms536947.aspx) event fires when the user moves the mouse over an object. The Pointer Lock API extends the normal [`MouseEvent`](https://msdn.microsoft.com/library/ff974344.aspx) interface with two movement attributes: [`movementX`](https://msdn.microsoft.com/library/mt560347.aspx) and [`movementY`](https://msdn.microsoft.com/library/mt560348.aspx). When pointer lock is enabled `clientX`, `clientY`, `screenX`, and `screenY` remain constant. Inside the `mousemove` callback, mouse motion data can be extracted from the event's `movementX` and `movementY` fields.The `movementX` and `movementY` attributes are updated with the number of pixels the pointer would have moved since the last event was delivered. In other words, `event.movementX = currentCursorPositionX - previousCursorPositionX;` and `event.movementY = currentCursorPositionY - previousCursorPositionY;`.


### exitPointerLock method

When the browser locks the pointer, a pop-up will let the user know that the pointer has been locked and can be canceled by pressing the 'Esc' key. Pressing the 'Esc' key activates [`exitPointerLock`](https://msdn.microsoft.com/library/mt560344.aspx), exiting the document out of pointer lock state. Using the `document.exitPointerLock()` method also causes the `pointerlockchange` event to fire and the system mouse cursor to once again display.

### pointerlockerror event

When there is an error caused by calling `requestPointerLock` or `exitPointerLock`, the [`pointerlockerror`](https://msdn.microsoft.com/library/mt560350.aspx) event is fired.

```js
document.addEventListener('pointerlockerror', lockError, false);
function lockError(e) {
  alert("Pointer lock failed"); 
}
```

The Pointer Lock API can only lock one iframe at a time. To avoid errors when using pointer lock on multiple iframes, be sure to unlock the pointer before attempting to lock into a new iframe.

## Pointer Lock CodePen Demo
In this demo, click on the canvas and your mouse will directly control the ball inside the canvas, not your mouse pointer. Press escape to return to the standard mouse state.

![codepen](https://codepen.io/MicrosoftEdgeDocumentation/pen/zqYBbb)

![spec](Pointer Lock)

## API Reference

[requestPointerLock](https://msdn.microsoft.com/library/mt560346.aspx)

[pointerLockElement](https://msdn.microsoft.com/library/mt560345(v=vs.85).aspx) 

[onpointerlockchange](https://msdn.microsoft.com/library/mt560349(v=vs.85).aspx)

[exitPointerLock](https://msdn.microsoft.com/library/mt560344.aspx)

[onpointerlockerror](https://msdn.microsoft.com/library/mt560350(v=vs.85).aspx)

[mousemove](https://msdn.microsoft.com/library/ms536947.aspx)

## Demo

[Pointer Lock Demo on CodePen](https://codepen.io/MicrosoftEdgeDocumentation/pen/zqYBbb)

## Related Topics

[How to Use Canvas to Create a Space Game](https://msdn.microsoft.com/library/gg589490.aspx)

[Using HTML5 canvas and JavaScript to move a vehicle in a game](https://msdn.microsoft.com/library/gg589516.aspx)

[Unleash the power of HTML 5 Canvas for gaming](https://blogs.msdn.microsoft.com/eternalcoding/2012/03/22/unleash-the-power-of-html-5-canvas-for-gaming/)

[About Mouse Capture](https://msdn.microsoft.com/library/ms537630.aspx)

## Specification

[Pointer Lock API, W3C](https://w3c.github.io/pointerlock/)

