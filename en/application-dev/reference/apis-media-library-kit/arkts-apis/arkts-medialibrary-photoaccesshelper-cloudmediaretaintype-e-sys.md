# CloudMediaRetainType (System API)

```TypeScript
enum CloudMediaRetainType
```

Enumerates the modes used for deleting cloud media assets.

**Since:** 14

<!--Device-photoAccessHelper-enum CloudMediaRetainType--><!--Device-photoAccessHelper-enum CloudMediaRetainType-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

## HDC_RETAIN_FORCE

```TypeScript
HDC_RETAIN_FORCE = 1
```

Deletes the local metadata and thumbnail of the original files from the home storage device.

**Since:** 22

<!--Device-CloudMediaRetainType-HDC_RETAIN_FORCE = 1--><!--Device-CloudMediaRetainType-HDC_RETAIN_FORCE = 1-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

## RETAIN_FORCE

```TypeScript
RETAIN_FORCE = 0
```

Deletes the local metadata and thumbnail of the original files from the cloud.

**Since:** 14

<!--Device-CloudMediaRetainType-RETAIN_FORCE = 0--><!--Device-CloudMediaRetainType-RETAIN_FORCE = 0-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

## SHARE_RETAIN_FORCE

```TypeScript
SHARE_RETAIN_FORCE = 2
```

Deletes the local metadata and thumbnails of shared files and shared albums from the cloud.

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-CloudMediaRetainType-SHARE_RETAIN_FORCE = 2--><!--Device-CloudMediaRetainType-SHARE_RETAIN_FORCE = 2-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.
