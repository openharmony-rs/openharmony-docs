# WritableEnvKey

定义可写的系统环境变量Key集合，用于通过@Env装饰器获取对应的系统环境变量。可通过 \_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_中的 \_\_\_MD\_LINK\_DESC\_USD\_1\_\_\_方法设置局部环境变量值以影响后代组件渲染，具体示例请参见 \_\_\_MD\_LINK\_DESC\_USD\_2\_\_\_。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

<!--Device-unnamed-declare class WritableEnvKey--><!--Device-unnamed-declare class WritableEnvKey-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## DIRECTION

```TypeScript
static readonly DIRECTION: WritableSystemEnvKey<Direction>
```

\_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_变量参数，通过@Env(WritableEnvKey.DIRECTION)可 获取[Direction]\_\_\_JSDOC\_LINK\_DESC\_USD\_3\_\_\_枚举类型的值。 当该装饰器声明在\_\_\_MD\_LINK\_DESC\_USD\_1\_\_\_或 \_\_\_MD\_LINK\_DESC\_USD\_2\_\_\_中时，用于获取窗口所在屏幕的布局方向。

**类型：** WritableSystemEnvKey&lt;Direction&gt;

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-WritableEnvKey-static readonly DIRECTION: WritableSystemEnvKey<Direction>--><!--Device-WritableEnvKey-static readonly DIRECTION: WritableSystemEnvKey<Direction>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## FONT_SCALE

```TypeScript
static readonly FONT_SCALE: WritableSystemEnvKey<double>
```

\_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_变量参数，通过@Env(WritableEnvKey.FONT\_SCALE) 可获取number类型的值，取值无上限，小于等于0的值按0处理。 当该装饰器声明在\_\_\_MD\_LINK\_DESC\_USD\_1\_\_\_或 \_\_\_MD\_LINK\_DESC\_USD\_2\_\_\_中时，用于为后代组件提供局部字体缩放倍数。

**类型：** WritableSystemEnvKey&lt;double&gt;

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-WritableEnvKey-static readonly FONT_SCALE: WritableSystemEnvKey<double>--><!--Device-WritableEnvKey-static readonly FONT_SCALE: WritableSystemEnvKey<double>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

