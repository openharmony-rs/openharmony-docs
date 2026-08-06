# BindOptions

半模态、全模态的公共配置接口。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare interface BindOptions--><!--Device-unnamed-export declare interface BindOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## backgroundColor

```TypeScript
backgroundColor?: ResourceColor
```

半模态页面的背板颜色。 默认值：Color.White。

**类型：** ResourceColor

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-BindOptions-backgroundColor?: ResourceColor--><!--Device-BindOptions-backgroundColor?: ResourceColor-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onAppear

```TypeScript
onAppear?: VoidCallback
```

半模态页面显示（动画结束后）回调函数。

**类型：** VoidCallback

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-BindOptions-onAppear?: VoidCallback--><!--Device-BindOptions-onAppear?: VoidCallback-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onDisappear

```TypeScript
onDisappear?: VoidCallback
```

半模态页面回退（动画结束后）回调函数。

**类型：** VoidCallback

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-BindOptions-onDisappear?: VoidCallback--><!--Device-BindOptions-onDisappear?: VoidCallback-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onWillAppear

```TypeScript
onWillAppear?: VoidCallback
```

半模态页面显示（动画开始前）回调函数。

**类型：** VoidCallback

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-BindOptions-onWillAppear?: VoidCallback--><!--Device-BindOptions-onWillAppear?: VoidCallback-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onWillDisappear

```TypeScript
onWillDisappear?: VoidCallback
```

半模态页面回退（动画开始前）回调函数。 **说明：** 不允许在onWillDisappear函数中修改状态变量，可能会导致组件行为不稳定。

**类型：** VoidCallback

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-BindOptions-onWillDisappear?: VoidCallback--><!--Device-BindOptions-onWillDisappear?: VoidCallback-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

