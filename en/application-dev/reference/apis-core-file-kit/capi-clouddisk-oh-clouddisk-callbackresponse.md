# OH_CloudDisk_CallbackResponse
<!--Kit: Core File Kit-->
<!--Subsystem: FileManagement-->
<!--Owner: @oh_create_jiawei-->
<!--Designer: @oh_create_jiawei-->
<!--Tester: @liuhonggang123-->
<!--Adviser: @jinqiuheng-->
<!-- md-trans-meta sourceCommit=129ae9ac672af572fa2f5d2a59eb096f01eee9a0 translatedAt=2026-11-03T03:43:30.422Z pushedAt=2026-11-04T03:11:33.441Z nl=1 -->

```c
typedef union OH_CloudDisk_CallbackResponse {...} OH_CloudDisk_CallbackResponse
```

## Overview

Union for callback response information.

**Since:** 26.0.1

**Related module:** [CloudDisk](capi-clouddisk.md)

**Header file:** [oh_cloud_disk_manager.h](capi-oh-cloud-disk-manager-h.md)

## Summary

### Member Variables

| Name | Description |
| -- | -- |
| [OH_CloudDisk_FetchData](capi-clouddisk-oh-clouddisk-fetchdata.md) *fetchData | Response for fetching data. Takes effect when callbackType is OH_CLOUD_DISK_CALLBACK_TYPE_FETCH_DATA.<br>**Since:** 26.0.1 |
