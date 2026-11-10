# AVPlayerCallback
<!--Kit: Media Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @chennotfound-->
<!--Designer: @chennotfound-->
<!--Tester: @xchaosioda-->
<!--Adviser: @w_Machine_cc-->
<!-- md-trans-meta sourceCommit=2d56846da3109c6542705ceefa4aed0cf271c3b1 translatedAt=2026-11-10T08:37:33.629Z pushedAt=2026-11-10T10:44:19.543Z nl=1 -->

```c
typedef struct AVPlayerCallback {...} AVPlayerCallback
```

## Overview

**AVPlayerCallback** is a callback management struct of AVPlayer, which contains the callback function pointers for playback process information **OH_AVPlayerOnInfo** and error information **OH_AVPlayerOnError**. An application needs to register this instance struct with the OH_AVPlayer instance and process the information reported by the callbacks to ensure the normal operation of AVPlayer. By registering these callbacks, developers can monitor the playback status of AVPlayer in real time, obtain playback process information (such as buffering progress and playback position) and error events, and respond to and handle various events during the playback process in a timely manner. This is suitable for scenarios that require fine-grained control and monitoring of the playback process.

**Since**: 11

**Deprecated from**: 12

**Substitute:** [OH_AVPlayerOnInfoCallback](capi-avplayer-base-h.md#oh_avplayeroninfocallback) or [OH_AVPlayerOnErrorCallback](capi-avplayer-base-h.md#oh_avplayeronerrorcallback).

**Related module**: [AVPlayer](capi-avplayer.md)

**Header file**: [avplayer_base.h](capi-avplayer-base-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| OH_AVPlayerOnInfo onInfo | Monitors the AVPlayer process information. This callback must be registered with the AVPlayer instance before use. For details, see [OH_AVPlayerOnInfo](capi-avplayer-base-h.md#oh_avplayeroninfo).<br>**Since:** 11<br>**Deprecated:** 12<br>**Alternative API:** [OH_AVPlayerOnInfoCallback](capi-avplayer-base-h.md#oh_avplayeroninfocallback) |
| OH_AVPlayerOnError onError | Monitors AVPlayer operation errors. This callback must be registered with the AVPlayer instance before use. The callback signature is OH_AVPlayerOnError. For details about the callback parameters, see [OH_AVPlayerOnError](capi-avplayer-base-h.md#oh_avplayeronerror).<br>**Since:** 11<br>**Deprecated:** 12<br>**Alternative API:** [OH_AVPlayerOnErrorCallback](capi-avplayer-base-h.md#oh_avplayeronerrorcallback) |
