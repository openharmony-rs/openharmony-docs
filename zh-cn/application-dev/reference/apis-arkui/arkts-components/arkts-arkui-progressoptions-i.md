# ProgressOptions

进度条选项。

**起始版本：** 7

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
```

## style

```TypeScript
style?: ProgressStyle
```

指定进度条样式。从API version 7开始支持，从API version 8开始废弃。建议使用[type](arkts-arkui-progresstype-e.md)替代。默认值：ProgressStyle.Linear

**类型：** [ProgressStyle](arkts-arkui-progressstyle-e.md)

**起始版本：** 7

**废弃版本：** 8

**替代接口：** [type](#type)

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## total

```TypeScript
total?: number
```

指定进度总长。设置小于0的数值时置为100。默认值：100取值范围：(0, +∞)。

**类型：** number

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## type

```TypeScript
type?: Type
```

指定进度条类型。默认值：ProgressType.Linear  
**说明：** 不同的type需分别对应相应的[style](arkts-arkui-progress-attribute.md#style)属性设置，详细映射关系参考 [ProgressStyleMap](arkts-arkui-progressstylemap-i.md)。

**类型：** [Type](../../apis-arkts/arkts-apis/arkts-arkts-util-type-e.md)

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## value

```TypeScript
value: number
```

指定当前进度值。默认值：0取值范围：[0, total]，设置小于0的数值时置为0，设置大于total的数值时置为total，设置非法值时按默认值处理。

**类型：** number

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
