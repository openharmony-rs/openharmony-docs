# ProgressConfiguration

进度条配置。继承自[CommonConfiguration]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_。

**继承/实现关系：** ProgressConfiguration extends [CommonConfiguration<ProgressConfiguration>](CommonConfiguration<ProgressConfiguration>)

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

<!--Device-unnamed-declare interface ProgressConfiguration extends CommonConfiguration<ProgressConfiguration>--><!--Device-unnamed-declare interface ProgressConfiguration extends CommonConfiguration<ProgressConfiguration>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## total

```TypeScript
total: number
```

进度总长。 取值范围：(0, +∞) **说明：** total小于等于0时，按照100处理。

**类型：** number

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-ProgressConfiguration-total: number--><!--Device-ProgressConfiguration-total: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## value

```TypeScript
value: number
```

当前进度值。当设置的数值小于0时，将其置为0。当设置的数值大于total时，将其置为total。 默认值：0 取值范围：[0, total] **说明：** 当Ring类型进度条的status设置为ProgressStatus.LOADING时，设置进度值不生效。

**类型：** number

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-ProgressConfiguration-value: number--><!--Device-ProgressConfiguration-value: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

