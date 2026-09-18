# Video

The **Video** component is used to play a video and control its playback. > **NOTE** > > The **Video** component provides only simple video playback features. For complex video playback control > scenarios, consider using the [AVPlayer](../../apis-media-kit/arkts-apis/arkts-media-media-avplayer-i.md) APIs in conjunction with the > XComponent component. > When using **expandSafeArea** to extend into safe areas, the **Video** component's content display area does not > support expansion. > > **Required Permissions** > > To use online videos, you must apply for the ohos.permission.INTERNET permission. For details about how to apply > for a permission, see [Declaring Permissions](../../../security/AccessToken/declare-permissions.md). > > **Child Components** > > Not supported.

## Video

```TypeScript
Video(value: VideoOptions)
```

Defines the constructor of video component.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [VideoOptions](arkts-arkui-videooptions-i.md) | Yes | Video information. |

## Summary

### Interfaces

| Name | Description |
| --- | --- |
| [FullscreenInfo](arkts-arkui-fullscreeninfo-i.md) | Describes whether the video is in full-screen playback mode. |
| [PlaybackInfo](arkts-arkui-playbackinfo-i.md) | Describes the current progress of video playback. |
| [PosterOptions](arkts-arkui-posteroptions-i.md) | Defines display options for the first frame of the video. |
| [PreparedInfo](arkts-arkui-preparedinfo-i.md) | Describes the duration of the video. |
| [VideoOptions](arkts-arkui-videooptions-i.md) | Defines the options of the **Video** component. |

### Enums

| Name | Description |
| --- | --- |
| [PlaybackSpeed](arkts-arkui-playbackspeed-e.md) | Enumerates video playback speed options. |
| [SeekMode](arkts-arkui-seekmode-e.md) | Enumerates video seek modes. |

## Examples

```TypeScript
### Example 1: Implementing Basic Video Playback Features

The basic usage includes: control bar, preview image, autoplay, playback speed, keyboard shortcut response (since API version 15, you can set the component to respond to keyboard shortcuts through [enableShortcutKey](arkts-arkui-video-comp-attribute.md#enableshortcutkey)), controller (start playback, pause playback, stop playback, reset the video player, seek, etc.), first-frame display (since API version 18, you can set the first-frame display options of video playback through [posterOptions](#posteroptions18). Since API version 21, posterOptions supports setting the transition animation effect when the preview image content of the current video changes through the contentTransitionEffect parameter of [PosterOptions](#posteroptions18).), and some state callback methods.


```

```TypeScript
### Example 2: Enabling AI Image Analyzer

This example shows how to use the enableAnalyzer attribute to enable AI image analyzer.
```

```TypeScript
### Example 3: Playing a Dragged-in Video

This example demonstrates how to enable the Video component to play a video that is dragged into it.
```

```TypeScript
### Example 4: Setting the Video Fill Mode

This example shows how to set the video fill mode using the objectFit attribute.


```

```TypeScript
### Example 5: Handling Errors with onError

This example uses an invalid video resource path to demonstrate how the Video component can obtain error codes through the [onError](#onerror) event, available since API version 20.


```

```TypeScript
### Example 6: Dynamically Setting Attributes and Methods of the Video Component Using attributeModifier

The following example demonstrates how to use attributeModifier to dynamically set the enableAnalyzer and analyzerConfig attributes and the onStart, onPause, onFinish, onError, onStop, onPrepared, onSeeking, onSeeked, onUpdate, and onFullscreenChange methods of the Video component.


```

```TypeScript
### Example 7: Using VideoControllerAsync

This example demonstrates the usage of the [start](#start-1), [pause](#pause-1), [stop](#stop-1), and [reset](#reset) APIs of VideoControllerAsync, and obtains the command execution status through promise-based asynchronous callbacks.

Since API version 26.0.0, the VideoControllerAsync controller and the [start](#start-1), [pause](#pause-1), [stop](#stop-1), and [reset](#reset) APIs are added.
```
