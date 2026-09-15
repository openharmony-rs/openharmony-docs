# ArkUI_SnapshotOptions

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @yihao-lin-->
<!--Designer: @piggyguy-->
<!--Tester: @songyanhong-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=307c96700aa31ceaed2d16437f8e9e4fabcbd960 translatedAt=2026-08-21T01:42:37.976Z pushedAt=2026-08-21T02:14:32.864Z -->

```c
typedef struct ArkUI_SnapshotOptions ArkUI_SnapshotOptions
```

## Overview

Defines snapshot options, used to configure the snapshot behavior when taking a snapshot of a component. It applies to scenarios where the snapshot output effect needs to be controlled based on service requirements.

To use this struct, first call [OH_ArkUI_CreateSnapshotOptions](capi-common-attributes-h.md#oh_arkui_createsnapshotoptions) to create a snapshot options object, and set the snapshot parameters through [OH_ArkUI_SnapshotOptions_SetScale](capi-common-attributes-h.md#oh_arkui_snapshotoptions_setscale), [OH_ArkUI_SnapshotOptions_SetColorMode](capi-common-attributes-h.md#oh_arkui_snapshotoptions_setcolormode), and [OH_ArkUI_SnapshotOptions_SetDynamicRangeMode](capi-common-attributes-h.md#oh_arkui_snapshotoptions_setdynamicrangemode); then pass the object as the **snapshotOptions** parameter to [OH_ArkUI_GetNodeSnapshot](capi-native-node-h.md#oh_arkui_getnodesnapshot). When the object is no longer used, call [OH_ArkUI_DestroySnapshotOptions](capi-common-attributes-h.md#oh_arkui_destroysnapshotoptions) to release resources.

**Since**: 15

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**Header file**: [common_attributes.h](capi-common-attributes-h.md)