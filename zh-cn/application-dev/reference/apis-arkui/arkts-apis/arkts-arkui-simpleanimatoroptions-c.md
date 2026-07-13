# SimpleAnimatorOptions

animator简易动画参数对象。与AnimatorOptions相比，部分动画参数有默认值，可不设置。

**起始版本：** 18

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## constructor

```TypeScript
constructor(begin: number, end: number)
```

SimpleAnimatorOptions的构造函数。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本18开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| begin | number | 是 | 动画插值起点。 |
| end | number | 是 | 动画插值终点。 |

**示例：**

完整示例请参考[基于ArkTS扩展的声明式开发范式](#基于arkts扩展的声明式开发范式)。

```TypeScript
import { AnimatorResult, SimpleAnimatorOptions } from '@kit.ArkUI';

@Entry
@Component
struct AnimatorTest {
  private animatorResult: AnimatorResult | undefined = undefined;
  options: SimpleAnimatorOptions = new SimpleAnimatorOptions(100, 200); // 动画插值过程从100到200，其余动画参数使用默认值。

  create() {
    this.animatorResult = this.getUIContext().createAnimator(this.options);
  }

  build() {
    // ......
  }
}

```

## delay

```TypeScript
delay(delay: number): SimpleAnimatorOptions
```

设置animator动画播放时延。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本18开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| delay | number | 是 | 设置animator动画播放时延，单位毫秒，设置为0时，表示不延时。设置为负数时动画提前播放，如果提前播放的时长大于动画总时长，动画直接过渡到终点。<br/>默认值：0 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| SimpleAnimatorOptions | Animator简易动画参数对象。 |

**示例：**

完整示例请参考[基于ArkTS扩展的声明式开发范式](#基于arkts扩展的声明式开发范式)。

```TypeScript
import { AnimatorResult, SimpleAnimatorOptions } from '@kit.ArkUI';

@Entry
@Component
struct AnimatorTest {
  private animatorResult: AnimatorResult | undefined = undefined;
  options: SimpleAnimatorOptions = new SimpleAnimatorOptions(100, 200).delay(500);

  create() {
    this.animatorResult = this.getUIContext().createAnimator(this.options);
  }

  build() {
    // ......
  }
}

```

## direction

```TypeScript
direction(direction: PlayMode): SimpleAnimatorOptions
```

设置animator动画播放方向。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本18开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| direction | PlayMode | 是 | 设置animator动画播放方向。<br/>默认值：PlayMode.Normal |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| SimpleAnimatorOptions | Animator简易动画参数对象。 |

## duration

```TypeScript
duration(duration: number): SimpleAnimatorOptions
```

设置animator动画时长。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本18开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| duration | number | 是 | 设置动画时长，单位毫秒。<br/>默认值：1000 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| SimpleAnimatorOptions | Animator简易动画参数对象。 |

**示例：**

完整示例请参考[基于ArkTS扩展的声明式开发范式](#基于arkts扩展的声明式开发范式)。

```TypeScript
import { AnimatorResult, SimpleAnimatorOptions } from '@kit.ArkUI';

@Entry
@Component
struct AnimatorTest {
  private animatorResult: AnimatorResult | undefined = undefined;
  options: SimpleAnimatorOptions = new SimpleAnimatorOptions(100, 200).duration(500);

  create() {
    this.animatorResult = this.getUIContext().createAnimator(this.options);
  }

  build() {
    // ......
  }
}

```

## easing

```TypeScript
easing(curve: string): SimpleAnimatorOptions
```

设置animator动画插值曲线。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本18开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| curve | string | 是 | 设置animator动画插值曲线，具体说明参考[AnimatorOptions](arkts-arkui-animatoroptions-i.md)。<br/>默认值：“ease” |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| SimpleAnimatorOptions | Animator简易动画参数对象。 |

**示例：**

完整示例请参考[基于ArkTS扩展的声明式开发范式](#基于arkts扩展的声明式开发范式)。

```TypeScript
import { AnimatorResult, SimpleAnimatorOptions } from '@kit.ArkUI';

@Entry
@Component
struct AnimatorTest {
  private animatorResult: AnimatorResult | undefined = undefined;
  options: SimpleAnimatorOptions = new SimpleAnimatorOptions(100, 200).easing("ease-in");

  create() {
    this.animatorResult = this.getUIContext().createAnimator(this.options);
  }

  build() {
    // ......
  }
}

```

## fill

```TypeScript
fill(fillMode: FillMode): SimpleAnimatorOptions
```

设置animator动画填充方式。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本18开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| fillMode | FillMode | 是 | 设置animator动画填充方式，影响动画delay期间和结束时的表现。<br/>默认值：FillMode.Forwards |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| SimpleAnimatorOptions | Animator简易动画参数对象。 |

## iterations

```TypeScript
iterations(iterations: number): SimpleAnimatorOptions
```

设置animator动画播放次数。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本18开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| iterations | number | 是 | 设置animator动画播放次数，设置为0时不播放，设置为-1时无限次播放。<br/>默认值：1 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| SimpleAnimatorOptions | Animator简易动画参数对象。 |

**示例：**

完整示例请参考[基于ArkTS扩展的声明式开发范式](#基于arkts扩展的声明式开发范式)。

```TypeScript
import { AnimatorResult, SimpleAnimatorOptions } from '@kit.ArkUI';

@Entry
@Component
struct AnimatorTest {
  private animatorResult: AnimatorResult | undefined = undefined;
  options: SimpleAnimatorOptions = new SimpleAnimatorOptions(100, 200).iterations(3);

  create() {
    this.animatorResult = this.getUIContext().createAnimator(this.options);
  }

  build() {
    // ......
  }
}

```

