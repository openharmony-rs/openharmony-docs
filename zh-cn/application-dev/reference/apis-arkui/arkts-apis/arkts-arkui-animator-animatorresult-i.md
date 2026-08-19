# AnimatorResult

定义Animator结果接口。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export interface AnimatorResult--><!--Device-unnamed-export interface AnimatorResult-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { Animator, AnimatorOptions, AnimatorResult, SimpleAnimatorOptions } from '@kit.ArkUI';
```

## cancel

```TypeScript
cancel(): void
```

取消动画，会触发onCancel回调。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AnimatorResult-cancel(): void--><!--Device-AnimatorResult-cancel(): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## finish

```TypeScript
finish(): void
```

结束动画，会触发onFinish回调。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AnimatorResult-finish(): void--><!--Device-AnimatorResult-finish(): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## pause

```TypeScript
pause(): void
```

暂停动画。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AnimatorResult-pause(): void--><!--Device-AnimatorResult-pause(): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## play

```TypeScript
play(): void
```

启动动画。动画会保留上一次的播放状态，比如播放状态设置reverse后，再次播放会保留reverse的播放状态。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AnimatorResult-play(): void--><!--Device-AnimatorResult-play(): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## reset

```TypeScript
reset(options: AnimatorOptions | SimpleAnimatorOptions): void
```

重置当前animator动画参数。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AnimatorResult-reset(options: AnimatorOptions | SimpleAnimatorOptions): void--><!--Device-AnimatorResult-reset(options: AnimatorOptions | SimpleAnimatorOptions): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [AnimatorOptions](arkts-arkui-animator-animatoroptions-i.md) \| [SimpleAnimatorOptions](arkts-arkui-animator-simpleanimatoroptions-c.md) | 是 | 定义动画选项。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [100001](../errorcode-internal.md#100001-接口调用异常错误码) | The specified page is not found or the object property list is not obtained. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: <br> 1. Mandatory parameters are left unspecified. <br> 2. Incorrect parameters types. <br> 3. Parameter verification failed. |

## reverse

```TypeScript
reverse(): void
```

以相反的顺序播放动画。使用interpolating-spring曲线时此接口无效。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AnimatorResult-reverse(): void--><!--Device-AnimatorResult-reverse(): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## setExpectedFrameRateRange

```TypeScript
setExpectedFrameRateRange(rateRange: ExpectedFrameRateRange): void
```

设置期望的帧率范围。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AnimatorResult-setExpectedFrameRateRange(rateRange: ExpectedFrameRateRange): void--><!--Device-AnimatorResult-setExpectedFrameRateRange(rateRange: ExpectedFrameRateRange): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| rateRange | [ExpectedFrameRateRange](../../apis-na/arkts-apis/arkts-na-common-expectedframeraterange-i.md) | 是 | 设置期望的帧率范围。 |

## onCancel

```TypeScript
onCancel: () => void
```

动画被取消时回调。

**类型：** () =&gt; void

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AnimatorResult-onCancel: () => void--><!--Device-AnimatorResult-onCancel: () => void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onFinish

```TypeScript
onFinish: () => void
```

动画完成时回调。

**类型：** () =&gt; void

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AnimatorResult-onFinish: () => void--><!--Device-AnimatorResult-onFinish: () => void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onFrame

```TypeScript
onFrame: (progress: double) => void
```

接收到帧时回调。

**类型：** (progress: double) =&gt; void

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AnimatorResult-onFrame: (progress: double) => void--><!--Device-AnimatorResult-onFrame: (progress: double) => void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onRepeat

```TypeScript
onRepeat: () => void
```

动画重复时回调。

**类型：** () =&gt; void

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AnimatorResult-onRepeat: () => void--><!--Device-AnimatorResult-onRepeat: () => void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

