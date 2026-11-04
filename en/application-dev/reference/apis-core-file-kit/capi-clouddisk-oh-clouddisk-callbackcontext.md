# OH_CloudDisk_CallbackContext
<!--Kit: Core File Kit-->
<!--Subsystem: FileManagement-->
<!--Owner: @oh_create_jiawei-->
<!--Designer: @oh_create_jiawei-->
<!--Tester: @liuhonggang123-->
<!--Adviser: @jinqiuheng-->
<!-- md-trans-meta sourceCommit=129ae9ac672af572fa2f5d2a59eb096f01eee9a0 translatedAt=2026-11-03T03:43:02.733Z pushedAt=2026-11-04T03:11:33.436Z nl=1 -->

```c
typedef union OH_CloudDisk_CallbackContext {...} OH_CloudDisk_CallbackContext
```

## Overview

Union for callback request context information.

**Since:** 26.0.1

**Related module:** [CloudDisk](capi-clouddisk.md)

**Header file:** [oh_cloud_disk_manager.h](capi-oh-cloud-disk-manager-h.md)

## Summary

### Member Variables

| Name | Description |
| -- | -- |
| [OH_CloudDisk_FetchDataRequest](capi-clouddisk-oh-clouddisk-fetchdatarequest.md) *fetchData | Request to fetch data. Takes effect when callbackType is OH_CLOUD_DISK_CALLBACK_TYPE_FETCH_DATA.<br>**Since:** 26.0.1 |
| [CloudDisk_PathInfo](capi-clouddisk-clouddisk-pathinfo.md) *cancelFetchData | Request to cancel fetching data. Takes effect when callbackType is OH_CLOUD_DISK_CALLBACK_TYPE_CANCEL_FETCH_DATA.<br>**Since:** 26.0.1 |
| [OH_CloudDisk_DehydrateInfo](capi-clouddisk-oh-clouddisk-dehydrateinfo.md) *dehydrateData | Dehydrate authorization request. Takes effect when callbackType is OH_CLOUD_DISK_CALLBACK_TYPE_DEHYDRATE.<br>**Since:** 26.0.1 |
