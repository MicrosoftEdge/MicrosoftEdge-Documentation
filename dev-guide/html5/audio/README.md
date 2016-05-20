# HTML5 Audio

You can use the `audio` element to embed simple sound effects, background audio, or more sophisticated audio engies to your webpage without requiring script or add-on controls.

To do more complex processing and syntehsizing of audio in web applications, check out the [Web Audio API](../../multimedia/web-audio). 

## Adding an audio element

To add audio to your webpage, you can declare an [`audio`](https://msdn.microsoft.com/library/hh772923(v=vs.85).aspx) element in your HTML, instantiate a new `audio` element in JavaScript, or embed an audio stream into your page. 

The `audio` element is added directly to your HTML code, using the [`src`](https://msdn.microsoft.com/library/ff974762(v=vs.85).aspx) property to specify the audio file to play and the `controls` attribute so that the built-in, player controls are used. If you use the browser's intrinsic player, no additional scripting is required.

``` html
<audio src="audio/sample.mp3" controls autoplay></audio>
```

Because not all browsers support the same audio formats, you can use the [`source`](https://msdn.microsoft.com/library/ff975070(v=vs.85).aspx) element to specify several file formats to try. The following example shows three formats:

``` html
<!-- The browser will automatically choose the format it supports. -->
<audio controls="true">
   <source src="audio/sample.mp3" type="audio/mp3"> 
   <source src="audio/sample.ogg" type="audio/ogg"> 
   <source src="audio/sample.aac" type="audio/mp4"> 
   <!-- If no support at all. -->
   HTML5 audio not supported 
</audio>
```

Instantiating a new `audio` element in JavaScript gives you more flexibility and better management of the network flow, as it defers the loading of the audio clip to a specific time during the application lifecycle.

``` js
var audio = document.createElement("audio");
if (audio != null && audio.canPlayType && audio.canPlayType("audio/mpeg"))
{
   audio.src = "audio/sample.mp3";
   audio.play();
}
```

Embedding an audio stream into your page (less recommended) consists of embedding the audio files as data-uri into the page, reducing the number of requests to the server. 

``` html
<audio src="data:audio/mpeg,ID3%02%00%00%00%00%…" autoplay></audio>
```

## Preloading audio

Once you have your audio element, you can choose the best preloading strategy. The [`audio`](https://msdn.microsoft.com/library/hh772923(v=vs.85).aspx) element has a [`preload`](https://msdn.microsoft.com/library/ff974759(v=vs.85).aspx) property with three possible values:

* `none`: The document author does not expect the user to need the media resource, or the server wants to minimize unnecessary traffic.
* `metadata`: The document author does not expect the user to need the resource. However, if the resource metadata (dimensions, first frame, track list, duration, and so on) is available, using a resource is preferred unless it impacts performance to do so.
* `auto`: The document author gives the user access to media content, which includes the ability to download the entire resource.

> NOTE: When you set the `src` property of the `audio` element, the `preload` property will be set to `auto`.

## Looping audio

Using the [`audio`](https://msdn.microsoft.com/library/hh772923(v=vs.85).aspx) element, you can also loop a sound clip. You can do this using the [`loop`](https://msdn.microsoft.com/library/ff974753(v=vs.85).aspx) property. This setting will loop your clip forever, or until the user or the application activates the pause() audio control.

``` html 
<audio src="sample.mp3" autoplay loop></audio>
```

You can also loop an audio file by calling the [`play()`](https://msdn.microsoft.com/library/ff975194(v=vs.85).aspx) method when the audio clip ends; doing so will allow you eventually to manage the delay between one loop and the other.

``` js
var audio = document.createElement("audio");
audio.src = "sample.mp3";
audio.addEventListener('ended', function () {
   // Wait 500 milliseconds before next loop
   setTimeout(function () { audio.play(); }, 500);
}, false);

audio.play(); 
```

## Fast-forwarding, rewinding, and restarting audio

The [`audio`](https://msdn.microsoft.com/library/hh772923(v=vs.85).aspx) object in HTML5 provides methods, properties, and events that you can use to control playback from JavaScript. While an audio file is playing, the [`currentTime`](https://msdn.microsoft.com/library/ff974748(v=vs.85).aspx) property tracks where the playback is in the audio clip. By changing the value of `currentTime`, you can skip forward, backward, or restart the playback. 

Using a progress bar created with the [`canvas`](https://msdn.microsoft.com/library/ff975062(v=vs.85).aspx) element, this [example](https://codepen.io/MicrosoftEdgeDocumentation/pen/wGGGRp) uses three functions to increment the value of `currentTime` (fast forward), decrement the value of `currentTime` (rewind), and set the value of `currentTime` to zero (restart). 

![codepen](https://codepen.io/MicrosoftEdgeDocumentation/pen/wGGGRp)

## Supported audio file formats 

Below is a list of audio formats supported by Microsoft Edge.

| Media file to serve  | Extension setting | Mime type setting |
| -------------------- | ----------------- | --------------- | 
Audio mp3 | mp3 | audio/mpeg 
Audio mp4 | m4a | audio/mp4 
Audio mp4 | aac | audio/mp4
Audio WebM | webm | audio/webm 
Audio WAV | wav | audio/wav, audio/wave, audio/x-wave, audio/vnd.wave 

> WebM audio and video files can be supported by installing the WebM components from [The WebM project](http://go.microsoft.com/fwlink/p/?LinkID=218894). 

> Audio WAV support was introduced in Microsoft Edge.

To test other browser support of audio file formats, use the [canPlayType](https://msdn.microsoft.com/library/ff975191(v=vs.85).aspx) method. This method returns `probably`, `maybe`, or an empty string depending on whether or not the client can play a given media resource type. The example below demostrates how to use the `canPlayType` method.

``` js
function checkAudioCompat() {
   var myAudio = document.createElement('audio');
   var msg = document.getElementById("display");

   msg.innerHTML = "";
   
   if (myAudio.canPlayType) {
       // CanPlayType returns maybe, probably, or an empty string.
       var playMsg = myAudio.canPlayType('audio/mpeg');
       if ( "" != playMsg) {
           msg.innerHTML += "mp3 is " + playMsg + " supported";
       }
   }
   else {
       // Type is not supported               
   }
}
```

![spec](HTMLAudioElement)

## API Reference
[HTML5 Audio and Video](https://msdn.microsoft.com/library/hh772500(v=vs.85).aspx)

## Demos
[Dolby Audio Experience](https://developer.microsoft.com/en-us/microsoft-edge/testdrive/demos/dolbyaudioexperience/)

## Specification
[HTML5](https://www.w3.org/TR/html5/)
