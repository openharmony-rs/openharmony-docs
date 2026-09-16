# SimpleAnimatorOptions

animator简易动画参数对象。与AnimatorOptions相比，duration、easing、delay、fill、direction、iterations等动画参数有默认值，可不设置。

**起始版本：** 18

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { Animator, AnimatorOptions, AnimatorResult, SimpleAnimatorOptions } from '@kit.ArkUI';
```

## constructor

```TypeScript
constructor(begin: number, end: number)
```

创建SimpleAnimatorOptions实例，指定动画插值起点和终点。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| begin | number | 是 | 动画插值起点。<br>**说明：** 会影响[onFrame](arkts-arkui-animator-animatorresult-i.md#onframe)回调的入参值，与end参数共同决定onFrame回调值的范围。 |
| end | number | 是 | 动画插值终点。<br>**说明：** 会影响[onFrame](arkts-arkui-animator-animatorresult-i.md#onframe)回调的入参值，与begin参数共同决定onFrame回调值的范围。 |

**示例**

```TypeScript
完整示例请参考基于ArkTS扩展的声明式开发范式。
```

## delay

```TypeScript
delay(delay: number): SimpleAnimatorOptions
```

设置animator动画延时播放时长。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| delay | number | 是 | 设置animator动画播放时延，单位毫秒，设置为0时，表示不延时。设置为负数时动画提前播放，如果提前播放的时长大于动画总时长，动画直接过渡到终点。<br>默认值：0 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [SimpleAnimatorOptions](arkts-arkui-animator-simpleanimatoroptions-c.md) | 返回当前简易动画参数对象，支持链式调用以继续配置动画参数。 |

**示例**

```TypeScript
完整示例请参考基于ArkTS扩展的声明式开发范式。
```

## direction

```TypeScript
direction(direction: PlayMode): SimpleAnimatorOptions
```

设置animator动画播放模式。使用interpolating-spring曲线时，此设置无效，direction固定设置为PlayMode.Normal。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| direction | [PlayMode](arkts-arkui-playmode-e.md) | 是 | 设置animator动画播放方向。<br>PlayMode.Normal：动画正向循环播放。<br>PlayMode.Reverse：动画反向循环播放。<br>PlayMode.Alternate：动画交替循环播放，奇数次正向播放，偶数次反向播放。<br>PlayMode.AlternateReverse：动画反向交替循环播放，奇数次反向播放，偶数次正向播放。<br>默认值：PlayMode.Normal |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [SimpleAnimatorOptions](arkts-arkui-animator-simpleanimatoroptions-c.md) | 返回当前简易动画参数对象，支持链式调用以继续配置动画参数。 |

**示例**

```TypeScript
完整示例请参考基于ArkTS扩展的声明式开发范式。
```

## duration

```TypeScript
duration(duration: number): SimpleAnimatorOptions
```

设置animator动画时长。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| duration | number | 是 | 设置动画播放的时长，单位毫秒。<br>默认值：1000 <br>**说明：** 使用interpolating-spring曲线时，duration不生效，由弹簧参数决定。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [SimpleAnimatorOptions](arkts-arkui-animator-simpleanimatoroptions-c.md) | 返回当前简易动画参数对象，支持链式调用以继续配置动画参数。 |

**示例**

```TypeScript
完整示例请参考基于ArkTS扩展的声明式开发范式。
```

## easing

```TypeScript
easing(curve: string): SimpleAnimatorOptions
```

设置animator动画插值曲线。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| curve | string | 是 | 设置animator动画插值曲线，具体说明参考[AnimatorOptions](arkts-arkui-animator-animatoroptions-i.md)。<br>默认值：“ease” |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [SimpleAnimatorOptions](arkts-arkui-animator-simpleanimatoroptions-c.md) | 返回当前简易动画参数对象，支持链式调用以继续配置动画参数。 |

**示例**

```TypeScript
完整示例请参考基于ArkTS扩展的声明式开发范式。
```

## fill

```TypeScript
fill(fillMode: FillMode): SimpleAnimatorOptions
```

设置animator动画填充方式。使用interpolating-spring曲线时，此设置无效，fill固定设置为FillMode.Forwards。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| fillMode | [FillMode](arkts-arkui-fillmode-e.md) | 是 | 设置animator动画填充方式，影响动画delay期间和结束时的表现。使用interpolating-spring曲线时，fill设置无效，固定设置为FillMode.Forwards。<br>默认值：FillMode.Forwards |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [SimpleAnimatorOptions](arkts-arkui-animator-simpleanimatoroptions-c.md) | 返回当前简易动画参数对象，支持链式调用以继续配置动画参数。 |

**示例**

```TypeScript
完整示例请参考基于ArkTS扩展的声明式开发范式。
```

## iterations

```TypeScript
iterations(iterations: number): SimpleAnimatorOptions
```

设置animator动画播放次数。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| iterations | number | 是 | 设置animator动画播放次数，设置为0时不播放，设置为-1时无限次播放，设置大于0时为播放次数。<br>**说明：** 设置为除-1外其他负数视为无效取值，无效取值动画默认播放1次。<br>默认值：1 <br>使用interpolating-spring曲线时，iterations设置无效，固定设置为1。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [SimpleAnimatorOptions](arkts-arkui-animator-simpleanimatoroptions-c.md) | 返回当前简易动画参数对象，支持链式调用以继续配置动画参数。 |

**示例**

```TypeScript
完整示例请参考基于ArkTS扩展的声明式开发范式。
```
