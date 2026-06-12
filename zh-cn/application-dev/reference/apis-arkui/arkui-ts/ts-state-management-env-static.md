# \@Env：环境变量 (ArkTS-Sta)
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @zhushilin5-->
<!--Designer: @s10021109-->
<!--Tester: @zhangwenhan12-->
<!--Adviser: @zhang_yixin13-->

> **说明：**
> 
>-  本模块首批接口从API version 24开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。
>
> - 本模块仅支持ArkTS-Sta。

## 导入模块

```ts
import { Env, SystemProperties, SystemEnvKey, WritableSystemEnvKey, ReadonlySystemEnvKey, WritableEnvKey, ReadonlyEnvKey } from '@kit.ArkUI';
```

开发者指南见：[\@Env开发者指南](../../../ui/state-management-static/arkts-static-new-env.md)。

## Env

环境变量装饰器，用于获取系统环境变量信息。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

| 名称 | 类型 | 说明 |
| --- | --- | --- |
| value | string | \@Env的参数，用于指定环境变量的key值。<br/>API版本26.0.0之前，仅支持[SystemProperties](#systemproperties)的枚举值。<br/>API版本26.0.0及以后，额外支持使用字符串字面量格式`'ReadonlyEnvKey.<keyName>'`或`'WritableEnvKey.<keyName>'`，其中keyName必须为[ReadonlyEnvKey](#readonlyenvkey)或[WritableEnvKey](#writableenvkey)的成员变量，不支持任意字符串。|

## SystemProperties

定义环境变量枚举值。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

| 名称        | 值   | 说明                                       |
| ----------- | ---- | ------------------------------------------------------------ |
|BREAK_POINT |'system.arkui.breakpoint'|[\@Env](../../../ui/state-management-static/arkts-static-new-env.md)变量参数，通过\@Env(SystemProperties.BREAK_POINT)可获取[WindowSizeLayoutBreakpointInfo](../js-apis-arkui-observer.md#windowsizelayoutbreakpointinfo22)实例。<br/>当该装饰器声明在[\@Component](../../../ui/state-management-static/arkts-static-create-component.md)或[\@ComponentV2](../../../ui/state-management-static/arkts-static-componentv2.md)中时，用于获取当前自定义组件所在窗口的尺寸布局断点信息。|
|WINDOW_SIZE |'system.window.size'|@Env变量参数，通过\@Env(SystemProperties.WINDOW_SIZE)可获取`SizeInVP`实例。<br/>当该装饰器声明在\@Component或\@ComponentV2中时，用于获取当前自定义组件所在窗口的大小信息，单位为vp。<br/>**模型约束**：此接口仅可在Stage模型下使用。|
|WINDOW_SIZE_PX |'system.window.size.px'|@Env变量参数，通过\@Env(SystemProperties.WINDOW_SIZE_PX)可获取[Size](../arkts-apis-window-i.md#size7)实例。<br/>当该装饰器声明在\@Component或\@ComponentV2中时，用于获取当前自定义组件所在窗口的大小信息，单位为px。<br/>**模型约束**：此接口仅可在Stage模型下使用。|
|WINDOW_AVOID_AREA |'system.window.avoidarea'|@Env变量参数，通过\@Env(SystemProperties.WINDOW_AVOID_AREA)可获取`UIEnvWindowAvoidAreaInfoVP`实例。<br/>当该装饰器声明在\@Component或\@ComponentV2中时，用于获取当前自定义组件所在窗口的避让区域信息，单位为vp。<br/>**模型约束**：此接口仅可在Stage模型下使用。|
|WINDOW_AVOID_AREA_PX |'system.window.avoidarea.px'|@Env变量参数，通过\@Env(SystemProperties.WINDOW_AVOID_AREA_PX)可获取`UIEnvWindowAvoidAreaInfoPX`实例。<br/>当该装饰器声明在\@Component或\@ComponentV2中时，用于获取当前自定义组件所在窗口的避让区域信息，单位为px。<br/>**模型约束**：此接口仅可在Stage模型下使用。|

## SystemEnvKey

系统环境变量Key的基类。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 26.0.0

### constructor

protected constructor()

系统环境变量Key的构造函数。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 26.0.0

## WritableSystemEnvKey

可写系统环境变量Key，继承自[SystemEnvKey](#systemenvkey)。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 26.0.0

## ReadonlySystemEnvKey

只读系统环境变量Key，继承自[SystemEnvKey](#systemenvkey)。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 26.0.0

## WritableEnvKey

可写系统环境变量Key类，用于\@Env装饰器的字符串参数格式`'WritableEnvKey.<keyName>'`中的key声明。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 26.0.0

## ReadonlyEnvKey

只读系统环境变量Key类，用于\@Env装饰器的字符串参数格式`'ReadonlyEnvKey.<keyName>'`中的key声明。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 26.0.0

### 属性

| 名称 | 类型 | 说明 |
| -------- | -------- | ------ |
| WINDOW_AVOID_AREA | [ReadonlySystemEnvKey](#readonlysystemenvkey) |[\@Env](#env)变量参数，通过\@Env('ReadonlyEnvKey.WINDOW_AVOID_AREA')可获取[UIEnvWindowAvoidAreaInfoVP](../arkts-apis-window-i.md#uienvwindowavoidareainfovp23)实例。<br/>当该装饰器声明在[\@Component](../../../ui/state-management-static/arkts-static-create-component.md)或[\@ComponentV2](../../../ui/state-management-static/arkts-static-componentv2.md)中时，用于获取当前自定义组件所在窗口的避让区域信息，单位为vp。<br/>**起始版本：** 26.0.0<br/>**模型约束：** 此接口仅可在Stage模型下使用。 |
| WINDOW_AVOID_AREA_PX | [ReadonlySystemEnvKey](#readonlysystemenvkey) |[\@Env](#env)变量参数，通过\@Env('ReadonlyEnvKey.WINDOW_AVOID_AREA_PX')可获取[UIEnvWindowAvoidAreaInfoPX](../arkts-apis-window-i.md#uienvwindowavoidareainfopx23)实例。<br/>当该装饰器声明在[\@Component](../../../ui/state-management-static/arkts-static-create-component.md)或[\@ComponentV2](../../../ui/state-management-static/arkts-static-componentv2.md)中时，用于获取当前自定义组件所在窗口的避让区域信息，单位为px。<br/>**起始版本：** 26.0.0<br/>**模型约束：** 此接口仅可在Stage模型下使用。 |
| WINDOW_SIZE | [ReadonlySystemEnvKey](#readonlysystemenvkey) |[\@Env](#env)变量参数，通过\@Env('ReadonlyEnvKey.WINDOW_SIZE')可获取[SizeInVP](../arkts-apis-window-i.md#sizeinvp23)实例。<br/>当该装饰器声明在[\@Component](../../../ui/state-management-static/arkts-static-create-component.md)或[\@ComponentV2](../../../ui/state-management-static/arkts-static-componentv2.md)中时，用于获取当前自定义组件所在窗口的大小信息，单位为vp。<br/>**起始版本：** 26.0.0<br/>**模型约束：** 此接口仅可在Stage模型下使用。 |
| WINDOW_SIZE_PX | [ReadonlySystemEnvKey](#readonlysystemenvkey) |[\@Env](#env)变量参数，通过\@Env('ReadonlyEnvKey.WINDOW_SIZE_PX')可获取[Size](../arkts-apis-window-i.md#size7)实例。<br/>当该装饰器声明在[\@Component](../../../ui/state-management-static/arkts-static-create-component.md)或[\@ComponentV2](../../../ui/state-management-static/arkts-static-componentv2.md)中时，用于获取当前自定义组件所在窗口的大小信息，单位为px。<br/>**起始版本：** 26.0.0<br/>**模型约束：** 此接口仅可在Stage模型下使用。 |
| WINDOW_DISPLAY_ID | [ReadonlySystemEnvKey](#readonlysystemenvkey) |[\@Env](#env)变量参数，通过\@Env('ReadonlyEnvKey.WINDOW_DISPLAY_ID')可获取long类型的值。<br/>当该装饰器声明在[\@Component](../../../ui/state-management-static/arkts-static-create-component.md)或[\@ComponentV2](../../../ui/state-management-static/arkts-static-componentv2.md)中时，用于获取当前自定义组件所在窗口的屏幕ID。<br/>**起始版本：** 26.0.0<br/>**模型约束：** 此接口仅可在Stage模型下使用。 |
| WINDOW_SYSTEM_DENSITY | [ReadonlySystemEnvKey](#readonlysystemenvkey) |[\@Env](#env)变量参数，通过\@Env('ReadonlyEnvKey.WINDOW_SYSTEM_DENSITY')可获取double类型的值。<br/>当该装饰器声明在[\@Component](../../../ui/state-management-static/arkts-static-create-component.md)或[\@ComponentV2](../../../ui/state-management-static/arkts-static-componentv2.md)中时，用于获取当前自定义组件所在窗口的系统显示大小缩放系数。该参数为浮点数，取值范围为[0.5, 4.0]或-1.0。4.0表示窗口可显示的最大显示大小缩放系数，-1.0表示窗口使用系统显示大小缩放系数。<br/>**起始版本：** 26.0.0<br/>**模型约束：** 此接口仅可在Stage模型下使用。 |
| WINDOW_IS_FOCUSED | [ReadonlySystemEnvKey](#readonlysystemenvkey) |[\@Env](#env)变量参数，通过\@Env('ReadonlyEnvKey.WINDOW_IS_FOCUSED')可获取boolean类型的值。<br/>当该装饰器声明在[\@Component](../../../ui/state-management-static/arkts-static-create-component.md)或[\@ComponentV2](../../../ui/state-management-static/arkts-static-componentv2.md)中时，用于获取当前自定义组件所在窗口是否获焦。<br/>**起始版本：** 26.0.0<br/>**模型约束：** 此接口仅可在Stage模型下使用。 |
| WINDOW_IS_HIGHLIGHTED | [ReadonlySystemEnvKey](#readonlysystemenvkey) |[\@Env](#env)变量参数，通过\@Env('ReadonlyEnvKey.WINDOW_IS_HIGHLIGHTED')可获取boolean类型的值。<br/>当该装饰器声明在[\@Component](../../../ui/state-management-static/arkts-static-create-component.md)或[\@ComponentV2](../../../ui/state-management-static/arkts-static-componentv2.md)中时，用于获取当前自定义组件所在窗口是否高亮。<br/>**起始版本：** 26.0.0<br/>**模型约束：** 此接口仅可在Stage模型下使用。 |