# DeliveryMode

枚举，资源分发模式。

该模式适用于分段式拍照或分段式视频。如果当前设备不具备分段式能力，则以下三种分发模式无区别，直接返回请求的图片或视频资源。请求的结果通过[onDataPrepared](arkts-medialibrary-photoaccesshelper-mediaassetdatahandler-i.md#ondataprepared)回调返回。

**起始版本：** 11

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## FAST_MODE

```TypeScript
FAST_MODE = 0
```

快速模式。

针对分段式拍照或视频场景，若当前存在高质量图或视频，则立即返回高质量图或视频的请求结果回调；若当前存在低质量图或视频，则立即返回低质量图或视频的请求结果回调。

**起始版本：** 11

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## HIGH_QUALITY_MODE

```TypeScript
HIGH_QUALITY_MODE = 1
```

高质量模式。

针对分段式拍照或视频场景，若当前存在高质量图或视频，则立即返回高质量图或视频的请求结果回调；若当前存在低质量图或视频，则申请高质量图或视频的生成任务，待高质量图或视频生成后，返回高质量图或视频的请求结果回调。

**起始版本：** 11

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## BALANCE_MODE

```TypeScript
BALANCE_MODE = 2
```

均衡模式。

- 针对分段式拍照场景，若当前存在高质量图，则立即返回高质量图的请求结果回调；若当前存在低质量图，则立即返回低质量图的请求  
结果回调，并申请高质量图生成任务，待高质量图生成后，再次返回高质量图的请求结果回调。  
- 针对分段式视频场景，若当前存在高质量视频，则立即返回高质量视频的请求结果回调；若当前存在低质量视频，  
则立即返回低质量视频的请求结果回调。

**起始版本：** 11

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core
