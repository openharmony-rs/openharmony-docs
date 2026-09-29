# AVCastCategory

```TypeScript
enum AVCastCategory
```

cast category indicating different playback scenes

**Since:** 10

<!--Device-avSession-enum AVCastCategory--><!--Device-avSession-enum AVCastCategory-End-->

**System capability:** SystemCapability.Multimedia.AVSession.AVCast

## CATEGORY_LOCAL

```TypeScript
CATEGORY_LOCAL = 0
```

The default cast type "local", media can be routed on the same device, including internal speakers or audio jack on the device itself, A2DP devices.

**Since:** 10

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-AVCastCategory-CATEGORY_LOCAL = 0--><!--Device-AVCastCategory-CATEGORY_LOCAL = 0-End-->

**System capability:** SystemCapability.Multimedia.AVSession.AVCast

## CATEGORY_REMOTE

```TypeScript
CATEGORY_REMOTE = 1
```

The remote category indicating the media is presenting on a remote device, the application needs to get an AVCastController to control remote playback.

**Since:** 10

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-AVCastCategory-CATEGORY_REMOTE = 1--><!--Device-AVCastCategory-CATEGORY_REMOTE = 1-End-->

**System capability:** SystemCapability.Multimedia.AVSession.AVCast
