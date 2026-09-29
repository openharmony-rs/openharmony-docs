# DynamicOptions (System API)

```TypeScript
declare interface DynamicOptions
```

Defines the parameters to be passed during **DynamicComponent** construction.

**Since:** 26.0.0

<!--Device-unnamed-declare interface DynamicOptions--><!--Device-unnamed-declare interface DynamicOptions-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## allowCrossProcessNesting

```TypeScript
allowCrossProcessNesting?: boolean
```

Whether to allow cross-process [UIExtensionComponent](arkts-arkui-uiextensioncomponent-comp-sys.md) nesting. **true**: yes; **false**: no. The default value is **false**.

**Type:** boolean

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-DynamicOptions-allowCrossProcessNesting?: boolean--><!--Device-DynamicOptions-allowCrossProcessNesting?: boolean-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## allowOccupied

```TypeScript
allowOccupied?: boolean
```

Indicates allow keyboard avoidance inside the DynamicComponent.

**Type:** boolean

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-DynamicOptions-allowOccupied?: boolean--><!--Device-DynamicOptions-allowOccupied?: boolean-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## backgroundTransparent

```TypeScript
backgroundTransparent?: boolean
```

Whether to enable the transparent background for the component. **true**: yes; **false**: no. The default value is **false**.

**Type:** boolean

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-DynamicOptions-backgroundTransparent?: boolean--><!--Device-DynamicOptions-backgroundTransparent?: boolean-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## entryPoint

```TypeScript
entryPoint: string
```

Entry of the .abc page to be loaded.

**Type:** string

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-DynamicOptions-entryPoint: string--><!--Device-DynamicOptions-entryPoint: string-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## worker

```TypeScript
worker: Worker
```

Worker for running the .abc file.

**Type:** [Worker](arkts-arkui-dynamiccomponent-comp-worker-t-sys.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-DynamicOptions-worker: Worker--><!--Device-DynamicOptions-worker: Worker-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.
