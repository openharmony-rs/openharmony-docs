# OH_AVPlaybackStrategy
<!--Kit: Media Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @chennotfound-->
<!--Designer: @chennotfound-->
<!--Tester: @xchaosioda-->
<!--Adviser: @w_Machine_cc-->
<!-- md-trans-meta sourceCommit=cc48f97eabfc91efede35183124197c3434b661e translatedAt=2026-11-09T06:26:43.016Z pushedAt=2026-11-09T08:36:44.728Z nl=1 -->

```c
typedef struct OH_AVPlaybackStrategy OH_AVPlaybackStrategy;
```

## Overview

Defines the struct type of the audio and video playback strategy, which is used to configure the strategy parameters of the player when playing audio and video content. Use scenarios: music player apps, online video playback, live streaming, and other scenarios that require fine-grained control over playback behavior. If this strategy parameter is not set, the player uses the default playback strategy.

**Since**: 23

**Related module**: [AVPlayer](capi-avplayer.md)

**Header file**: [avplayer_base.h](capi-avplayer-base-h.md)

