# AnimatorResult

定义Animator结果接口。

**起始版本：** 6

<!--Device-unnamed-export interface AnimatorResult--><!--Device-unnamed-export interface AnimatorResult-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { AnimatorOptions, SimpleAnimatorOptions, AnimatorResult } from '@kit.ArkUI';
```

<a id="cancel"></a>
## cancel

```TypeScript
cancel(): void
```

取消动画，会触发[onCancel](docroot://reference/apis-arkui/js-apis-animator.md#属性)回调。此接口和[finish](arkts-arkui-animator-animatorresult-i.md#finish-1)接口功能上没有区别，仅触发的回调不同，建议使用finish接口结束动画。

**起始版本：** 6

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-AnimatorResult-cancel(): void--><!--Device-AnimatorResult-cancel(): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**示例：**

完整示例请参考[基于ArkTS扩展的声明式开发范式](#基于arkts扩展的声明式开发范式)。

```TypeScript
animator.cancel();

```

<a id="finish"></a>
## finish

```TypeScript
finish(): void
```

结束动画，会触发[onFinish](docroot://reference/apis-arkui/js-apis-animator.md#属性)回调。

**起始版本：** 6

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-AnimatorResult-finish(): void--><!--Device-AnimatorResult-finish(): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**示例：**

完整示例请参考[基于ArkTS扩展的声明式开发范式](#基于arkts扩展的声明式开发范式)。

```TypeScript
animator.finish();

```

<a id="pause"></a>
## pause

```TypeScript
pause(): void
```

暂停动画。

**起始版本：** 6

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-AnimatorResult-pause(): void--><!--Device-AnimatorResult-pause(): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**示例：**

完整示例请参考[基于ArkTS扩展的声明式开发范式](#基于arkts扩展的声明式开发范式)。

```TypeScript
animator.pause();

```

<a id="play"></a>
## play

```TypeScript
play(): void
```

启动动画。动画会保留上一次的播放状态，比如播放状态设置reverse后，再次播放会保留reverse的播放状态。

**起始版本：** 6

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-AnimatorResult-play(): void--><!--Device-AnimatorResult-play(): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**示例：**

完整示例请参考[基于ArkTS扩展的声明式开发范式](#基于arkts扩展的声明式开发范式)。

```TypeScript
animator.play();

```

<a id="reset"></a>
## reset

```TypeScript
reset(options: AnimatorOptions): void
```

重置当前animator动画参数。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-AnimatorResult-reset(options: AnimatorOptions): void--><!--Device-AnimatorResult-reset(options: AnimatorOptions): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [AnimatorOptions](arkts-arkui-animator-animatoroptions-i.md) | 是 | 定义动画选项。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:<br> 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameters types.<br> 3. Parameter verification failed. |
| [100001](../errorcode-internal.md#100001-接口调用异常错误码) | The specified page is not found or the object property list is not obtained. |

**示例：**

```TypeScript
import { AnimatorResult } from '@kit.ArkUI';

@Entry
@Component
struct AnimatorTest {
  private animatorResult: AnimatorResult | undefined = undefined;

  create() {
    this.animatorResult = this.getUIContext().createAnimator({
      duration: 1500,
      easing: "friction",
      delay: 0,
      fill: "forwards",
      direction: "normal",
      iterations: 3,
      begin: 200.0,
      end: 400.0
    })
    this.animatorResult.reset({
      duration: 1500,
      easing: "friction",
      delay: 0,
      fill: "forwards",
      direction: "normal",
      iterations: 5,
      begin: 200.0,
      end: 400.0
    });
  }

  build() {
    // ......
  }
}

```

<a id="reset-1"></a>
## reset

```TypeScript
reset(options: AnimatorOptions | SimpleAnimatorOptions): void
```

重置当前animator动画参数。与[reset](arkts-arkui-animator-animatorresult-i.md#reset-1)相比，新增对[SimpleAnimatorOptions](arkts-arkui-animator-simpleanimatoroptions-c.md)类型入参的支持。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-AnimatorResult-reset(options: AnimatorOptions | SimpleAnimatorOptions): void--><!--Device-AnimatorResult-reset(options: AnimatorOptions | SimpleAnimatorOptions): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [AnimatorOptions](arkts-arkui-animator-animatoroptions-i.md) \| SimpleAnimatorOptions | 是 | 定义动画选项。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:<br> 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameters types.<br> 3. Parameter verification failed. |
| [100001](../errorcode-internal.md#100001-接口调用异常错误码) | The specified page is not found or the object property list is not obtained. |

**示例：**

完整示例请参考[基于ArkTS扩展的声明式开发范式](#基于arkts扩展的声明式开发范式)。

```TypeScript
import { Animator as animator, AnimatorResult, AnimatorOptions, SimpleAnimatorOptions } from '@kit.ArkUI';

let options: AnimatorOptions = {
  duration: 1500,
  easing: 'ease',
  delay: 0,
  fill: "forwards",
  direction: "normal",
  iterations: 1,
  begin: 100,
  end: 200
};
let optionsNew: SimpleAnimatorOptions = new SimpleAnimatorOptions(100, 200)
  .duration(2000)
  .iterations(3)
  .delay(1000);
let animatorResult: AnimatorResult = animator.create(options);
animatorResult.reset(optionsNew);

```

<a id="reverse"></a>
## reverse

```TypeScript
reverse(): void
```

以相反的顺序播放动画。使用interpolating-spring曲线时此接口无效。

**起始版本：** 6

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-AnimatorResult-reverse(): void--><!--Device-AnimatorResult-reverse(): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**示例：**

完整示例请参考[基于ArkTS扩展的声明式开发范式](#基于arkts扩展的声明式开发范式)。

```TypeScript
animator.reverse();

```

<a id="setexpectedframeraterange"></a>
## setExpectedFrameRateRange

```TypeScript
setExpectedFrameRateRange(rateRange: ExpectedFrameRateRange): void
```

设置期望的帧率范围。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AnimatorResult-setExpectedFrameRateRange(rateRange: ExpectedFrameRateRange): void--><!--Device-AnimatorResult-setExpectedFrameRateRange(rateRange: ExpectedFrameRateRange): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| rateRange | [ExpectedFrameRateRange](../arkts-components/arkts-arkui-expectedframeraterange-i.md) | 是 | 设置期望的帧率范围。 |

**示例：**

```TypeScript
import { AnimatorResult } from '@kit.ArkUI';

let expectedFrameRate: ExpectedFrameRateRange = {
  min: 0,
  max: 120,
  expected: 30
}

@Entry
@Component
struct AnimatorTest {
  private backAnimator: AnimatorResult | undefined = undefined;

  create() {
    this.backAnimator = this.getUIContext().createAnimator({
      duration: 2000,
      easing: "ease",
      delay: 0,
      fill: "forwards",
      direction: "normal",
      iterations: 1,
      begin: 100, // 动画插值起点
      end: 200 // 动画插值终点
    })
    this.backAnimator.setExpectedFrameRateRange(expectedFrameRate);
  }

  build() {
    // ......
  }
}

```

<a id="update"></a>
## update

```TypeScript
update(options: AnimatorOptions): void
```

更新当前动画器。

> **说明：**  
>  
> 从API version 6开始支持，从API version 9开始废弃。建议使用[reset](arkts-arkui-animator-animatorresult-i.md#reset-1)替代。

**起始版本：** 6

**废弃版本：** 9

**替代接口：** [reset(options:](arkts-arkui-animator-animatorresult-i.md#reset-1)

<!--Device-AnimatorResult-update(options: AnimatorOptions): void--><!--Device-AnimatorResult-update(options: AnimatorOptions): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [AnimatorOptions](arkts-arkui-animator-animatoroptions-i.md) | 是 | 定义动画选项。 |

**示例：**

完整示例请参考[基于ArkTS扩展的声明式开发范式](#基于arkts扩展的声明式开发范式)。

```TypeScript
animator.update(options);

```

## onCancel

```TypeScript
onCancel: () => void
```

动画被取消时回调。

**类型：** () =&gt; void

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AnimatorResult-onCancel: () => void--><!--Device-AnimatorResult-onCancel: () => void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onFinish

```TypeScript
onFinish: () => void
```

动画完成时回调。

**类型：** () =&gt; void

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AnimatorResult-onFinish: () => void--><!--Device-AnimatorResult-onFinish: () => void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onFrame

```TypeScript
onFrame: (progress: number) => void
```

接收到帧时回调。

progress表示动画的当前值。取值范围为[AnimatorOptions](arkts-arkui-animator-animatoroptions-i.md)定义的[begin, end]，默认取值范围为[0, 1]。

**类型：** (progress: number) =&gt; void

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AnimatorResult-onFrame: (progress: number) => void--><!--Device-AnimatorResult-onFrame: (progress: number) => void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onRepeat

```TypeScript
onRepeat: () => void
```

动画重复时回调。

**类型：** () =&gt; void

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AnimatorResult-onRepeat: () => void--><!--Device-AnimatorResult-onRepeat: () => void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## oncancel

```TypeScript
oncancel: () => void
```

动画被取消时回调。

**说明:** 从API version 6开始支持，从API version 12开始废弃，推荐使用onCancel。

**类型：** () =&gt; void

**起始版本：** 6

**废弃版本：** 12

**替代接口：** onCancel

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-AnimatorResult-oncancel: () => void--><!--Device-AnimatorResult-oncancel: () => void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onfinish

```TypeScript
onfinish: () => void
```

动画完成时回调。

**说明:** 从API version 6开始支持，从API version 12开始废弃，推荐使用onFinish。

**类型：** () =&gt; void

**起始版本：** 6

**废弃版本：** 12

**替代接口：** onFinish

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-AnimatorResult-onfinish: () => void--><!--Device-AnimatorResult-onfinish: () => void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onframe

```TypeScript
onframe: (progress: number) => void
```

接收到帧时回调。

**说明:** 从API version 6开始支持，从API version 12开始废弃，推荐使用onFrame。

**类型：** (progress: number) =&gt; void

**起始版本：** 6

**废弃版本：** 12

**替代接口：** onFrame

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-AnimatorResult-onframe: (progress: number) => void--><!--Device-AnimatorResult-onframe: (progress: number) => void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onrepeat

```TypeScript
onrepeat: () => void
```

动画重复时回调。

**说明:** 从API version 6开始支持，从API version 12开始废弃，推荐使用onRepeat。

**类型：** () =&gt; void

**起始版本：** 6

**废弃版本：** 12

**替代接口：** onRepeat

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-AnimatorResult-onrepeat: () => void--><!--Device-AnimatorResult-onrepeat: () => void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

