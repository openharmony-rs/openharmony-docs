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

如需读取由[WithEnv](ts-container-with-env.md)作用域通过[customEnv](ts-container-with-env.md#customenv)设置的自定义环境变量，请参考[@CustomEnv：自定义环境变量](ts-custom-env-system-property.md)。

除本文明确列出的`@Env('system.arkui.layout.direction')`外，当前文档不表示其他普通系统环境变量已经与WithEnv形成通用的作用域化读取和更新链路。

## \@Env
Env: EnvDecorator

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
  // @Env读取系统环境变量
  @Env(SystemProperties.BREAK_POINT) breakpoint: uiObserver.WindowSizeLayoutBreakpointInfo;

  build() {}
}
```

## EnvDecorator
type EnvDecorator = (value: SystemProperties | 'system.arkui.layout.direction') => PropertyDecorator

定义@Env装饰器类型。

**模型约束**：此接口仅可在Stage模型下使用。

**原子化服务API：** 从API version 22开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名   | 类型                  | 必填 | 说明          |
| -------- | -------------------- | ---- | --------- |
| value    | [SystemProperties](./ts-env-system-property.md#systemproperties) \| `'system.arkui.layout.direction'` | 是   | 环境变量属性名。`SystemProperties`用于读取组件所在窗口的环境变量；`'system.arkui.layout.direction'`用于读取当前组件上下文中的方向环境变量。 |

**返回值：**

|类型|说明|
| ----- | ----- |
| PropertyDecorator| 属性装饰器。 |

**错误码：**

详细介绍请参见[环境变量错误码](../errorcode-env.md)。

| 错误码ID | 错误信息 |
| ------- | -------------------------------- |
|140000|Invalid key for @Env|

## WithEnv作用域化方向环境变量

可通过`@Env('system.arkui.layout.direction')`读取当前组件上下文中的方向环境变量。该能力与[WithEnv](ts-container-with-env.md)配合使用，用于读取祖先作用域通过`env(SystemEnvKeys.DIRECTION, value)`设置的局部布局方向。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

| 参数 | 返回类型 | 说明 |
| ----- | ----- | ----- |
| `'system.arkui.layout.direction'` | [Direction](ts-appendix-enums.md#direction) | 返回当前组件上下文的方向值。显式设置的[direction](ts-universal-attributes-location.md#direction)优先于祖先WithEnv方向作用域；没有匹配的WithEnv方向作用域时，读取结果与当前组件的direction解析语义保持一致。 |

> **说明：**
>
> - `@Env('system.arkui.layout.direction')`会在祖先WithEnv方向作用域变化，或attach/detach/reparent导致最近作用域提供者变化时响应式更新。
> - `Direction.Auto`保留Auto语义；实际非Auto回落仍遵循组件现有方向解析规则。

**示例：**

```ts
@Component
struct DirectionTag {
  @Env('system.arkui.layout.direction') currentDirection: Direction;

  build() {
    Text(`${this.currentDirection}`)
  }
}

@Entry
@Component
struct Index {
  @State directionValue: Direction = Direction.Ltr;

  build() {
    Column({ space: 12 }) {
      Button('切换方向')
        .onClick(() => {
          this.directionValue = this.directionValue === Direction.Ltr ? Direction.Rtl : Direction.Ltr;
        })

      WithEnv() {
        DirectionTag()
      }
      .env(SystemEnvKeys.DIRECTION, this.directionValue)
    }
  }
}
```

## SystemProperties

定义窗口级环境变量枚举值。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

| 名称        | 值   | 说明                                       |
| ----------- | ---- | ------------------------------------------------------------ |
|BREAK_POINT|'system.arkui.breakpoint'|[@Env](#env)变量参数，通过\@Env(SystemProperties.BREAK_POINT)可获取[`WindowSizeLayoutBreakpointInfo`](../js-apis-arkui-observer.md#windowsizelayoutbreakpointinfo22)实例。<br/>当该装饰器声明在[\@Component](../../../ui/state-management/arkts-create-custom-components.md#component)或[\@ComponentV2](../../../ui/state-management/arkts-create-custom-components.md#componentv2)中时，用于获取当前自定义组件所在窗口的尺寸布局断点信息。<br/>**原子化服务API：** 从API version 22开始，该接口支持在原子化服务中使用。|
|WINDOW_SIZE<sup>23+</sup>|'system.window.size'|[@Env](#env)变量参数，通过\@Env(SystemProperties.WINDOW_SIZE)可获取[`SizeInVP`](../arkts-apis-window-i.md#sizeinvp23)实例。<br/>当该装饰器声明在[\@Component](../../../ui/state-management/arkts-create-custom-components.md#component)或[\@ComponentV2](../../../ui/state-management/arkts-create-custom-components.md#componentv2)中时，用于获取当前自定义组件所在窗口的大小信息，单位为vp。<br/>**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。<br/>**模型约束**：此接口仅可在Stage模型下使用。|
|WINDOW_SIZE_PX<sup>23+</sup>|'system.window.size.px'|[@Env](#env)变量参数，通过\@Env(SystemProperties.WINDOW_SIZE_PX)可获取[`Size`](../arkts-apis-window-i.md#size7)实例。<br/>当该装饰器声明在[\@Component](../../../ui/state-management/arkts-create-custom-components.md#component)或[\@ComponentV2](../../../ui/state-management/arkts-create-custom-components.md#componentv2)中时，用于获取当前自定义组件所在窗口的大小信息，单位为px。<br/>**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。<br/>**模型约束**：此接口仅可在Stage模型下使用。|
|WINDOW_AVOID_AREA<sup>23+</sup>|'system.window.avoidarea'|[@Env](#env)变量参数，通过\@Env(SystemProperties.WINDOW_AVOID_AREA)可获取[`UIEnvWindowAvoidAreaInfoVP`](../arkts-apis-window-i.md#uienvwindowavoidareainfovp23)实例。<br/>当该装饰器声明在[\@Component](../../../ui/state-management/arkts-create-custom-components.md#component)或[\@ComponentV2](../../../ui/state-management/arkts-create-custom-components.md#componentv2)中时，用于获取当前自定义组件所在窗口的避让区域信息，单位为vp。<br/>**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。<br/>**模型约束**：此接口仅可在Stage模型下使用。|
|WINDOW_AVOID_AREA_PX<sup>23+</sup>|'system.window.avoidarea.px'|[@Env](#env)变量参数，通过\@Env(SystemProperties.WINDOW_AVOID_AREA_PX)可获取[`UIEnvWindowAvoidAreaInfoPX`](../arkts-apis-window-i.md#uienvwindowavoidareainfopx23)实例。<br/>当该装饰器声明在[\@Component](../../../ui/state-management/arkts-create-custom-components.md#component)或[\@ComponentV2](../../../ui/state-management/arkts-create-custom-components.md#componentv2)中时，用于获取当前自定义组件所在窗口的避让区域信息，单位为px。<br/>**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。<br/>**模型约束**：此接口仅可在Stage模型下使用。|
|WINDOW_DISPLAY_ID|'system.window.displayid'|[@Env](#env)变量参数，通过\@Env(SystemProperties.WINDOW_DISPLAY_ID)可获取number类型的值。<br/>当该装饰器声明在[\@Component](../../../ui/state-management/arkts-create-custom-components.md#component)或[\@ComponentV2](../../../ui/state-management/arkts-create-custom-components.md#componentv2)中时，用于获取当前自定义组件所在窗口的屏幕ID。<br/>**起始版本：** 26.0.0<br/>**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。<br/>**模型约束**：此接口仅可在Stage模型下使用。|
|WINDOW_SYSTEM_DENSITY|'system.window.density.system'|[@Env](#env)变量参数，通过\@Env(SystemProperties.WINDOW_SYSTEM_DENSITY)可获取number类型的值。<br/>当该装饰器声明在[\@Component](../../../ui/state-management/arkts-create-custom-components.md#component)或[\@ComponentV2](../../../ui/state-management/arkts-create-custom-components.md#componentv2)中时，用于获取当前自定义组件所在窗口的系统显示大小缩放系数。该参数为浮点数，取值范围为[0.5, 4.0]或-1.0。4.0表示窗口可显示的最大显示大小缩放系数，-1.0表示窗口使用系统显示大小缩放系数。<br/>**起始版本：** 26.0.0<br/>**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。<br/>**模型约束**：此接口仅可在Stage模型下使用。|
