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

 **起始版本：** 26.0.0

## 子组件

无

## 接口

DynamicComponent(options: DynamicOptions): DynamicComponentAttribute

创建DynamicComponent组件，用于显示Worker线程中运行的Abc UI。

**起始版本：** 26.0.0

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| options | [DynamicOptions](#dynamicoptions) | 是 | DynamicComponent的构造配置参数，用于配置要加载的Abc页面入口、运行Worker及显示选项。 |

## Worker

用于运行Abc的Worker线程对象，继承自[@ohos.worker](../../apis-arkts/js-apis-worker.md)中的Worker类型。

**起始版本：** 26.0.0

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## ErrorCallback

错误回调类型，继承自[@ohos.base](../../apis-basic-services-kit/js-apis-base.md#errorcallback)中的ErrorCallback类型，用于接收异常信息。

**起始版本：** 26.0.0

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## DynamicOptions

用于在DynamicComponent构造时传递参数。

**起始版本：** 26.0.0

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

| 名称 | 类型 | 只读 | 可选 | 说明 |
| -------- | -------- | -------- | -------- | -------- |
| entryPoint | string | 否 | 否 | 要加载的abc页面入口。 |
| worker | [Worker](#worker) | 否 | 否 | 运行Abc的Worker。 |
| backgroundTransparent | boolean | 否 | 是 | 是否启用组件背景透明。<br/>true：启用背景透明；false：不启用背景透明。<br/>默认值：false。 |
| allowCrossProcessNesting | boolean | 否 | 是 | 是否允许跨进程[UIExtensionComponent](./ts-container-ui-extension-component-sys.md)嵌套。<br/>true：允许跨进程嵌套；false：不允许跨进程嵌套。<br/>默认值：false。 |

## 属性

支持[通用属性](ts-component-general-attributes.md)。

## 事件

支持以下事件：

### onError

onError(callback: ErrorCallback): DynamicComponentAttribute

DynamicComponent运行过程中发生异常时触发该回调（不包含与DynamicAbility断连场景）。

**起始版本：** 26.0.0

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| callback | [ErrorCallback](#errorcallback) | 是 | 回调函数，入参用于接收异常信息。 |
