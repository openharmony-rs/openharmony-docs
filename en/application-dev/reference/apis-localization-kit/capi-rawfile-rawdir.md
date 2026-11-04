# RawDir

<!--Kit: Localization Kit-->
<!--Subsystem: Global-->
<!--Owner: @liule_123-->
<!--Designer: @buda_wy-->
<!--Tester: @lpw_work-->
<!--Adviser: @ningningW-->
<!-- md-trans-meta sourceCommit=d1ed4ce8d034cfba750330bf06dcd3a9995f70ce translatedAt=2026-11-03T13:30:20.569Z pushedAt=2026-11-04T08:47:59.707Z nl=1 -->

```c
typedef struct RawDir RawDir
```

## Overview

RawDir represents an opened rawfile directory object, which can be used to traverse the directory and the files in it. It is obtained through [OH_ResourceManager_OpenRawDir](capi-raw-file-manager-h.md#oh_resourcemanager_openrawdir), and must be closed and released by calling [OH_ResourceManager_CloseRawDir](capi-raw-dir-h.md#oh_resourcemanager_closerawdir) after use.

**Since**: 8

**Related module**: [rawfile](capi-rawfile.md)

**Header file**: [raw_dir.h](capi-raw-dir-h.md)

