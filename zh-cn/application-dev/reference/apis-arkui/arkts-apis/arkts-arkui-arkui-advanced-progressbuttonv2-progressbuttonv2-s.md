# ProgressButtonV2

文本下载按钮，可显示具体的下载进度。 该组件基于\_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_实现，相较于\_\_\_MD\_LINK\_DESC\_USD\_1\_\_\_，状态管理（V2）增强了对数据对象的深度观察与管理能力，不再局限于组件层级。借助状态管理（V2），开发者可以通过该组件更灵活地控制文本下载按钮的数据和状态，实现更高效的用户界面刷新。 设备行为差异：该接口在Wearable设备上使用时，应用程序运行异常，异常信息中提示接口未定义，在其他设备中可正常调用。 > **说明：** > > - 如果ProgressButtonV2设置\_\_\_MD\_LINK\_DESC\_USD\_2\_\_\_和\_\_\_MD\_LINK\_DESC\_USD\_3\_\_\_，编译工具链会额外生成节点\_\_Common\_\_，并将通用属性或通用事件挂载在\_\_Common\_\_上，而不是直接应用到ProgressButtonV2本身。这可能导致开发者设置的通用属性或通用事件不生效或不符合预期，因此，不建议ProgressButtonV2设置通用属性和通用事件。

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**装饰器类型：** @ComponentV2

<!--Device-unnamed-export declare struct ProgressButtonV2--><!--Device-unnamed-export declare struct ProgressButtonV2-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## colorOptions

```TypeScript
@Param colorOptions?: ProgressButtonV2Color
```

下载按钮颜色选项。

**类型：** ProgressButtonV2Color

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**装饰器类型：** @Param

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-ProgressButtonV2-@Param colorOptions?: ProgressButtonV2Color--><!--Device-ProgressButtonV2-@Param colorOptions?: ProgressButtonV2Color-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## content

```TypeScript
@Param readonly content: ResourceStr
```

下载按钮的文本。

**类型：** ResourceStr

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**装饰器类型：** @Require、@Param

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-ProgressButtonV2-@Param readonly content: ResourceStr--><!--Device-ProgressButtonV2-@Param readonly content: ResourceStr-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## isEnabled

```TypeScript
@Param readonly isEnabled: boolean
```

下载按钮是否可以点击。\_\_\_HTML\_TAG\_DESC\_USD\_0\_\_\_ true：可以点击。\_\_\_HTML\_TAG\_DESC\_USD\_1\_\_\_ false：不可点击。

**类型：** boolean

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**装饰器类型：** @Param

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-ProgressButtonV2-@Param readonly isEnabled: boolean--><!--Device-ProgressButtonV2-@Param readonly isEnabled: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onClicked

```TypeScript
@Param readonly onClicked: ClickCallback
```

下载按钮的点击回调。

**类型：** ClickCallback

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**装饰器类型：** @Param

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-ProgressButtonV2-@Param readonly onClicked: ClickCallback--><!--Device-ProgressButtonV2-@Param readonly onClicked: ClickCallback-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## progress

```TypeScript
@Param readonly progress: number
```

下载按钮的当前进度值。\_\_\_HTML\_TAG\_DESC\_USD\_0\_\_\_取值范围：[0,100]。设置小于0的数值时置为0，设置大于100的数值置为100。\_\_\_HTML\_TAG\_DESC\_USD\_1\_\_\_默认值：0

**类型：** number

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**装饰器类型：** @Require、@Param

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-ProgressButtonV2-@Param readonly progress: number--><!--Device-ProgressButtonV2-@Param readonly progress: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## progressButtonRadius

```TypeScript
@Param progressButtonRadius?: LengthMetrics
```

下载按钮的圆角（不支持百分比设置）。\_\_\_HTML\_TAG\_DESC\_USD\_0\_\_\_取值范围：[0, height/2]\_\_\_HTML\_TAG\_DESC\_USD\_1\_\_\_默认值：height/2\_\_\_HTML\_TAG\_DESC\_USD\_2\_\_\_设置非法数值时，按照默认值处理。

**类型：** LengthMetrics

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**装饰器类型：** @Param

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-ProgressButtonV2-@Param progressButtonRadius?: LengthMetrics--><!--Device-ProgressButtonV2-@Param progressButtonRadius?: LengthMetrics-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## progressButtonWidth

```TypeScript
@Param @Once progressButtonWidth?: LengthMetrics
```

下载按钮的宽度。\_\_\_HTML\_TAG\_DESC\_USD\_0\_\_\_默认值：44vp

**类型：** LengthMetrics

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**装饰器类型：** @Param

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-ProgressButtonV2-@Param @Once progressButtonWidth?: LengthMetrics--><!--Device-ProgressButtonV2-@Param @Once progressButtonWidth?: LengthMetrics-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

