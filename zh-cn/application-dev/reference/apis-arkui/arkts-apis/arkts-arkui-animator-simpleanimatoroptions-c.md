# SimpleAnimatorOptions

animator简易动画参数对象。与AnimatorOptions相比，部分动画参数有默认值，可不设置。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare class SimpleAnimatorOptions--><!--Device-unnamed-export declare class SimpleAnimatorOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { Animator, AnimatorOptions, AnimatorResult, SimpleAnimatorOptions } from '@kit.ArkUI';
```

## constructor

```TypeScript
constructor(begin: double, end: double)
```

SimpleAnimatorOptions的构造函数。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SimpleAnimatorOptions-constructor(begin: double, end: double)--><!--Device-SimpleAnimatorOptions-constructor(begin: double, end: double)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| begin | double | 是 | 动画插值起点。 |
| end | double | 是 | 动画插值终点。 |

## delay

```TypeScript
delay(delay: int): SimpleAnimatorOptions
```

设置animator动画播放时延。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SimpleAnimatorOptions-delay(delay: int): SimpleAnimatorOptions--><!--Device-SimpleAnimatorOptions-delay(delay: int): SimpleAnimatorOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| delay | int | 是 | 设置animator动画播放时延，单位毫秒，设置为0时，表示不延时。设置为负数时动画提前播放，如果提前播放的时长大于动画总时长，动画直接过渡到终点，默认值：0。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [SimpleAnimatorOptions](arkts-arkui-animator-simpleanimatoroptions-c.md) | Animator简易动画参数对象。 |

## direction

```TypeScript
direction(direction: PlayMode): SimpleAnimatorOptions
```

设置animator动画播放方向。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SimpleAnimatorOptions-direction(direction: PlayMode): SimpleAnimatorOptions--><!--Device-SimpleAnimatorOptions-direction(direction: PlayMode): SimpleAnimatorOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| direction | [PlayMode](../../apis-na/arkts-apis/arkts-na-enums-playmode-e.md) | 是 | 设置animator动画播放方向，默认值：PlayMode.Normal。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [SimpleAnimatorOptions](arkts-arkui-animator-simpleanimatoroptions-c.md) | Animator简易动画参数对象。 |

## duration

```TypeScript
duration(duration: int): SimpleAnimatorOptions
```

设置animator动画时长。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SimpleAnimatorOptions-duration(duration: int): SimpleAnimatorOptions--><!--Device-SimpleAnimatorOptions-duration(duration: int): SimpleAnimatorOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| duration | int | 是 | 设置动画时长，单位毫秒，默认值：1000。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [SimpleAnimatorOptions](arkts-arkui-animator-simpleanimatoroptions-c.md) | Animator简易动画参数对象。 |

## easing

```TypeScript
easing(curve: string): SimpleAnimatorOptions
```

设置animator动画插值曲线。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SimpleAnimatorOptions-easing(curve: string): SimpleAnimatorOptions--><!--Device-SimpleAnimatorOptions-easing(curve: string): SimpleAnimatorOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| curve | string | 是 | 设置animator动画插值曲线，默认值：“ease”。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [SimpleAnimatorOptions](arkts-arkui-animator-simpleanimatoroptions-c.md) | Animator简易动画参数对象。 |

## fill

```TypeScript
fill(fillMode: FillMode): SimpleAnimatorOptions
```

设置animator动画填充方式。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SimpleAnimatorOptions-fill(fillMode: FillMode): SimpleAnimatorOptions--><!--Device-SimpleAnimatorOptions-fill(fillMode: FillMode): SimpleAnimatorOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| fillMode | [FillMode](../../apis-na/arkts-apis/arkts-na-enums-fillmode-e.md) | 是 | 设置animator动画填充方式，影响动画delay期间和结束时的表现，默认值：FillMode.Forwards。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [SimpleAnimatorOptions](arkts-arkui-animator-simpleanimatoroptions-c.md) | Animator简易动画参数对象。 |

## iterations

```TypeScript
iterations(iterations: int): SimpleAnimatorOptions
```

设置animator动画播放次数。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SimpleAnimatorOptions-iterations(iterations: int): SimpleAnimatorOptions--><!--Device-SimpleAnimatorOptions-iterations(iterations: int): SimpleAnimatorOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| iterations | int | 是 | 设置animator动画播放次数，设置为0时不播放，设置为-1时无限次播放，默认值：1。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [SimpleAnimatorOptions](arkts-arkui-animator-simpleanimatoroptions-c.md) | Animator简易动画参数对象。 |

