# CloudMediaDownloadType (System API)

```TypeScript
enum CloudMediaDownloadType
```

Enumerates the types of download tasks.

**Since:** 14

<!--Device-photoAccessHelper-enum CloudMediaDownloadType--><!--Device-photoAccessHelper-enum CloudMediaDownloadType-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

## DOWNLOAD_FORCE

```TypeScript
DOWNLOAD_FORCE = 0
```

High-priority download, without the need for the device to switch to screen-off charging mode.

**Since:** 14

<!--Device-CloudMediaDownloadType-DOWNLOAD_FORCE = 0--><!--Device-CloudMediaDownloadType-DOWNLOAD_FORCE = 0-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

## DOWNLOAD_GENTLE

```TypeScript
DOWNLOAD_GENTLE = 1
```

Low-priority download, demanding that device be in screen-off charging mode.

**Since:** 14

<!--Device-CloudMediaDownloadType-DOWNLOAD_GENTLE = 1--><!--Device-CloudMediaDownloadType-DOWNLOAD_GENTLE = 1-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.
