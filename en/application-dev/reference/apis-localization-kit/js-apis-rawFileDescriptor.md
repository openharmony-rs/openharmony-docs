# RawFileDescriptor

<!--Kit: Localization Kit-->
<!--Subsystem: Global-->
<!--Owner: @liule_123-->
<!--Designer: @buda_wy-->
<!--Tester: @lpw_work-->
<!--Adviser: @ningningW-->
<!-- md-trans-meta sourceCommit=a8446c9be4dbeea364560754c05cf5bc58bb15cf translatedAt=2026-11-03T13:45:05.303Z pushedAt=2026-11-04T08:47:59.742Z nl=1 -->

This module provides the file descriptor information of the rawfile in the HAP package, including the file descriptor, start offset, and file length of the rawfile.

> **NOTE**
>
> The initial APIs of this module are supported since API version 8. Newly added APIs will be marked with a superscript to indicate their earliest API version.

## Import a module.

```js
import { resourceManager } from '@kit.LocalizationKit'
```

## RawFileDescriptor

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Global.ResourceManager

| Name    | Type   | Read-Only  | Optional | Description          |
| ------ | ------  | ---- | ---- | ------------------ |
| fd     | number  | No   | No| Pointer to the file descriptor.|
| offset | number  | No    | No | Start offset, which indicates the start position of the rawfile in the HAP package. The unit is Byte.  |
| length | number  | No    | No | File length, which indicates the size of the rawfile. The unit is Byte.       |