# RawDir

<!--Kit: Localization Kit-->
<!--Subsystem: Global-->
<!--Owner: @liule_123-->
<!--Designer: @buda_wy-->
<!--Tester: @lpw_work-->
<!--Adviser: @ningningW-->
<!-- md-trans-meta sourceCommit=cc8fe8b0f1b2859346994908b98ebf9b3df1ff9d translatedAt=2026-07-17T00:20:54.978Z pushedAt=2026-07-17T09:13:16.041Z -->

```c
typedef struct RawDir RawDir
```

## Overview

`RawDir` represents an opened rawfile directory object, which can be used to traverse the directory and files within it. It is obtained through [OH_ResourceManager_OpenRawDir](capi-raw-file-manager-h.md#oh_resourcemanager_openrawdir), and must be closed and released through [OH_ResourceManager_CloseRawDir](capi-raw-dir-h.md#oh_resourcemanager_closerawdir) after use.

**Since**: 8

**Related module**: [rawfile](capi-rawfile.md)

**Header file**: [raw_dir.h](capi-raw-dir-h.md)