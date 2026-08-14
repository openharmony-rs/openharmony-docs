# RawFileDescriptor

<!--Kit: Localization Kit-->
<!--Subsystem: Global-->
<!--Owner: @liule_123-->
<!--Designer: @buda_wy-->
<!--Tester: @lpw_work-->
<!--Adviser: @ningningW-->
<!-- md-trans-meta sourceCommit=cc8fe8b0f1b2859346994908b98ebf9b3df1ff9d translatedAt=2026-07-17T00:24:13.233Z pushedAt=2026-07-17T03:55:04.929Z -->

This module provides file descriptor information of the HAP where the `rawfile` file is located, including the file descriptor, start offset, and file length.

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
| fd     | number  | No   | No| File descriptor.|
| offset | number  | No    | No | Start offset, indicating the start position of the `rawfile` file in the HAP. The unit is bytes.  |
| length | number  | No    | No | File length, indicating the size of the `rawfile` file. The unit is bytes.       |