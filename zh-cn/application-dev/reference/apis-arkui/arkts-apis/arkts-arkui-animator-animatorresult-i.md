# AnimatorResult

```TypeScript
export interface AnimatorResult
```

定义AnimatorResult接口，提供动画播放状态回调及动画控制方法。

**起始版本：** 6

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { Animator, AnimatorOptions, AnimatorResult, SimpleAnimatorOptions } from '@kit.ArkUI';
```

## cancel

```TypeScript
cancel(): void
```

取消动画，会触发[onCancel](#oncancel)回调。此接口和[finish](#finish)接口功能上没有区别，仅触发的回调不同，建议使用finish接口结束动画。调用此方法时会触发一次额外的[onFrame](#onframe)回调，返回值是动画终点值，可能导致属性值在一帧内跳变至终点。

**起始版本：** 6

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**示例**

完整示例请参考基于ArkTS扩展的声明式开发范式。

```TypeScript
// animator需先通过this.getUIContext().createAnimator()获取AnimatorResult对象
animator.cancel();
```

## finish

```TypeScript
finish(): void
```

结束动画，会触发[onFinish](#onfinish)回调。与[cancel](#cancel)方法功能相同，但cancel()触发[onCancel](#oncancel)回调，建议使用finish方法结束动画。调用此方法时会触发一次额外的[onFrame](#onframe)回调，返回值是动画终点值，可能导致属性值在一帧内跳变至终点。若希望动画在中途暂停，可先将onFrame设置为空函数，再调用finish。

**起始版本：** 6

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**示例**

完整示例请参考基于ArkTS扩展的声明式开发范式。

```TypeScript
// animator需先通过this.getUIContext().createAnimator()获取AnimatorResult对象
animator.finish();
```

## onCancel

```TypeScript
onCancel: () => void
```

动画被取消时回调。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onFinish

```TypeScript
onFinish: () => void
```

动画完成时回调。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onFrame

```TypeScript
onFrame: (progress: number) => void
```

接收到帧时回调。

progress表示动画的当前值。取值范围为[AnimatorOptions](arkts-arkui-animator-animatoroptions-i.md)定义的[begin, end]，默认取值范围为[0, 1]。

**说明：** 调用cancel、finish方法时，会触发一次额外的onFrame回调，返回值为动画终点值。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| progress | number | 是 |  |

## onRepeat

```TypeScript
onRepeat: () => void
```

动画重复时回调。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## pause

```TypeScript
pause(): void
```

暂停动画。暂停后可调用[play](#play)方法恢复播放，也可调用[finish](#finish)或[cancel](#cancel)方法结束动画。

**起始版本：** 6

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**示例**

完整示例请参考基于ArkTS扩展的声明式开发范式。

```TypeScript
// animator需先通过this.getUIContext().createAnimator()获取AnimatorResult对象
animator.pause();
```

## play

```TypeScript
play(): void
```

启动动画。动画暂停后调用此方法可恢复播放。动画会保留上一次的播放状态，比如播放状态设置reverse后，再次播放会保留reverse的播放状态。动画结束后（[onFinish](#onfinish)或[onCancel](#oncancel)回调触发后）可再次调用此方法重新播放动画。

**起始版本：** 6

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**示例**

完整示例请参考基于ArkTS扩展的声明式开发范式。

```TypeScript
// animator需先通过this.getUIContext().createAnimator()获取AnimatorResult对象
animator.play();
```

## reset

```TypeScript
reset(options: AnimatorOptions): void
```

重置当前animator动画参数。建议在动画未开始播放或播放结束后（[onFinish](#onfinish)或[onCancel](#oncancel)回调触发后）调用此方法，重置后需调用[play](#play)方法重新启动动画。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [AnimatorOptions](arkts-arkui-animator-animatoroptions-i.md) | 是 | 动画配置选项，用于定义动画的播放时长、插值曲线、延时、填充模式、播放方向、播放次数及插值起止值等参数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-函数参数数量或参数类型不匹配) | Parameter error. Possible causes:<br> 1. Mandatory parameters are left unspecified. <br> 2. Incorrect parameters types. <br> 3. Parameter verification failed. |
| [100001](../errorcode-internal.md#100001-接口调用异常错误码) | The specified page is not found or the object property list is not obtained. |

**示例**

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
    // ...
  }
}
```

<a id="reset-1"></a>

## reset

```TypeScript
reset(options: AnimatorOptions | SimpleAnimatorOptions): void
```

重置当前animator动画参数。与[reset](#reset)相比，新增对[SimpleAnimatorOptions](arkts-arkui-animator-simpleanimatoroptions-c.md)类型入参的支持。建议在动画未开始播放或播放结束后（[onFinish](#onfinish)或[onCancel](#oncancel)回调触发后）调用此方法，重新设置动画参数后调用[play](#play)启动新动画。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [AnimatorOptions](arkts-arkui-animator-animatoroptions-i.md) &#124; [SimpleAnimatorOptions](arkts-arkui-animator-simpleanimatoroptions-c.md) | 是 | 定义动画选项。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-函数参数数量或参数类型不匹配) | Parameter error. Possible causes:<br> 1. Mandatory parameters are left unspecified. <br> 2. Incorrect parameters types. <br> 3. Parameter verification failed. |
| [100001](../errorcode-internal.md#100001-接口调用异常错误码) | The specified page is not found or the object property list is not obtained. |

**示例**

完整示例请参考基于ArkTS扩展的声明式开发范式。

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

## reverse

```TypeScript
reverse(): void
```

以相反的顺序播放动画。使用interpolating-spring曲线时此接口无效。调用reverse后动画将以相反方向继续播放，可通过[pause](#pause)暂停或[finish](#finish)结束动画。

**起始版本：** 6

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**示例**

完整示例请参考基于ArkTS扩展的声明式开发范式。

```TypeScript
// animator需先通过this.getUIContext().createAnimator()获取AnimatorResult对象
animator.reverse();
```

## setExpectedFrameRateRange

```TypeScript
setExpectedFrameRateRange(rateRange: ExpectedFrameRateRange): void
```

设置期望的帧率范围，包含最小、最大和期望帧率值。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| rateRange | [ExpectedFrameRateRange](../arkts-components/arkts-arkui-common-comp-expectedframeraterange-i.md) | 是 | 设置期望的帧率范围。 |

**示例**

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
    // ...
  }
}
```

## oncancel

```TypeScript
oncancel: () => void
```

动画被取消时回调。

**说明：** 从API version 6开始支持，从API version 12开始废弃，推荐使用[onCancel](#oncancel)。

**起始版本：** 6

**废弃版本：** 12

**替代接口：** onCancel

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onfinish

```TypeScript
onfinish: () => void
```

动画完成时回调。

**说明：** 从API version 6开始支持，从API version 12开始废弃，推荐使用[onFinish](#onfinish)。

**起始版本：** 6

**废弃版本：** 12

**替代接口：** onFinish

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onframe

```TypeScript
onframe: (progress: number) => void
```

接收到帧时回调。

**说明：** 从API version 6开始支持，从API version 12开始废弃，推荐使用[onFrame](#onframe)。

**起始版本：** 6

**废弃版本：** 12

**替代接口：** onFrame

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| progress | number | 是 |  |

## onrepeat

```TypeScript
onrepeat: () => void
```

动画重复时回调。

**说明：** 从API version 6开始支持，从API version 12开始废弃，推荐使用[onRepeat](#onrepeat)。

**起始版本：** 6

**废弃版本：** 12

**替代接口：** onRepeat

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## update

```TypeScript
update(options: AnimatorOptions): void
```

更新当前animator动画参数。

> **说明：** 
> 
> 从API version 6开始支持，从API version 9开始废弃。

**起始版本：** 6

**废弃版本：** 9

**替代接口：** reset

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [AnimatorOptions](arkts-arkui-animator-animatoroptions-i.md) | 是 | 动画配置选项，用于定义动画的播放时长、插值曲线、延时、填充模式、播放方向、播放次数及插值起止值等参数。 |

**示例**

完整示例请参考基于ArkTS扩展的声明式开发范式。

```TypeScript
// animator需先通过this.getUIContext().createAnimator()获取AnimatorResult对象
animator.update(options);
```
