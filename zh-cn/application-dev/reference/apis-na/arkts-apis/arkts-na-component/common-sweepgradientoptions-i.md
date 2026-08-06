# SweepGradientOptions

Defines the options of sweep gradient.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare interface SweepGradientOptions--><!--Device-unnamed-export declare interface SweepGradientOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## center

```TypeScript
center: [
        Length,
        Length
    ]
```

Defines center point for angle gradient. Anonymous Object Rectification.

**类型：** [         Length,         Length     ]

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SweepGradientOptions-center: [        Length,        Length    ]--><!--Device-SweepGradientOptions-center: [        Length,        Length    ]-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## colors

```TypeScript
colors: Array<[
        ResourceColor,
        double
    ]>
```

Defines color description for gradients. Anonymous Object Rectification.

**类型：** Array&lt;[         ResourceColor,         double     ]&gt;

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SweepGradientOptions-colors: Array<[        ResourceColor,        double    ]>--><!--Device-SweepGradientOptions-colors: Array<[        ResourceColor,        double    ]>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## end

```TypeScript
end?: double | string
```

Defines end point of angle gradient. Anonymous Object Rectification.

**类型：** double \| string

**默认值：** 0

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SweepGradientOptions-end?: double | string--><!--Device-SweepGradientOptions-end?: double | string-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## metricsColors

```TypeScript
metricsColors?: Array<[
        ColorMetrics,
        double
    ]>
```

Defines color description in ColorMetrics format for gradients. This parameter takes precedence over colors parameter.

**类型：** Array&lt;[         ColorMetrics,         double     ]&gt;

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SweepGradientOptions-metricsColors?: Array<[        ColorMetrics,        double    ]>--><!--Device-SweepGradientOptions-metricsColors?: Array<[        ColorMetrics,        double    ]>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## repeating

```TypeScript
repeating?: boolean
```

Defines gradient colors with repeated coloring. Anonymous Object Rectification.

**类型：** boolean

**默认值：** false

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SweepGradientOptions-repeating?: boolean--><!--Device-SweepGradientOptions-repeating?: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## rotation

```TypeScript
rotation?: double | string
```

Defines the rotation angle of the gradient. Anonymous Object Rectification.

**类型：** double \| string

**默认值：** 0

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SweepGradientOptions-rotation?: double | string--><!--Device-SweepGradientOptions-rotation?: double | string-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## start

```TypeScript
start?: double | string
```

Defines the starting point of angle gradient. Anonymous Object Rectification.

**类型：** double \| string

**默认值：** 0

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SweepGradientOptions-start?: double | string--><!--Device-SweepGradientOptions-start?: double | string-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

