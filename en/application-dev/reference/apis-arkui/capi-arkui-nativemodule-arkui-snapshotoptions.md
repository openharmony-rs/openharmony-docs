# ArkUI_SnapshotOptions
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @zhou-chaobo-->
<!--Designer: @piggyguy-->
<!--Tester: @songyanhong-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=9c92183287fa23162e04874223c3b068eb1f8a4d translatedAt=2026-11-23T07:08:18.382Z pushedAt=2026-11-25T01:17:18.955Z nl=1 -->

```c
typedef struct ArkUI_SnapshotOptions ArkUI_SnapshotOptions
```

## Overview

Defines snapshot options, used to configure the snapshot behavior when taking a snapshot of a component. It applies to scenarios where the snapshot output effect needs to be controlled based on service requirements.

To use this struct, first call [OH_ArkUI_CreateSnapshotOptions](capi-common-attributes-h.md#oh_arkui_createsnapshotoptions) to create a snapshot options object, and set the snapshot parameters through the related configuration APIs; then pass the object as the **snapshotOptions** parameter to [OH_ArkUI_GetNodeSnapshot](capi-native-node-h.md#oh_arkui_getnodesnapshot). When the object is no longer used, you must call [OH_ArkUI_DestroySnapshotOptions](capi-common-attributes-h.md#oh_arkui_destroysnapshotoptions) to release resources.

**Since**: 15

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**Header file**: [common_attributes.h](capi-common-attributes-h.md)

