# DynamicOptions（系统接口）

用于在DynamicComponent构造时传递参数。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

<!--Device-unnamed-export declare interface DynamicOptions--><!--Device-unnamed-export declare interface DynamicOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## allowCrossProcessNesting

```TypeScript
allowCrossProcessNesting?: boolean
```

是否允许DynamicComponent跨进程嵌套UIExtensionComponent。<br/>true：允许跨进程嵌套；false：不允许跨进程嵌套。<br/>默认值：false

**类型：** boolean

**默认值：** false

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

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

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DynamicOptions-allowOccupied?: boolean--><!--Device-DynamicOptions-allowOccupied?: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## backgroundTransparent

```TypeScript
backgroundTransparent?: boolean
```

是否启用组件背景透明。<br/>true：启用背景透明；false：不启用背景透明。<br/>默认值：false

**类型：** boolean

**默认值：** false

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DynamicOptions-backgroundTransparent?: boolean--><!--Device-DynamicOptions-backgroundTransparent?: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## entryPoint

```TypeScript
entryPoint: string
```

要加载的Abc页面入口。<br/>取值格式：'bundleName/moduleName/pagePath'，例如'com.example.myapplication/entry/ets/pages/DynamicPage'。

**类型：** string

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DynamicOptions-entryPoint: string--><!--Device-DynamicOptions-entryPoint: string-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## worker

```TypeScript
worker: EAWorker | undefined
```

运行Abc的Worker。<br/>ArkTS-Sta模式下，可传入undefined，表示回拉起一个空的DynamicComponent。

**类型：** [EAWorker](arkts-na-eaworker-c.md) \| undefined

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DynamicOptions-worker: EAWorker | undefined--><!--Device-DynamicOptions-worker: EAWorker | undefined-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

