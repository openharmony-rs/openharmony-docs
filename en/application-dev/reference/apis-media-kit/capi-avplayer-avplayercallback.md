# AVPlayerCallback
<!--Kit: Media Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @chennotfound-->
<!--Designer: @dongyu_dy-->
<!--Tester: @xchaosioda-->
<!--Adviser: @w_Machine_cc-->
<!-- md-trans-meta sourceCommit=320793da1b58e6a20565f5e582fc3e50f69572ee translatedAt=2026-06-22T03:37:07.702Z pushedAt=2026-06-22T09:23:26.573Z -->

```c
typedef struct AVPlayerCallback {...} AVPlayerCallback
```

## Overview

The struct contains the set of the **OH_AVPlayerOnInfo** and **OH_AVPlayerOnError** callback function pointers. To ensure the normal running of OH_AVPlayer, you must register the instance of this struct with the OH_AVPlayer instance and process the information reported by the callback functions.

**Since**: 11

**Deprecated from**: 12

**Substitute**: [OH_AVPlayerOnInfoCallback](capi-avplayer-base-h.md#oh_avplayeroninfocallback) and [OH_AVPlayerOnErrorCallback](capi-avplayer-base-h.md#oh_avplayeronerrorcallback)

**Related module**: [AVPlayer](capi-avplayer.md)

**Header file**: [avplayer_base.h](capi-avplayer-base-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| OH_AVPlayerOnInfo onInfo | Callback for AVPlayer process information. For details about the available options, see [OH_AVPlayerOnInfo](capi-avplayer-base-h.md#oh_avplayeroninfo).<br>**Since**: 11<br>**Deprecated from**: 12<br>**Substitute**: [OH_AVPlayerOnInfoCallback](capi-avplayer-base-h.md#oh_avplayeroninfocallback)|
| OH_AVPlayerOnError onError | Callback for AVPlayer error information. For details about the available options, see [OH_AVPlayerOnError](capi-avplayer-base-h.md#oh_avplayeronerror).<br>**Since**: 11<br>**Deprecated from**: 12<br>**Substitute**: [OH_AVPlayerOnErrorCallback](capi-avplayer-base-h.md#oh_avplayeronerrorcallback)|