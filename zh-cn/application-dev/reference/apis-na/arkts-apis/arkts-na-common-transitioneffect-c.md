# TransitionEffect

定义TransitionEffect类指定转场效果。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare class TransitionEffect--><!--Device-unnamed-export declare class TransitionEffect-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## animation

```TypeScript
animation(value: AnimateParam): TransitionEffect
```

指定该TransitionEffect的动画参数。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-TransitionEffect-animation(value: AnimateParam): TransitionEffect--><!--Device-TransitionEffect-animation(value: AnimateParam): TransitionEffect-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [AnimateParam](arkts-na-common-animateparam-i.md) | 是 | 动画参数。&lt;/br&gt;该参数只用来指定动画参数，其入参AnimateParam的onFinish回调不生效。&lt;/br&gt;如果通过combine进行 TransitionEffect的组合，前一TransitionEffect的动画参数也可用于后一TransitionEffect。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [TransitionEffect](arkts-na-common-transitioneffect-c.md) | 当前动画效果。 |

## asymmetric

```TypeScript
static asymmetric(appear: TransitionEffect, disappear: TransitionEffect): TransitionEffect
```

设置非对称的转场效果。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-TransitionEffect-static asymmetric(appear: TransitionEffect, disappear: TransitionEffect): TransitionEffect--><!--Device-TransitionEffect-static asymmetric(appear: TransitionEffect, disappear: TransitionEffect): TransitionEffect-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| appear | [TransitionEffect](arkts-na-common-transitioneffect-c.md) | 是 | 指定出现的转场效果。<br/>如不通过asymmetric函数构造TransitionEffect，则表明该效果在组件出现和消失时均生效。 |
| disappear | [TransitionEffect](arkts-na-common-transitioneffect-c.md) | 是 | 指定消失的转场效果。<br/>如不通过asymmetric函数构造TransitionEffect，则表明该效果在组件出现和消失时均生效。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [TransitionEffect](arkts-na-common-transitioneffect-c.md) | 当前动画非对称的转场效果。 |

## combine

```TypeScript
combine(transitionEffect: TransitionEffect): TransitionEffect
```

对TransitionEffect进行链式组合，以形成包含多种转场效果的TransitionEffect。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-TransitionEffect-combine(transitionEffect: TransitionEffect): TransitionEffect--><!--Device-TransitionEffect-combine(transitionEffect: TransitionEffect): TransitionEffect-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| transitionEffect | [TransitionEffect](arkts-na-common-transitioneffect-c.md) | 是 | 被组合的过渡效果。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [TransitionEffect](arkts-na-common-transitioneffect-c.md) | 组合过渡效应。 |

## constructor('identity' | 'slideSwitch')

```TypeScript
constructor(type: 'identity' | 'slideSwitch', effect: undefined)
```

构造TransitionEffect对象。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-TransitionEffect-constructor(type: 'identity' | 'slideSwitch', effect: undefined)--><!--Device-TransitionEffect-constructor(type: 'identity' | 'slideSwitch', effect: undefined)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'identity' \| 'slideSwitch' | 是 | 转场类型。 |
| effect | undefined | 是 | 转场参数。 |

## constructor('opacity')

```TypeScript
constructor(type: 'opacity', effect: double)
```

构造TransitionEffect对象。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-TransitionEffect-constructor(type: 'opacity', effect: double)--><!--Device-TransitionEffect-constructor(type: 'opacity', effect: double)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'opacity' | 是 | 转场类型。 |
| effect | double | 是 | 转场参数。 |

## constructor('move')

```TypeScript
constructor(type: 'move', effect: TransitionEdge)
```

构造TransitionEffect对象。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-TransitionEffect-constructor(type: 'move', effect: TransitionEdge)--><!--Device-TransitionEffect-constructor(type: 'move', effect: TransitionEdge)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'move' | 是 | 转场类型。 |
| effect | [TransitionEdge](arkts-na-common-transitionedge-e.md) | 是 | 转场参数。 |

## constructor('translate')

```TypeScript
constructor(type: 'translate', effect: TranslateOptions)
```

构造TransitionEffect对象。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-TransitionEffect-constructor(type: 'translate', effect: TranslateOptions)--><!--Device-TransitionEffect-constructor(type: 'translate', effect: TranslateOptions)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'translate' | 是 | 转场类型。 |
| effect | [TranslateOptions](arkts-na-common-translateoptions-i.md) | 是 | 转场参数。 |

## constructor('rotate')

```TypeScript
constructor(type: 'rotate', effect: RotateOptions)
```

构造TransitionEffect对象。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-TransitionEffect-constructor(type: 'rotate', effect: RotateOptions)--><!--Device-TransitionEffect-constructor(type: 'rotate', effect: RotateOptions)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'rotate' | 是 | 转场类型。 |
| effect | [RotateOptions](arkts-na-common-rotateoptions-i.md) | 是 | 转场参数。 |

## constructor('scale')

```TypeScript
constructor(type: 'scale', effect: ScaleOptions)
```

构造TransitionEffect对象。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-TransitionEffect-constructor(type: 'scale', effect: ScaleOptions)--><!--Device-TransitionEffect-constructor(type: 'scale', effect: ScaleOptions)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'scale' | 是 | 转场类型。 |
| effect | [ScaleOptions](arkts-na-common-scaleoptions-i.md) | 是 | 转场参数。 |

## constructor('asymmetric')

```TypeScript
constructor(type: 'asymmetric', effect: AsymmetricTransitionOption)
```

构造TransitionEffect对象。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-TransitionEffect-constructor(type: 'asymmetric', effect: AsymmetricTransitionOption)--><!--Device-TransitionEffect-constructor(type: 'asymmetric', effect: AsymmetricTransitionOption)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'asymmetric' | 是 | 转场类型。 |
| effect | [AsymmetricTransitionOption](arkts-na-common-asymmetrictransitionoption-i.md) | 是 | 转场参数。 |

## move

```TypeScript
static move(edge: TransitionEdge): TransitionEffect
```

设置组件转场时从屏幕边缘滑入和滑出的效果。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-TransitionEffect-static move(edge: TransitionEdge): TransitionEffect--><!--Device-TransitionEffect-static move(edge: TransitionEdge): TransitionEffect-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| edge | [TransitionEdge](arkts-na-common-transitionedge-e.md) | 是 | 组件转场时从屏幕边缘滑入和滑出的效果，本质为平移效果，为插入时起点和删除时终点的值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [TransitionEffect](arkts-na-common-transitioneffect-c.md) | 当前动画从屏幕边缘滑入和滑出的效果。 |

## opacity

```TypeScript
static opacity(alpha: double): TransitionEffect
```

设置组件转场时的透明度效果。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-TransitionEffect-static opacity(alpha: double): TransitionEffect--><!--Device-TransitionEffect-static opacity(alpha: double): TransitionEffect-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| alpha | double | 是 | 组件转场时的透明度效果，为插入时起点和删除时终点的值。<br/>取值范围：[0, 1]<br/>**说明：** <br/>设置小于0的非法值按0处理，大于1的非法值按1处理。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [TransitionEffect](arkts-na-common-transitioneffect-c.md) | 当前动画透明度效果。 |

## rotate

```TypeScript
static rotate(options: RotateOptions): TransitionEffect
```

设置组件转场时的旋转效果。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-TransitionEffect-static rotate(options: RotateOptions): TransitionEffect--><!--Device-TransitionEffect-static rotate(options: RotateOptions): TransitionEffect-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [RotateOptions](arkts-na-common-rotateoptions-i.md) | 是 | 组件转场时的旋转效果，为插入时起点和删除时终点的值。<br/>-x：横向的旋转向量分量。<br/>-y：纵向的旋转向量分量。<br/>-z：竖向的旋转向量分 量。<br/>- centerX、centerY指旋转中心点，centerX和centerY默认值是"50%"，即默认以组件的中心点为旋转中心点。<br/>- 中心点为(0, 0)代表组件的左上角。<br/>- centerZ指z轴锚点，即3D旋转中心点的z轴分量，centerZ默认值是0。<br/>-perspective指视距，不支持perspective属性做转场动画。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [TransitionEffect](arkts-na-common-transitioneffect-c.md) | 当前动画旋转效果。 |

## scale

```TypeScript
static scale(options: ScaleOptions): TransitionEffect
```

设置组件转场时的缩放效果。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-TransitionEffect-static scale(options: ScaleOptions): TransitionEffect--><!--Device-TransitionEffect-static scale(options: ScaleOptions): TransitionEffect-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [ScaleOptions](arkts-na-common-scaleoptions-i.md) | 是 | 组件转场时的缩放效果，为插入时起点和删除时终点的值。设置的缩放值在组件当前的scale属性上进行叠加，如组件当前scale值为0.8，当转场缩放值设置为0.5 时，组件入场动画的缩放值将从0.4开始执行。<br/>-x：横向放大倍数（或缩小比例）。<br/>-y：纵向放大倍数（或缩小比例）。<br/>-z：当前为二维显示，该参数无效。<br/>- centerX、 centerY指缩放中心点，centerX和centerY默认值是"50%"，即默认以组件的中心点为缩放中心点。<br/>- 中心点为(0, 0)代表组件的左上角。<br>**说明：** <br>设置centerX、 centerY为非法字符串时（例如，"illegalString"），默认值为"0"。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [TransitionEffect](arkts-na-common-transitioneffect-c.md) | 当前动画缩放效果。 |

## translate

```TypeScript
static translate(options: TranslateOptions): TransitionEffect
```

设置组件转场时的平移效果。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-TransitionEffect-static translate(options: TranslateOptions): TransitionEffect--><!--Device-TransitionEffect-static translate(options: TranslateOptions): TransitionEffect-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [TranslateOptions](arkts-na-common-translateoptions-i.md) | 是 | 组件转场时的平移效果，为插入时起点和删除时终点的值。<br/>-x：横向的平移距离。<br/>-y：纵向的平移距离。<br/>-z：竖向的平移距离。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [TransitionEffect](arkts-na-common-transitioneffect-c.md) | 当前动画平移效果。 |

