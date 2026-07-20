# DynamicOptions（系统接口）

该接口用于在构造时设置DynamicComponentAttribute的选项。

**起始版本：** 26.0.0

<!--Device-unnamed-declare interface DynamicOptions--><!--Device-unnamed-declare interface DynamicOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## allowCrossProcessNesting

```TypeScript
allowCrossProcessNesting?: boolean
```

表示是否允许DynamicComponent跨进程嵌套UEC。

**类型：** boolean

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DynamicOptions-allowCrossProcessNesting?: boolean--><!--Device-DynamicOptions-allowCrossProcessNesting?: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## allowOccupied

```TypeScript
allowOccupied?: boolean
```

表示是否允许DynamicComponent内部避让键盘。

**类型：** boolean

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DynamicOptions-allowOccupied?: boolean--><!--Device-DynamicOptions-allowOccupied?: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## backgroundTransparent

```TypeScript
backgroundTransparent?: boolean
```

表示DynamicComponent的背景是否透明。

**类型：** boolean

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DynamicOptions-backgroundTransparent?: boolean--><!--Device-DynamicOptions-backgroundTransparent?: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## entryPoint

```TypeScript
entryPoint: string
```

表示DynamicOptions的entryPoint。

**类型：** string

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DynamicOptions-entryPoint: string--><!--Device-DynamicOptions-entryPoint: string-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## worker

```TypeScript
worker: Worker
```

表示用于运行abc的受限worker。

**类型：** Worker

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DynamicOptions-worker: Worker--><!--Device-DynamicOptions-worker: Worker-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

