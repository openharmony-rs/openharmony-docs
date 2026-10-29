# Module Description
<!--Kit: Audio Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @boxwall-->
<!--Designer: @magekkkk-->
<!--Tester: @Filger-->
<!--Adviser: @w_Machine_cc-->
<!-- md-trans-meta sourceCommit=138f7dcec9e99067f11a5ba1afa58271363a7ef2 translatedAt=2026-10-08T12:13:50.807Z pushedAt=2026-10-12T10:49:36.181Z -->

The module provides basic audio control capabilities, including volume adjustment, device management, data capture, and rendering.

This module provides the following common audio-related functions:

- [AudioManager](arkts-apis-audio-AudioManager.md): audio manager.
- [AudioDeviceEnhanceManager](arkts-apis-audio-AudioDeviceEnhanceManager.md): audio device enhancement manager.
- [AudioRenderer](arkts-apis-audio-AudioRenderer.md): audio renderer, which is used to play Pulse Code Modulation (PCM) audio data.
- [AudioCapturer](arkts-apis-audio-AudioCapturer.md): audio capturer, which is used to record PCM audio data.

> **NOTE**
>
> The initial APIs of this module are supported since API version 7. Newly added APIs will be marked with a superscript to indicate their earliest API version.

## Modules to Import

```ts
import { audio } from '@kit.AudioKit';
```