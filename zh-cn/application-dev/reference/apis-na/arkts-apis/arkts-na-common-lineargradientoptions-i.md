# LinearGradientOptions

Defines the options of linear gradient.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare interface LinearGradientOptions--><!--Device-unnamed-export declare interface LinearGradientOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## angle

```TypeScript
angle?: double | string
```

Defines starting angle of linear gradient. Anonymous Object Rectification.

**类型：** double \| string

**默认值：** 180

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-LinearGradientOptions-angle?: double | string--><!--Device-LinearGradientOptions-angle?: double | string-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## colors

```TypeScript
colors: Array<[
        ResourceColor,
        double
    ]>
```

Defines color description for gradients. Anonymous Object Rectification.

**类型：** Array&lt;[         ResourceColor, double     ]&gt;

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-LinearGradientOptions-colors: Array<[        ResourceColor,        double    ]>--><!--Device-LinearGradientOptions-colors: Array<[        ResourceColor,        double    ]>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## direction

```TypeScript
direction?: GradientDirection
```

Defines the direction of linear gradient. Anonymous Object Rectification.

**类型：** [GradientDirection](../../apis-arkui/arkts-apis/arkts-arkui-gradientdirection-e.md)

**默认值：** GradientDirection.Bottom

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-LinearGradientOptions-direction?: GradientDirection--><!--Device-LinearGradientOptions-direction?: GradientDirection-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## repeating

```TypeScript
repeating?: boolean
```

Defines gradient colors with repeated coloring. Anonymous Object Rectification.

**类型：** boolean

**默认值：** false

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-LinearGradientOptions-repeating?: boolean--><!--Device-LinearGradientOptions-repeating?: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

