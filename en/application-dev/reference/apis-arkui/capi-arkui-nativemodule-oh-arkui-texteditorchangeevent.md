# OH_ArkUI_TextEditorChangeEvent

 <!--Kit: ArkUI-->
 <!--Subsystem: ArkUI-->
 <!--Owner: @carnivore233-->
 <!--Designer: @carnivore233-->
 <!--Tester: @mateng_Holtens-->
 <!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=2c5ecf1461774eee81076a9dfbe0054fd9d94ff3 translatedAt=2026-08-21T04:07:41.490Z pushedAt=2026-08-21T06:44:48.348Z -->

```c
typedef struct OH_ArkUI_TextEditorChangeEvent OH_ArkUI_TextEditorChangeEvent
```

## Overview

Defines the text content change event of the **TextEditor** component, which is used to notify users when the text content changes and supports obtaining information such as the content before and after the change. It is applicable to scenarios where interception or validation is required before the text content changes, such as input interception, content filtering, and change confirmation.

**Since**: 24

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**Header file**: [native_node.h](capi-native-node-h.md)