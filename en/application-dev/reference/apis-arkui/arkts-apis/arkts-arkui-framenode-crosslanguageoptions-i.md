# CrossLanguageOptions

Provides options for configuring or querying the cross-language access permissions for a FrameNode. For example, for nodes created using ArkTS, this API can control whether non-ArkTS languages are allowed to access or modify the attributes of these nodes.

**Since:** 15

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## attributeSetting

```TypeScript
attributeSetting?: boolean
```

Whether the FrameNode supports cross-language settings.

The value **true** means the FrameNode supports cross-language settings, and **false** means the opposite.

The default value is **false**.

**Type:** boolean

**Default:** false

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 15.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## treeOperating

```TypeScript
treeOperating?: boolean
```

Whether the FrameNode supports cross-language operations on the component tree.

The value **true** means the FrameNode supports cross-language operations on the component tree, and **false** means the opposite.

The default value is **false**.

Note: When **treeOperating** is set to **true** for a FrameNode, the FrameNode can call [addChild](../../../reference/apis-arkui/capi-arkui-nativemodule-arkui-nativenodeapi-1.md#addchild), [insertChildAfter](../../../reference/apis-arkui/capi-arkui-nativemodule-arkui-nativenodeapi-1.md#insertchildafter), [insertChildAt](../../../reference/apis-arkui/capi-arkui-nativemodule-arkui-nativenodeapi-1.md#insertchildat), [insertChildBefore](../../../reference/apis-arkui/capi-arkui-nativemodule-arkui-nativenodeapi-1.md#insertchildbefore), and [removeChild](../../../reference/apis-arkui/capi-arkui-nativemodule-arkui-nativenodeapi-1.md#removechild) across languages.

**Type:** boolean

**Default:** false

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
