# \@Env：环境变量
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @liwenzhen3-->
<!--Designer: @s10021109-->
<!--Tester: @zhangwenhan12-->
<!--Adviser: @zhang_yixin13-->

> **说明：**
> 
> 本模块首批接口从API version 22开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。

开发者指南见：[\@Env开发者指南](../../../ui/arkts-env-system-property.md)。


## \@Env

**原子化服务API：** 从API version 22开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

|名称|类型|说明|
| ----- | ----- | ------ |
|Env|[EnvDecorator](#envdecorator)| 环境变量装饰器。|

**示例：**

```ts
import { uiObserver } from '@kit.ArkUI';

@Entry
@Component
struct Index {
  @Env(SystemProperties.BREAK_POINT) breakpoint: uiObserver.WindowSizeLayoutBreakpointInfo;

  build() {}
}
```

## EnvDecorator
type EnvDecorator = (value: string) => PropertyDecorator

定义@Env装饰器类型。

**原子化服务API：** 从API version 22开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名   | 类型                  | 必填 | 说明          |
| -------- | -------------------- | ---- | --------- |
| value    |      string          | 是   |      环境变量属性名。    |

**返回值：**

|类型|说明|
| ----- | ----- |
| PropertyDecorator| 属性装饰器。 |

**错误码：**

详细介绍请参见[\@Env错误码](../errorcode-env.md)。
| 错误码ID | 错误信息 |
| ------- | -------------------------------- |
|140000|Invalid key for @Env|

## SystemProperties

定义环境变量枚举值。

**原子化服务API：** 从API version 22开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

| 名称        | 值   | 说明                                       |
| ----------- | ---- | ------------------------------------------------------------ |
|BREAK_POINT|'system.arkui.breakpoint'|[@Env](#env)变量参数，通过\@Env(SystemProperties.BREAK_POINT)可获取[`WindowSizeLayoutBreakpointInfo`](../js-apis-arkui-observer.md#windowsizelayoutbreakpointinfo22)实例。<br/>当该装饰器声明在[\@Component](../../../ui/state-management/arkts-create-custom-components.md#component)或[\@ComponentV2](../../../ui/state-management/arkts-create-custom-components.md#componentv2)中时，用于获取当前自定义组件所在窗口的尺寸布局断点信息。|
