# Module Description
<!--Kit: Audio Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @boxwall-->
<!--Designer: @magekkkk-->
<!--Tester: @Filger-->
<!--Adviser: @w_Machine_cc-->
<!-- md-trans-meta sourceCommit=1961de06e85063963f633ec54a8a4baaf5cb7dc8 translatedAt=2026-07-21T03:49:33.921Z pushedAt=2026-07-21T07:02:27.048Z -->

The module provides basic audio control capabilities, including volume adjustment, device management, data capture, and rendering.

This module provides the following common audio features:

- [AudioManager](arkts-apis-audio-AudioManager.md): audio manager.
- [AudioDeviceEnhanceManager](arkts-apis-audio-AudioDeviceEnhanceManager.md): audio device enhancement manager.
- [AudioRenderer](arkts-apis-audio-AudioRenderer.md): audio renderer, used to play Pulse Code Modulation (PCM) audio data.
- [AudioCapturer](arkts-apis-audio-AudioCapturer.md): audio capturer, used to record PCM audio data.

> **NOTE**
>
> The initial APIs of this module are supported since API version 7. Newly added APIs will be marked with a superscript to indicate their earliest API version.

## Modules to Import

```ts
import { audio } from '@kit.AudioKit';
```