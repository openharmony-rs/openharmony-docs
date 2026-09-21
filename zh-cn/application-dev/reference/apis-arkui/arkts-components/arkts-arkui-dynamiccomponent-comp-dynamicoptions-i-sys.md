# DynamicOptions（系统接口）

```TypeScript
declare interface DynamicOptions
```

用于在DynamicComponent构造时传递参数。

**起始版本：** 26.0.0

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## allowCrossProcessNesting

```TypeScript
allowCrossProcessNesting?: boolean
```

是否允许跨进程[UIExtensionComponent](arkts-arkui-uiextensioncomponent-comp-sys.md#ui_extension_componentsystem-api)嵌套。<br>true：允许跨进程嵌套；false：不允许跨进程嵌套。<br>默认值：false

**类型：** boolean

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

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

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## backgroundTransparent

```TypeScript
backgroundTransparent?: boolean
```

是否启用组件背景透明。<br>true：启用背景透明；false：不启用背景透明。<br>默认值：false

**类型：** boolean

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## entryPoint

```TypeScript
entryPoint: string
```

要加载的Abc页面入口。<br>取值格式：'bundleName/moduleName/pagePath'，例如'com.example.myapplication/entry/ets/pages/DynamicPage'。

**类型：** string

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## worker

```TypeScript
worker: Worker
```

用于运行Abc的Worker线程对象，需通过worker.ThreadWorker创建。Worker在独立线程中执行Abc的UI逻辑，与主线程通信。

**类型：** [Worker](arkts-arkui-dynamiccomponent-comp-worker-t-sys.md)

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。
