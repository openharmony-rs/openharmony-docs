# AVPlayerCallback
<!--Kit: Media Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @chennotfound-->
<!--Designer: @dongyu_dy-->
<!--Tester: @xchaosioda-->
<!--Adviser: @w_Machine_cc-->
<!-- md-trans-meta sourceCommit=09a82d06cdbfe294e7bdee52844240f730ae4276 translatedAt=2026-09-15T16:01:01.304Z pushedAt=2026-09-22T01:34:18.774Z -->

```c
typedef struct AVPlayerCallback {...} AVPlayerCallback
```

## Overview

**AVPlayerCallback** is a callback management struct of the AVPlayer. It contains the **OH_AVPlayerOnInfo** and **OH_AVPlayerOnError** callback function pointers. To ensure the normal running of OH_AVPlayer, you must register the instance of this struct with the OH_AVPlayer instance and process the information reported by the callback functions. By registering these callbacks, you can monitor the playback state of the AVPlayer in real time, obtain playback process information (such as the buffering progress and playback position), and handle error events promptly. This struct is applicable to scenarios where fine-grained control and monitoring of the playback process are required, such as music players, video players, and live streaming apps that need to monitor the playback state and handle exceptions in real time.

**Since**: 11

**Deprecated version**: 12

**Substitute:** [OH_AVPlayerOnInfoCallback](capi-avplayer-base-h.md#oh_avplayeroninfocallback) or [OH_AVPlayerOnErrorCallback](capi-avplayer-base-h.md#oh_avplayeronerrorcallback).

**Related module**: [AVPlayer](capi-avplayer.md)

**Header file**: [avplayer_base.h](capi-avplayer-base-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| [OH_AVPlayerOnInfo](capi-avplayer-base-h.md#oh_avplayeroninfo) onInfo<sup>(deprecated)</sup> | Monitors the AVPlayer process information. This callback needs to be registered with the AVPlayer instance. After this callback is set, it will be triggered when the player generates a message. In this way, you can obtain the playback information in real time. If this callback is not set, it will not be triggered. You are advised to register this callback in scenarios where the playback state needs to be monitored in real time and information such as the buffering progress or playback position needs to be obtained. If this callback is not registered, your app will not receive notifications about state changes during playback.<br>**Since:** 11<br>**Deprecated version:** 12<br>**Substitute:** [OH_AVPlayerOnInfoCallback](capi-avplayer-base-h.md#oh_avplayeroninfocallback) |
| [OH_AVPlayerOnError](capi-avplayer-base-h.md#oh_avplayeronerror) onError<sup>(deprecated)</sup> | Monitors AVPlayer operation errors. This callback needs to be registered with the AVPlayer instance. After this callback is set, it will be triggered when an error occurs during player operations. In this way, you can obtain the error information for processing. If this callback is not set, it will not be triggered. You are advised to register this callback in scenarios where playback errors need to be captured and handled. If this callback is not registered, your app will not receive notifications about error events during playback.<br>**Since:** 11<br>**Deprecated version:** 12<br>**Substitute:** [OH_AVPlayerOnErrorCallback](capi-avplayer-base-h.md#oh_avplayeronerrorcallback) |
