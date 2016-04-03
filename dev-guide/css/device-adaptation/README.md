# Device adaptation

As a web developer, you are faced with a dilemma: Code your site to work with as many devices, sizes, and resolutions as possible; or risk alienating users by potentially allowing your content to be either clipped (in fixed layouts) or jumbled confusingly (in fluid layouts). The [`@-ms-viewport`](https://msdn.microsoft.com/library/hh869615) rule, in combination with CSS Media Queries, attempts to solve this dilemma by enabling developers to optimize the layout of sites and apps for different devices with minimal effort.

The `@-ms-viewport` rule is based on the `@viewport` rule, which is defined in the [CSS Device Adaptation specification](http://go.microsoft.com/fwlink/p/?LinkId=233011). 

> Microsoft Edge only supports the `width` and `height` properties of `@-ms-viewport` 

## Viewing sites in narrow windows
Some sites on the web today become difficult to use when viewed in a very narrow window. Fixed layouts can become clipped, and fluid layouts can become jumbled. To avoid problems with clipping or jumbling of content, content is automatically scaled down. This requires no extra effort from you as a developer, but it might not be ideal, depending on the default width of your content. Users will be forced to zoom every time they need to access the content.

The `@-ms-viewport` rule makes it possible to deliver optimized sites and apps. Instead of forcing a "one-size-fits-all" scenario where a small UI might be awkwardly enlarged or a large UI over-compressed, using `@-ms-viewport` and CSS Media Queries enable optimization of your site or app for different ranges of resolutions. Specify that pages optimized for a particular range are scaled more naturally for devices with resolutions within that range. This enables you to optimize your site not just for desktop displays, but for phones, tablets, or even for the snapped state.

## Using the @-ms-viewport rule
The `@-ms-viewport` rule works in tandem with media queries to help optimize your layout. Typically, you nest the `@-ms-viewport` rule inside the media query, as shown in the following pseudocode snippet:

```CSS
@media [media query logic here] {
  @-ms-viewport {
    [viewport size here]
  }
  [CSS for this layout combination goes here.]
}
```
Be aware that, in browsers that don't support the `@-ms-viewport` rule, this CSS degrades gracefully. The `@-ms-viewport` rule and its contents, if not recognized, are simply ignored.

## Example usage: Web page with snapped state optimization

The following example shows a common use for the `@-ms-viewport` rule. Specifically, this selector can be used to optimize a small version of your webpage for viewing in the snapped state.

```CSS
@media screen and (max-width: 400px) {
  @-ms-viewport { width: 320px; }
  /* CSS for 320px width Modern taskbar layout goes here */
}
```
Any viewport smaller than 400 pixels in width (for instance, the snapped state), is laid out to a width of 320 pixels and scaled to fit. The CSS listed underneath it (which has presumably been optimized for a small screen) will be applied.

## Example usage: Fixed-size application

Following is a very basic example of the `@-ms-viewport` rule in use, without any media query (indicating the rule applies in all cases).

```CSS
@-ms-viewport {
  width: 1024px;
  height: 768px;
}
```
This example might be used, for instance, in a Universal Windows Platform app using JavaScript that is locked to landscape mode. It specifies that, regardless of the resolution of the display or the display ratio (4:3, 16:9 widescreen, and so on), the displayed content (the "viewport") must always contain at minimum 1024 pixels by 768 pixels. In the case of a display that is, for instance, 1920 pixels by 1080 pixels (16:9 widescreen ratio), the viewport is scaled up to fit the display's height. Because it is a widescreen display, the application can be centered using normal CSS methods for a "pillarboxing" effect (black bars on both sides of the viewport). On a 1280×960 display, because its aspect ratio is equal to that of the 1024×768 viewport, the viewport would scale up to fill the display completely.

We can expand this example by adding media queries that allow for both landscape and portrait modes in this app:

```CSS
@media screen and (orientation: landscape) {
  @-ms-viewport {
    width: 1024px;
    height: 768px;
  }
  /* CSS for landscape layout goes here */
}

@media screen and (orientation: portrait) {
  @-ms-viewport {
    width: 768px;
    height: 1024px;
  }
  /* CSS for portrait layout goes here */
}
```

This example does effectively the same thing as the previous example, except that the portrait orientation is accounted for in the second @media rule. In the case of portrait mode, the orientation of the content might change (text and pictures might be laid out differently to account for the difference in direction), but the viewport stays the same. The width and height values have been swapped, so the visible content area does not change.

## Example usage: Optimizing for width

Following is an example of a page whose scaling behavior has been optimized for width using media queries and `@-ms-viewport`. Notice that each media query covers a different resolution range. Within each range, the `@-ms-viewport` rule specifies what width any device that falls within that range should scale to. The CSS that follows each rule then defines exactly how to display the content that has been scaled for that resolution range.

```CSS
@media screen and (max-width: 400px) {
    @-ms-viewport { width: 320px; }
    /* CSS for 320px layout goes here */
}

@media screen and (min-width: 400px) and (max-width: 640px) {
    @-ms-viewport { width: 400px; }
    /* CSS for 400px layout goes here */
}

@media screen and (min-width: 640px) and (max-width: 1024px) {
    @-ms-viewport { width: 640px; }
    /* CSS for 640px layout goes here */
}

@media screen and (min-width: 1024px) and (max-width: 1366px) {
    @-ms-viewport { width: 1024px; }
    /* CSS for 1024px layout goes here */
}

@media screen and (min-width: 1366px) {
    /* CSS for 1366px layout goes here */
}
```

## Example usage: Opting out of automatic scaling

By default, Microsoft Edge automatically scales content when the window is narrower than 1024 pixels. This primarily includes the snapped state and portrait mode.

However, in cases where this automatic scaling is not needed or desired, the device-width keyword can be used. This keyword signifies that the page is optimized to work well regardless of the width of the device.

```CSS
@-ms-viewport { width: device-width; }
```
When using this keyword, make sure that the page continues to work well in the narrow snapped state and portrait modes. 

## Example: "Make it Snappy" -- See @-ms-viewport in action
First, an example of page width layout without applying media queries, but without the `@-ms-viewport` to styling.
![Make It Snappy @-ms-viewport Demo](../../media/css-device-viewport-makeitsnappyDemo2.gif)

Applying `@-ms-viewport` will reflect the example screen shot in Microsoft Edge.

```CSS
@media screen and (max-width: 480px) {
    @-ms-viewport { width: 320px; }
}

@media screen and (max-width: 959px) and (min-width: 768px) {
    @-ms-viewport { width: 768px; }
}
```

![spec](CSS  Device Adaptation)

## API Reference

[Device Adaptation](https://msdn.microsoft.com/library/hh869463)


## Specification

[CSS Device Adaptation](http://go.microsoft.com/fwlink/p/?LinkID=233011)
