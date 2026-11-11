# SoundPool (Sound Pool) (System API)
<!--Kit: Media Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @hanzhengshi-->
<!--Designer: @chris2981-->
<!--Tester: @xchaosioda-->
<!--Adviser: @w_Machine_cc-->
<!-- md-trans-meta sourceCommit=febcfb5be499533fb9012106cbb3934ae1688a19 translatedAt=2026-11-10T08:41:48.994Z pushedAt=2026-11-10T10:48:58.327Z nl=1 -->

The module provides APIs for loading, unloading, playing, and stopping playing system sounds, setting the volume, and setting the number of loops.

Before using these APIs, you must call [media.createSoundPool](arkts-apis-media-f.md#mediacreatesoundpool10) to create a SoundPool instance.

> **NOTE**
>
> - The initial APIs of this module are supported since API version 10. Newly added APIs will be marked with a superscript to indicate their earliest API version.
> - This topic describes only system APIs provided by the module. For details about its public APIs, see [SoundPool (Sound Pool)](js-apis-inner-multimedia-soundPool.md).

## PlayParameters

Describes the playback parameters of the sound pool.

**System capability**: SystemCapability.Multimedia.Media.SoundPool

| Name           | Type                     |        Read-Only   | Optional| Description                                                        |
| --------------- | ----------------------|------------------ | ---- | ------------------------------------------------------------ |
| parallelPlayFlag | boolean | No|Yes | Whether to play in parallel with other audio being played.<br>true: does not preempt the audio focus and plays in parallel with other audio being played; false: preempts the focus and interrupts other audio being played. Default value: false.<br>**System API:** This is a system API. |
