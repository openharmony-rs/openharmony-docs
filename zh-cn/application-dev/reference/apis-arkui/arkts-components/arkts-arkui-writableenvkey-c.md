# WritableEnvKey

定义可写的系统环境变量Key集合，用于通过@Env装饰器获取对应的系统环境变量。可通过 [WithEnv](../arkts-apis/arkts-arkui-arkui-withenv-con.md)中的 env方法设置局部环境变量值以影响后代组件渲染，具体示例请参见 [示例2（设置局部布局方向）](../../../reference/apis-arkui/arkui-ts/ts-container-with-env.md#示例2设置局部布局方向)。

**起始版本：** 26.0.0

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
```

## DIRECTION

```TypeScript
static readonly DIRECTION: WritableSystemEnvKey<Direction>
```

[@Env](../../../reference/apis-arkui/arkui-ts/ts-env-system-property.md#env)变量参数，通过@Env(WritableEnvKey.DIRECTION)可 获取Direction枚举类型的值。当该装饰器声明在[@Component](../../../ui/state-management/arkts-create-custom-components.md#component)或 [@ComponentV2](../../../ui/state-management/arkts-create-custom-components.md#componentv2)中时，用于获取窗口所在屏幕的布局方向。

**类型：** [WritableSystemEnvKey](arkts-arkui-writablesystemenvkey-c.md)&lt;Direction&gt;

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## FONT_SCALE

```TypeScript
static readonly FONT_SCALE: WritableSystemEnvKey<number>
```

[@Env](../../../reference/apis-arkui/arkui-ts/ts-env-system-property.md#env)变量参数，通过@Env(WritableEnvKey.FONT_SCALE) 可获取number类型的值，取值无上限，小于等于0的值按0处理。当该装饰器声明在[@Component](../../../ui/state-management/arkts-create-custom-components.md#component)或 [@ComponentV2](../../../ui/state-management/arkts-create-custom-components.md#componentv2)中时，用于为后代组件提供局部字体缩放倍数。

**类型：** [WritableSystemEnvKey](arkts-arkui-writablesystemenvkey-c.md)&lt;number&gt;

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
