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

Whether to allow cross-process [UIExtensionComponent](arkts-arkui-uiextensioncomponent-comp-sys.md) nesting.<br>**true**: allow cross-process nesting; **false**: disallow cross-process nesting.<br>Default value: **false**

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

Whether to allow the **DynamicComponent** to avoid the keyboard internally.<br>**true**: allow avoiding the keyboard; **false**: do not allow avoiding the keyboard.<br>Default value: **false**

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

Whether to enable background transparency for the component.<br>**true**: enable background transparency; **false**: disable background transparency.<br>Default value: **false**

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

The .abc page entry to load. The value format is 'bundleName/moduleName/pagePath', for example,'com.example.myapplication/entry/ets/pages/DynamicPage'.

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

Worker thread object used to run the .abc, which must be created through **worker.ThreadWorker**. The Worker executes the UI logic of the .abc in an independent thread and communicates with the main thread.

**Type:** [Worker](arkts-arkui-dynamiccomponent-comp-worker-t-sys.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-DynamicOptions-worker: Worker--><!--Device-DynamicOptions-worker: Worker-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.
