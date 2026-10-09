# video

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @Lichtschein-->
<!--Designer: @fenglinbailu-->
<!--Tester: @liuli0427-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=93458ca6cb2d2618da5fc6bdfa2819210775aa38 translatedAt=2026-06-23T07:35:22.637Z pushedAt=2026-06-24T01:11:44.229Z -->

>  **NOTE**
>
>  This component is supported since API version 4. Updates will be marked with a superscript to indicate their earliest API version.
>

The **\<video>** component provides a video player.

## Child Components

Not supported

## Attributes

In addition to the [universal attributes](js-components-common-attributes.md), the following attributes are supported.

| Name     | Type    | Default Value | Mandatory | Description                                |
| -------- | ------- | ----- | ---- | ---------------------------------------- |
| muted    | boolean | false | No   | Whether the video is muted.<br/>**true**: The video is muted.<br/>**false**: The video is unmuted.                           |
| src      | string  | -     | No   | Path of the video content to play.                               |
| autoplay | boolean | false | No   | Whether the video is played automatically.<br/>**true**: The video is played automatically.<br/>**false**: The video is not played automatically.                                |
| controls | boolean | true  | No   | Whether the control bar is displayed during video playback. If the value is set to **false**, the control bar is not displayed. The default value is **true**, indicating that the platform can either show or hide the control bar. |

## Styles

In addition to the [universal styles](js-components-common-styles.md), the following styles are supported.

| Name         | Type     | Default Value     | Mandatory   | Description                                       |
| ---------- | ------ | ------- | ---- | ---------------------------------------- |
| object-fit | string | contain | No    | Video scale type. If **poster** has been assigned a value, the setting of this style will affect the scaling type of the video poster. For details, see object-fit enums. |

**Table 1** object-fit enums

| Type   | Description                        |
| ---- | ------------------------- |
| fill | The image is resized to fill the display area, and its aspect ratio is not retained. |

## Events

In addition to the [universal events](js-components-common-events.md), the following events are supported.

| Name         | Parameter                                       | Description                                    |
| ---------- | ---------------------------------------- | ------------------------------------- |
| prepared   | {&nbsp;duration:&nbsp;value&nbsp;}<sup>5+</sup> | Triggered when the video preparation is complete. The video duration (in seconds) is obtained from **duration**. |
| start      | -                                        | Triggered when the video is played.                             |
| pause      | -                                        | Triggered when the video playback is paused.                             |
| finish     | -                                        | Triggered when the video playback is finished.                           |
| error      | -                                        | Triggered when the video playback fails.                           |
| seeking    | {&nbsp;currenttime:&nbsp;value&nbsp;}    | Triggered to report the time (in seconds) when the progress bar is being dragged.                  |
| seeked     | {&nbsp;currenttime:&nbsp;value&nbsp;}    | Triggered to report the playback time (in seconds) when the user finishes dragging the progress bar.               |
| timeupdate | {&nbsp;currenttime:&nbsp;value&nbsp;}    | Triggered once per 250 ms when the playback progress changes. The unit of the current playback time is second.       |

## Methods

In addition to the [universal methods](js-components-common-methods.md), the following methods are supported.

| Name             | Parameter                                    | Description                |
| -------------- | ------------------------------------- | ----------------- |
| start          | -                                     | Starts playing a video.           |
| pause          | -                                     | Pauses a video.         |
| setCurrentTime | {&nbsp;currenttime:&nbsp;value&nbsp;} | Sets the video playback position, in seconds. |

>  **NOTE**
>  The methods in the above table can be called after the **attached** callback is invoked.

## Example

```html
<!-- xxx.hml -->
<div class="container">
<!-- Replace '/common/myDream.mp4' with the resource file you use. -->
    <video id='videoId' src='/common/myDream.mp4' muted='false' autoplay='false'
           controls='true' onprepared='preparedCallback' onstart='startCallback'
           onpause='pauseCallback' onfinish='finishCallback' onerror='errorCallback'
           onseeking='seekingCallback' onseeked='seekedCallback'
           ontimeupdate='timeupdateCallback'
           style="object-fit: fill; width: 100%; height: 900px;"
           onclick="change_start_pause">
    </video>
</div>
```

```css
/* xxx.css */
.container {
  justify-content: center;
  align-items: center;
}
```

```js
// xxx.js
export default {
    data: {
        event: '',
        seekingTime: '',
        timeupdateTime: '',
        seekedTime: '',
        isStart: true,
        duration: '',
    },
    preparedCallback: function (e) {
        this.event = 'Video successfully connected.';
        this.duration = e.duration;
    },
    startCallback: function () {
        this.event = 'Playback starts.';
    },
    pauseCallback: function () {
        this.event = 'Playback pauses.';
    },
    finishCallback: function () {
        this.event = 'Playback ends.';
    },
    errorCallback: function () {
        this.event = 'Playback error.';
    },
    seekingCallback: function (e) {
        this.seekingTime = e.currenttime;
    },
    timeupdateCallback: function (e) {
        this.timeupdateTime = e.currenttime;
    },
    change_start_pause: function () {
        if (this.isStart) {
            this.$element('videoId').pause();
            this.isStart = false;
        } else {
            this.$element('videoId').start();
            this.isStart = true;
        }
    },
}
```

![en-us_gif_js_media_video](figures/js-media-video.gif)