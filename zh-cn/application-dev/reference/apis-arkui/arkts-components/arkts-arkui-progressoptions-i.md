# ProgressOptions

进度条选项。

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

<!--Device-unnamed-declare interface ProgressOptions<Type extends keyof ProgressStyleMap>--><!--Device-unnamed-declare interface ProgressOptions<Type extends keyof ProgressStyleMap>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## style

```TypeScript
style?: ProgressStyle
```

指定进度条样式。 从API version 7开始支持，从API version 8开始废弃。建议使用[type]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_替代。 默认值：ProgressStyle.Linear

**类型：** ProgressStyle

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** 8

**替代接口：** [type](arkts-arkui-progressoptions-i.md#type)

<!--Device-ProgressOptions-style?: ProgressStyle--><!--Device-ProgressOptions-style?: ProgressStyle-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## total

```TypeScript
total?: number
```

指定进度总长。设置小于0的数值时置为100。 默认值：100 取值范围：(0, +∞)。

**类型：** number

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-ProgressOptions-total?: number--><!--Device-ProgressOptions-total?: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## type

```TypeScript
type?: Type
```

指定进度条类型。 默认值：ProgressType.Linear **说明：** 不同的type需分别对应相应的[style]\_\_\_JSDOC\_LINK\_DESC\_USD\_1\_\_\_属性设置，详细映射关系参考 \_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_。

**类型：** Type

**起始版本：** 8

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为8。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-ProgressOptions-type?: Type--><!--Device-ProgressOptions-type?: Type-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## value

```TypeScript
value: number
```

指定当前进度值。 默认值：0 取值范围：[0, total]，设置小于0的数值时置为0，设置大于total的数值时置为total，设置非法值时按默认值处理。

**类型：** number

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-ProgressOptions-value: number--><!--Device-ProgressOptions-value: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

