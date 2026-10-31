# @ohos.graphics.hdrCapability (HDR Capability)

<!--Kit: ArkGraphics 2D-->
<!--Subsystem: Graphics-->
<!--Owner: @xiaojianfeng_jeffery-->
<!--Designer: @njuptkid-->
<!--Tester: @zhaoxiaoguang2-->
<!--Adviser: @ge-yafang-->
<!-- md-trans-meta sourceCommit=9a673d444fec536578066af1baf013d52353a6c3 translatedAt=2026-08-24T09:23:47.992Z pushedAt=2026-08-31T12:05:04.201Z -->

This module provides the enums related to HDR (High Dynamic Range) capabilities. HDR technology can significantly expand the dynamic range and color expressiveness of images. It is applicable to scenarios such as video playback and image display, and can solve the problems of overexposed highlights and lost shadow details in high-contrast scenes with traditional SDR, delivering a more realistic and richer visual experience.

> **NOTE**
>
> The initial APIs of this module are supported since API version 11. Newly added APIs will be marked with a superscript to indicate their earliest API version.

## Modules to Import

```ts
import { hdrCapability } from '@kit.ArkGraphics2D';
```

## HDRFormat

Enumerates the HDR formats.

**System capability**: SystemCapability.Graphic.Graphic2D.ColorManager.Core

| Name                        | Value    | Description                   |
| --------------------------- | ------ | ----------------------- |
| NONE                         | 0      | Unsupported HDR type.<br>**Atomic service API**: This API can be used in atomic services since API version 12.|
| VIDEO_HLG                    | 1      | Videos in Hybrid Log-Gamma (HLG) format.<br>**Atomic service API**: This API can be used in atomic services since API version 12.|
| VIDEO_HDR10                  | 2      | Videos in HDR10 format.<br>**Atomic service API**: This API can be used in atomic services since API version 12.|
| VIDEO_HDR_VIVID              | 3      | Videos in HDR_VIVID format.<br>**Atomic service API**: This API can be used in atomic services since API version 12.|
| IMAGE_HDR_VIVID_DUAL         | 4      | Images in HDR_VIVID format, stored in dual JPEG format.<br>**Atomic service API**: This API can be used in atomic services since API version 12.|
| IMAGE_HDR_VIVID_SINGLE       | 5      | Images in HDR_VIVID format, stored in single HEIF format.<br>**Atomic service API**: This API can be used in atomic services since API version 12.|
| IMAGE_HDR_ISO_DUAL           | 6      | Images in HDR_ISO format, stored in dual JPEG format.<br>**Atomic service API**: This API can be used in atomic services since API version 12.|
| IMAGE_HDR_ISO_SINGLE         | 7      | Images in HDR_ISO format, stored in single HEIF format.<br>**Atomic service API**: This API can be used in atomic services since API version 12.|
| VIDEO_AIHDR<sup>24+</sup>     | 8      | Videos in AIHDR format.<br>**Atomic service API**: This API can be used in atomic services since API version 24.<br> **Model restriction**: This API can be used only in the stage model.|