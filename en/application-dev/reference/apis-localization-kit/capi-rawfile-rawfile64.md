# RawFile64

<!--Kit: Localization Kit-->
<!--Subsystem: Global-->
<!--Owner: @liule_123-->
<!--Designer: @buda_wy-->
<!--Tester: @lpw_work-->
<!--Adviser: @ningningW-->
<!-- md-trans-meta sourceCommit=cc8fe8b0f1b2859346994908b98ebf9b3df1ff9d translatedAt=2026-07-17T00:21:15.843Z pushedAt=2026-07-17T09:12:54.429Z -->

```c
typedef struct RawFile64 RawFile64
```

## Overview

`RawFile64` represents an opened rawfile object, which is used for accessing large files of 2 GB and above. It is obtained through [OH_ResourceManager_OpenRawFile64](capi-raw-file-manager-h.md#oh_resourcemanager_openrawfile64), and must be closed and released through [OH_ResourceManager_CloseRawFile64](capi-raw-file-h.md#oh_resourcemanager_closerawfile64) after use.

**Since**: 11

**Related module:** [rawfile](capi-rawfile.md)

**Header file**: [raw_file.h](capi-raw-file-h.md)