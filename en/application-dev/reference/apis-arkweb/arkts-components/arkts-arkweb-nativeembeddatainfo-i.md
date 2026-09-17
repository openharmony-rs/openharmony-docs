# NativeEmbedDataInfo

Provides detailed information about the changes of the same-layer tag lifecycle, including the status and tag information. It is suitable for scenarios where monitoring same-layer element lifecycle is required, improving rendering state management accuracy and user experience.

@interface NativeEmbedDataInfo [since 11 - 11]

**Since:** 11

**System capability:** SystemCapability.Web.Webview.Core

## embedId

```TypeScript
embedId?: string
```

Unique ID of the same-layer tag.

**Type:** string

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core

## info

```TypeScript
info?: NativeEmbedInfo
```

Detailed information about the same-layer tag.

**Type:** [NativeEmbedInfo](arkts-arkweb-nativeembedinfo-i.md)

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core

## status

```TypeScript
status?: NativeEmbedStatus
```

Lifecycle status of the same-layer tag.

**Type:** [NativeEmbedStatus](arkts-arkweb-nativeembedstatus-e.md)

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core

## surfaceId

```TypeScript
surfaceId?: string
```

SurfaceId of the NativeImage.

**Type:** string

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core
