# ProgressOptions

进度条选项。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-unnamed-export declare interface ProgressOptions--><!--Device-unnamed-export declare interface ProgressOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## total

```TypeScript
total?: double
```

指定进度总长。设置小于等于0的数值时置为100。 默认值：100 。

**类型：** double

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ProgressOptions-total?: double--><!--Device-ProgressOptions-total?: double-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## type

```TypeScript
type?: ProgressType
```

指定进度条类型。 默认值：ProgressType.Linear。

**类型：** [ProgressType](arkts-na-progress-progresstype-e.md)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ProgressOptions-type?: ProgressType--><!--Device-ProgressOptions-type?: ProgressType-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## value

```TypeScript
value: double
```

指定当前进度值。设置小于0的数值时置为0，设置大于total的数值时置为total。 取值范围：[0, total]。

**类型：** double

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ProgressOptions-value: double--><!--Device-ProgressOptions-value: double-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

