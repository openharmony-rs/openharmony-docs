# NotifyChangeType

```TypeScript
enum NotifyChangeType
```

Enumerates the types of changes that trigger the media asset or album change events.

**Since:** 20

<!--Device-photoAccessHelper-enum NotifyChangeType--><!--Device-photoAccessHelper-enum NotifyChangeType-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## NOTIFY_CHANGE_ADD_ANALYSIS

```TypeScript
NOTIFY_CHANGE_ADD_ANALYSIS = 4
```

A media asset (image or video) is created in the smart analysis album.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

<!--Device-NotifyChangeType-NOTIFY_CHANGE_ADD_ANALYSIS = 4--><!--Device-NotifyChangeType-NOTIFY_CHANGE_ADD_ANALYSIS = 4-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

## NOTIFY_CHANGE_REMOVE_ANALYSIS

```TypeScript
NOTIFY_CHANGE_REMOVE_ANALYSIS = 5
```

A media asset (image or video) is deleted from the smart analysis album.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

<!--Device-NotifyChangeType-NOTIFY_CHANGE_REMOVE_ANALYSIS = 5--><!--Device-NotifyChangeType-NOTIFY_CHANGE_REMOVE_ANALYSIS = 5-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

## NOTIFY_CHANGE_YUV_READY

```TypeScript
NOTIFY_CHANGE_YUV_READY = 3
```

A high-quality image is ready in deferred photo delivery scenarios.

Image quality metrics such as sharpness and color accuracy can be checked in the [OnDataPrepared](arkts-medialibrary-photoaccesshelper-quickimagedatahandler-i.md#ondataprepared) callback.

**Since:** 23

<!--Device-NotifyChangeType-NOTIFY_CHANGE_YUV_READY = 3--><!--Device-NotifyChangeType-NOTIFY_CHANGE_YUV_READY = 3-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.
