# OH_CloudDisk_CallbackResponse
<!--Kit: Core File Kit-->
<!--Subsystem: FileManagement-->
<!--Owner: @oh_create_jiawei-->
<!--Designer: @oh_create_jiawei-->
<!--Tester: @liuhonggang123-->
<!--Adviser: @jinqiuheng-->
<!-- md-trans-meta sourceCommit=4165f338bbfe7f5ad0b3bd882976a1f16b4d44a0 translatedAt=2026-11-04T03:40:18.436Z pushedAt=2026-11-04T10:12:33.403Z nl=1 -->

```c
typedef union OH_CloudDisk_CallbackResponse {...} OH_CloudDisk_CallbackResponse
```

## Overview

Union of callback response information.

**Since:** 26.0.1

**Related module**: [CloudDisk](capi-clouddisk.md)

**Header File:** [oh_cloud_disk_manager.h](capi-oh-cloud-disk-manager-h.md)

## Summary

### Member Variables

| Name | Description |
| -- | -- |
| [OH_CloudDisk_FetchData](capi-clouddisk-oh-clouddisk-fetchdata.md) *fetchData | Response for fetching data. Takes effect when callbackType is OH_CLOUD_DISK_CALLBACK_TYPE_FETCH_DATA.<br>**Since:** 26.0.1 |
