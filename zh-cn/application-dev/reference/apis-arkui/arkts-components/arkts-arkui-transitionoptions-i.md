# TransitionOptions

TransitionOptions通过指定结构体内的参数来指定转场效果。
> **说明：**  
>  
> 1. 当使用TransitionOptions类型的入参指定转场效果时，**必须**配合  
> [animateTo](../../../reference/apis-arkui/arkts-apis-uicontext-uicontext.md#animateto)使用才有动画效果，动效时长、曲线、延时跟随  
> animateTo中的配置。  
>  
> 2. 当使用TransitionOptions作为入参，且不指定除type外的任何参数时，此时相当于指定了透明度的转场效果。例如，指定{type: TransitionType.Insert}相当于指定了{type:  
> TransitionType.Insert, opacity: 0}的转场效果。而指定了具体效果时，则不会添加默认的透明度转场效果。

**起始版本：** 7

**废弃版本：** 10

**替代接口：** [TransitionEffect](arkts-arkui-transitioneffect-c.md)

<!--Device-unnamed-declare interface TransitionOptions--><!--Device-unnamed-declare interface TransitionOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## opacity

```TypeScript
opacity?: number
```

设置组件转场时的透明度效果，为插入时起点和删除时终点的值。

取值范围： [0, 1]

**说明：**

设置小于0的非法值时，按0处理；设置大于1的非法值时，按1处理。

**类型：** number

**起始版本：** 7

**废弃版本：** 10

**替代接口：** [opacity](arkts-arkui-transitioneffect-c.md#opacity)

<!--Device-TransitionOptions-opacity?: number--><!--Device-TransitionOptions-opacity?: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## rotate

```TypeScript
rotate?: RotateOptions
```

设置组件转场时的旋转效果，为插入时起点和删除时终点的值。

-x：横向的旋转向量分量。

-y：纵向的旋转向量分量。

-z：竖向的旋转向量分量。

- centerX、centerY指旋转中心点，centerX和centerY默认值是"50%"，即默认以组件的中心点为旋转中心点。

- 中心点为(0, 0)代表组件的左上角。

**类型：** RotateOptions

**起始版本：** 7

**废弃版本：** 10

**替代接口：** [rotate](arkts-arkui-transitioneffect-c.md#rotate)

<!--Device-TransitionOptions-rotate?: RotateOptions--><!--Device-TransitionOptions-rotate?: RotateOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## scale

```TypeScript
scale?: ScaleOptions
```

设置组件转场时的缩放效果，为插入时起点和删除时终点的值。

-x：横向放大倍数（或缩小比例）。

-y：纵向放大倍数（或缩小比例）。

-z：当前为二维显示，该参数无效 。

- centerX、centerY指缩放中心点，centerX和centerY默认值是"50%"，即默认以组件的中心点为缩放中心点。

- 中心点为(0, 0)代表组件的左上角。

**说明：**

设置centerX、centerY为非法字符串时（例如，"illegalString"），默认值为"0"。

**类型：** ScaleOptions

**起始版本：** 7

**废弃版本：** 10

**替代接口：** [scale](arkts-arkui-transitioneffect-c.md#scale)

<!--Device-TransitionOptions-scale?: ScaleOptions--><!--Device-TransitionOptions-scale?: ScaleOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## translate

```TypeScript
translate?: TranslateOptions
```

设置组件转场时的平移效果，为插入时起点和删除时终点的值。

-x：横向的平移距离。

-y：纵向的平移距离。

-z：竖向的平移距离。

**类型：** TranslateOptions

**起始版本：** 7

**废弃版本：** 10

**替代接口：** [translate](arkts-arkui-transitioneffect-c.md#translate)

<!--Device-TransitionOptions-translate?: TranslateOptions--><!--Device-TransitionOptions-translate?: TranslateOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## type

```TypeScript
type?: TransitionType
```

指定该转场样式生效的场景。

默认值：TransitionType.All

**说明：**

不指定type时默认为TransitionType.All，即插入删除都生效。

**类型：** TransitionType

**起始版本：** 7

**废弃版本：** 10

**替代接口：** [TransitionEffect](arkts-arkui-transitioneffect-c.md)

<!--Device-TransitionOptions-type?: TransitionType--><!--Device-TransitionOptions-type?: TransitionType-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

