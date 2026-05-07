# DynamicComponent (系统接口)
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @dutie123-->
<!--Designer: @dutie123-->
<!--Tester: @fredyuan0912-->
<!--Adviser: @Brilliantry_Rui-->

DynamicComponent用于支持在本页面内嵌入显示独立Abc（.abc文件）提供的UI，展示的内容在Worker线程中运行。

通常用于动态加载Abc页面的模块化开发场景。

> **说明：**
>
> - 本模块为系统接口。
> - 本模块接口仅可在Stage模型下使用。

## 子组件

无

## 接口

DynamicComponent(options: DynamicOptions)

创建DynamicComponent组件，用于显示Worker线程中运行的Abc UI。

**系统接口：** 此接口为系统接口。

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| options | [DynamicOptions](#dynamicoptions) | 是 | DynamicComponent构造参数。 |

## DynamicOptions

用于在DynamicComponent构造时传递参数。

**系统接口：** 此接口为系统接口。

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

| 名称 | 类型 | 只读 | 可选 | 说明 |
| -------- | -------- | -------- | -------- | -------- |
| entryPoint | string | 否 | 否 | 要加载的abc页面入口。 |
| worker | [Worker](../../apis-arkts/js-apis-worker.md) | 否 | 否 | 运行Abc的Worker。 |
| backgroundTransparent | boolean | 否 | 是 | 是否启用组件背景透明。 |
| allowCrossProcessNesting | boolean | 否 | 是 | 是否允许跨进程[UIExtensionComponent](./ts-container-ui-extension-component-sys.md)嵌套。 |

## 属性

支持[通用属性](ts-component-general-attributes.md)。

## 事件

支持以下事件：

### onError

onError(callback: ErrorCallback)

DynamicComponent运行过程中发生异常时触发该回调（不包含与DynamicAbility断连场景）。

**系统接口：** 此接口为系统接口。

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| callback | [ErrorCallback](../../apis-basic-services-kit/js-apis-base.md#errorcallback) | 是 | 回调函数，入参用于接收异常信息。 |
