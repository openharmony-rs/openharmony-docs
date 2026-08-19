# PopupBorderLinearGradient

Popup border LinearGradient

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare interface PopupBorderLinearGradient--><!--Device-unnamed-export declare interface PopupBorderLinearGradient-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## colors

```TypeScript
colors: Array<[ResourceColor | undefined, double]>
```

Sets the colors and positions of the gradient. When the color setting is undefined, use the default value Color.Black. The position setting ranges from 0 to 1.

**类型：** Array&lt;[ResourceColor \| undefined, double]&gt;

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PopupBorderLinearGradient-colors: Array<[ResourceColor | undefined, double]>--><!--Device-PopupBorderLinearGradient-colors: Array<[ResourceColor | undefined, double]>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## direction

```TypeScript
direction?: GradientDirection
```

direction: Direction of Linear Gradient.

**类型：** [GradientDirection](../../apis-arkui/arkts-apis/arkts-arkui-gradientdirection-e.md)

**默认值：** GradientDirection.Bottom

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PopupBorderLinearGradient-direction?: GradientDirection--><!--Device-PopupBorderLinearGradient-direction?: GradientDirection-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

