# BlanklessLoadingParam

Loading parameters of the White-Screen-Free Loading frame interpolation scheme.

**Since:** 23

**System capability:** SystemCapability.Web.Webview.Core

## Modules to Import

```TypeScript
import { webview } from '@kit.ArkWeb';
```

## callback

```TypeScript
callback?: Callback<BlanklessFrameInterpolationInfo>
```

Callback invoked after frame interpolation succeeds, fails, or is removed.

This takes effect only when **enable** is **true**. This parameter is optional. If not set, no operation is performed.

**Type:** [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[BlanklessFrameInterpolationInfo](arkts-arkweb-webview-blanklessframeinterpolationinfo-i.md)&gt;

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Web.Webview.Core

## duration

```TypeScript
duration?: number
```

Duration of frame interpolation.

The value range is the union of **[200, 2000]** and **{0}**, where **0** indicates that the duration is not specified and the system automatically sets a proper duration.

Unit: ms.

**Type:** number

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Web.Webview.Core

## enable

```TypeScript
enable: boolean
```

Whether to enable the white-screen-free loading frame interpolation scheme.

The value **true** means enabled, and **false** means disabled.

**Type:** boolean

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Web.Webview.Core

## expirationTime

```TypeScript
expirationTime?: number
```

Expiration time of the historical frame, in UTC time.

**T** indicates the current UTC time. If the expiration time is 30 days, the value is 2592000000 ms. The value range is the union of **(T, T + 2592000000]** and **{0}**. **0** indicates that the expiration time is not specified and the default expiration time (7 days) is used.

Unit: ms.

**Type:** number

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Web.Webview.Core
