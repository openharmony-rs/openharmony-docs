# Constants
<!--Kit: Audio Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @songshenke-->
<!--Designer: @zhanganxiang1-->
<!--Tester: @Filger-->
<!--Adviser: @w_Machine_cc-->
<!-- md-trans-meta sourceCommit=138f7dcec9e99067f11a5ba1afa58271363a7ef2 translatedAt=2026-10-08T12:08:46.178Z pushedAt=2026-10-12T08:57:14.425Z -->

> **NOTE**
>
> The initial APIs of this module are supported since API version 7. Newly added APIs will be marked with a superscript to indicate their earliest API version.

| Name                                   | Type     | Read-Only| Description              |
| --------------------------------------- | ----------|---| ------------------ |
| DEFAULT_VOLUME_GROUP_ID<sup>9+</sup>    | number    | Yes | Default volume group ID.<br> **System capability:** SystemCapability.Multimedia.Audio.Volume       |
| DEFAULT_INTERRUPT_GROUP_ID<sup>9+</sup> | number    | Yes | Default audio interrupt group ID.<br> **System capability:** SystemCapability.Multimedia.Audio.Interrupt       |

**Example**

```ts
import { audio } from '@kit.AudioKit';

const defaultVolumeGroupId = audio.DEFAULT_VOLUME_GROUP_ID;
const defaultInterruptGroupId = audio.DEFAULT_INTERRUPT_GROUP_ID;
```
