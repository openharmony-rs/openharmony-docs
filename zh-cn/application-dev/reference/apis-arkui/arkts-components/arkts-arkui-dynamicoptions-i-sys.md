# DynamicOptions（系统接口）

用于在DynamicComponent构造时传递参数。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

<!--Device-unnamed-declare interface DynamicOptions--><!--Device-unnamed-declare interface DynamicOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## allowCrossProcessNesting

```TypeScript
allowCrossProcessNesting?: boolean
```

是否允许跨进程[UIExtensionComponent]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_嵌套。\_\_\_HTML\_TAG\_DESC\_USD\_1\_\_\_true：允许跨进程嵌套；false：不允许跨进程嵌套。\_\_\_HTML\_TAG\_DESC\_USD\_2\_\_\_默认值：false

**类型：** boolean

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

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

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DynamicOptions-allowOccupied?: boolean--><!--Device-DynamicOptions-allowOccupied?: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## backgroundTransparent

```TypeScript
backgroundTransparent?: boolean
```

是否启用组件背景透明。\_\_\_HTML\_TAG\_DESC\_USD\_0\_\_\_true：启用背景透明；false：不启用背景透明。\_\_\_HTML\_TAG\_DESC\_USD\_1\_\_\_默认值：false

**类型：** boolean

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DynamicOptions-backgroundTransparent?: boolean--><!--Device-DynamicOptions-backgroundTransparent?: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## entryPoint

```TypeScript
entryPoint: string
```

要加载的Abc页面入口。\_\_\_HTML\_TAG\_DESC\_USD\_0\_\_\_取值格式：'bundleName/moduleName/pagePath'，例如'com.example.myapplication/entry/ets/pages/DynamicPage'。

**类型：** string

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DynamicOptions-entryPoint: string--><!--Device-DynamicOptions-entryPoint: string-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## worker

```TypeScript
worker: Worker
```

用于运行Abc的Worker线程对象，需通过worker.ThreadWorker创建。Worker在独立线程中执行Abc的UI逻辑，与主线程通信。

**类型：** Worker

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DynamicOptions-worker: Worker--><!--Device-DynamicOptions-worker: Worker-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

