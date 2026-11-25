# RawFile

<!--Kit: Localization Kit-->
<!--Subsystem: Global-->
<!--Owner: @liule_123-->
<!--Designer: @buda_wy-->
<!--Tester: @lpw_work-->
<!--Adviser: @ningningW-->
<!-- md-trans-meta sourceCommit=d1ed4ce8d034cfba750330bf06dcd3a9995f70ce translatedAt=2026-11-04T04:05:15.992Z pushedAt=2026-11-04T10:13:14.898Z nl=1 -->

```c
typedef struct RawFile RawFile
```

## Overview

RawFile represents an opened rawfile object. It is obtained through the [OH_ResourceManager_OpenRawFile](capi-raw-file-manager-h.md#oh_resourcemanager_openrawfile) function, and must be closed and released by calling [OH_ResourceManager_CloseRawFile](capi-raw-file-h.md#oh_resourcemanager_closerawfile) after use.

**Since**: 8

**Related module**: [rawfile](capi-rawfile.md)

**Header file**: [raw_file.h](capi-raw-file-h.md)

