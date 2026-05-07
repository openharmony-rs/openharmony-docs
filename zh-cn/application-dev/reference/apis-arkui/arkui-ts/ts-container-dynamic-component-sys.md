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

### DynamicComponent<sup>26+</sup>

ArkTS-Dyn: DynamicComponent(options: DynamicOptions): DynamicComponentAttribute

ArkTS-Sta: DynamicComponent(options: DynamicOptions): DynamicComponentAttribute

创建DynamicComponent组件，用于显示Worker线程中运行的Abc UI。

**起始版本：** 26.0.0

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| options | [DynamicOptions](#dynamicoptions) | 是 | DynamicComponent构造参数。 |

## DynamicOptions

用于在DynamicComponent构造时传递参数。

**起始版本：** 26.0.0

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

| 名称 | 类型 | 只读 | 可选 | 说明 |
| -------- | -------- | -------- | -------- | -------- |
| entryPoint | string | 否 | 否 | 要加载的abc页面入口。 |
| worker | ArkTS-Dyn: [Worker](../../apis-arkts/js-apis-worker.md)<br/>ArkTS-Sta: EAWorker \| undefined | 否 | ArkTS-Dyn: 否<br/>ArkTS-Sta: 是 | 运行Abc的Worker。 |
| backgroundTransparent | boolean | 否 | 是 | 是否启用组件背景透明。<br/>true：启用背景透明；false：不启用背景透明。<br/>默认值：false。 |
| allowCrossProcessNesting | boolean | 否 | 是 | 是否允许跨进程[UIExtensionComponent](./ts-container-ui-extension-component-sys.md)嵌套。<br/>true：允许跨进程嵌套；false：不允许跨进程嵌套。<br/>默认值：false。 |
| allowOccupied<sup>26+</sup> | boolean | 否 | 是 | 是否允许DynamicComponent占用键盘避让区域。<br/>true：允许占用键盘避让区域；false：不允许占用键盘避让区域。<br/>默认值：false。<br/>**说明：** 仅ArkTS-Sta支持此参数。 |

## 属性

支持[通用属性](ts-component-general-attributes.md)。

## 事件

支持以下事件：

### onError

ArkTS-Dyn: onError(callback: ErrorCallback): DynamicComponentAttribute

ArkTS-Sta: onError(callback: ErrorCallback\<[BusinessError](../../apis-basic-services-kit/js-apis-base.md#businesserror)> | undefined): DynamicComponentAttribute

DynamicComponent运行过程中发生异常时触发该回调（不包含与DynamicAbility断连场景）。

**起始版本：** 26.0.0

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| callback | ArkTS-Dyn: [ErrorCallback](../../apis-basic-services-kit/js-apis-base.md#errorcallback)<br/>ArkTS-Sta: [ErrorCallback](../../apis-basic-services-kit/js-apis-base.md#errorcallback)\<[BusinessError](../../apis-basic-services-kit/js-apis-base.md#businesserror)> \| undefined | 是 | 回调函数，入参用于接收异常信息。<br/>ArkTS-Sta模式下可不传。 |
