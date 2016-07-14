# HTML5 Video

Using HTML5 [`video`](https://msdn.microsoft.com/library/hh772959(v=vs.85).aspx), you can embed a full featured video player on your webpage without requiring a third-party plug-in or JavaScript.

Microsoft Edge introduces support for HTTP Live Streaming (HLS), enhanced supported for [MPEG-DASH](http://go.microsoft.com/fwlink/p/?LinkID=533900), and support for Motion JPEG (MJPEG). These media streaming protocols automate adaptive streaming, making it simple for you to deliver professional quality videos, including live streams, on your website without needing a plug-in. For more information about adaptive video streaming, see [Simplified Adaptive Video Streaming: Announcing support for HLS and DASH in Windows 10](http://go.microsoft.com/fwlink/p/?LinkId=529964).

Microsoft Edge also supports in-band closed captioning based on the [mandate by the FCC](http://go.microsoft.com/fwlink/p/?LinkId=524313). For more information on how to map the in-band 608/708 CC to Text Track cues, see [Conversion of 608/708 captions to WebVTT](http://go.microsoft.com/fwlink/p/?LinkId=524314). 

## Adding a video element

In its most basic form, adding a video player to your webpage with the [`video`](https://msdn.microsoft.com/library/hh772959(v=vs.85).aspx) element is done with a single line of HTML. Adding the [`controls`](https://msdn.microsoft.com/library/ff974746) attribute allows users to control the video playback and adding the [`autoplay`](https://msdn.microsoft.com/library/ff974744) attribute will play the video as soon as the page loads. Specify the source of video using the [`src`](https://msdn.microsoft.com/library/ff974762(v=vs.85).aspx) attribute.

``` html
<video src="demo.mp4" controls autoplay ></video> 
```

Since the `video` element only allows you to set one `src` at a time, you can support more than one video file format by using the [`source`](https://msdn.microsoft.com/library/ff975070(v=vs.85).aspx) element. You can use the `source` element to specify several video formats, and the HTML5 video player will pick the one that is the most compatible. This is typically either an .mp4 file or an .ogg/.ogv format. This example shows a video element that has three possible file formats:

``` html
<video controls poster="demo.jpg">
   <source src="demo.mp4" type="video/mp4" />
   <source src="demo.webm" type="video/webm"/>
   <source src="demo.ogv" type="video/ogg"/>             
   <p>HTML5 video element is not supported in your browser</p>
 </video>
```

## Using multiple audio and video tracks

A [`video`](https://msdn.microsoft.com/library/hh772959(v=vs.85).aspx) element can have more than one associated audio track. For example a single video with multiple audio tracks in different languages. The [`audioTrackList`](https://msdn.microsoft.com/library/hh772483(v=vs.85).aspx) object represents a list of [`AudioTrack`](https://msdn.microsoft.com/library/hh772479(v=vs.85).aspx) objects. 

``` javascript
// Returns the first audio track in the array
var myAudioTracks = myVideo.audioTracks[0];
```

You also can access information about the multiple audio tracks using properties like [`enabled`](https://msdn.microsoft.com/library/hh772492(v=vs.85).aspx), [`id`](https://msdn.microsoft.com/library/hh772686(v=vs.85).aspx), [`language`](https://msdn.microsoft.com/library/hh772495(v=vs.85).aspx), and [`sourceBuffer`](https://msdn.microsoft.com/library/dn254952(v=vs.85).aspx).

Similarily, a `video` element can also have more than one associated video track.  The [`videoTrackList`](https://msdn.microsoft.com/library/dn806262(v=vs.85).aspx) object represents a list of [`videoTrack`](https://msdn.microsoft.com/library/dn806264(v=vs.85).aspx) objects. 

``` javascript
// Returns the video track with ID = "english"
var myVideoTrack = myVideo.videoTracks.getTrackByID("english");
```

You also have the ability to get information about the multiple video tracks, and switch between them using the [`selected`](https://msdn.microsoft.com/library/dn806261(v=vs.85).aspx) proprety. 

## HLS and DASH

Microsoft Edge introduces support for HTTP Live Streaming (HLS) and enhanced supported for [MPEG-DASH](http://go.microsoft.com/fwlink/p/?LinkID=533900). These two media streaming protocols automate adaptive streaming, making it simple for web developers to deliver professional quality videos, like live streams, on their web sites without needing a plug-in.

You can detect HLS or the enhanced DASH manifest support using the [`canPlayType`](https://msdn.microsoft.com/en-us/library/ff975191(v=vs.85).aspx) method: 

HLS: Use one of 4 optional MIME types for HLS .m3u8 files (the first two are recommended):
* `video.canPlayType('application/vnd.apple.mpegurl')` 
* `video.canPlayType('audio/mpegurl')` 
* `video.canPlayType('application/x-mpegurl')`
* `video.canPlayType('audio/x-mpegURL') `

DASH: Use the MIME type for DASH .mpd files:

* `video.canPlayType('application/dash+xml')`

For more information about adaptive video streaming, see [Simplified Adaptive Video Streaming: Announcing support for HLS and DASH in Windows 10](http://go.microsoft.com/fwlink/p/?linkid=529964). For additional format support information, go to the [`video`](https://msdn.microsoft.com/library/hh772959(v=vs.85).aspx) page. 

Microsoft Edge now supports in-band closed captioning based on the [mandate by the FCC](http://go.microsoft.com/fwlink/p/?LinkId=524313). For more information on how to map the in-band 608/708 CC to Text Track cues, see [Conversion of 608/708 captions to WebVTT](http://go.microsoft.com/fwlink/p/?LinkId=524314). 

## Supported video file formats

Below is a list of video formats supported by Microsoft Edge.

| Media file to serve  | Extension setting | Mime type setting |
| -------------------- | ----------------- | --------------- | 
Video MP4 | .mp4 | video/mp4
Video WebM | .webm | video/webm
Video HLS | .m3u8 | application/vnd.apple.mpegurl, audio/mpegurl,<br/>application/x-mpegurl, or audio/x-mpegURL 
Video DASH | .mpd | application/dash+xml
Video Motion JPEG | .mjpeg | video/x-motion-jpeg

> Updates to Microsoft Edge introduce support for HLS, DASH, and MJPEG. 

To test other browser support of video file formats, use the [`canPlayType`](https://msdn.microsoft.com/library/ff975191(v=vs.85).aspx) method. This method returns  *probably*, *maybe*, or an empty string depending on whether or not the client can play a given media resource type. The example below demostrates how to use the `canPlayType` method.

``` javascript
function checkVideoCompat() {
	var myvideo = document.createElement('video');
	var msg = document.getElementById("display");
	
	msg.innerHTML = "";
	
	if (myvideo.canPlayType) {
		// CanPlayType returns maybe, probably, or an empty string.
		playMsg = myvideo.canPlayType('video/webm; codecs="vp8, vorbis"');
		if ("" != playMsg) {
			msg.innerHTML += "webm is " + playMsg + " supported<br/>";
		}
	}
	else {
		// File type is not supported
	}
}

```

## Video element keyboard shortcuts

The following table shows keyboard shortcuts for controlling the `video` element in Microsoft Edge. 

| Key | Action | 
| ------- | ----------------- |
Space | Toggle play / pause
M | Mute
Down | Volume down
Up | Volume up
Home or Control + Left | Go to the beginning of the file
End or Control + Right | Go to the end of the file
Left | Rewind back 10 seconds
Right | Skip forward 10 seconds
Shift + Left | Rewind back 30 seconds
Shift + Right | Skip forward 30 seconds
+ | Increase play speed
- | Decrease play speed
T | Toggle controls visibility
K | Skip forward one frame
J | Rewind back one frame
U | Show available tracks
A | Show available subtitles 
Z | Toggle zoom mode
Alt + Enter | Toggle full screen
Escape | Exit full screen


![spec](HTMLVideoElement, AudioTrack, AudioTrackList, VideoTrack, VideoTrackList)

## API reference
[HTML5 Audio and Video](https://msdn.microsoft.com/library/hh772500(v=vs.85).aspx)


## Related topics
[Simplified Adaptive Video Streaming: Announcing support for HLS and DASH in Windows 10](http://go.microsoft.com/fwlink/p/?LinkId=529964)

## Specification
[HTML5](https://www.w3.org/TR/html5/)
