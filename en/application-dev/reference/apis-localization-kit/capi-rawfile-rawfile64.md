# RawFile64

<!--Kit: Localization Kit-->
<!--Subsystem: Global-->
<!--Owner: @liule_123-->
<!--Designer: @buda_wy-->
<!--Tester: @lpw_work-->
<!--Adviser: @ningningW-->
<!-- md-trans-meta sourceCommit=d1ed4ce8d034cfba750330bf06dcd3a9995f70ce translatedAt=2026-11-04T04:05:54.592Z pushedAt=2026-11-04T10:13:14.900Z nl=1 -->

```c
typedef struct RawFile64 RawFile64
```

## Overview

RawFile64 represents an opened rawfile object, used to access large files of 2 GB or larger. It is obtained through the [OH_ResourceManager_OpenRawFile64](capi-raw-file-manager-h.md#oh_resourcemanager_openrawfile64) function, and must be closed and released by calling [OH_ResourceManager_CloseRawFile64](capi-raw-file-h.md#oh_resourcemanager_closerawfile64) after use.

**Since**: 11

**Related module:** [rawfile](capi-rawfile.md)

**Header file**: [raw_file.h](capi-raw-file-h.md)

