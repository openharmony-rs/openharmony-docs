# Stepper属性/事件

```TypeScript
declare class StepperAttribute extends CommonMethod<StepperAttribute>
```

无

**继承/实现关系：** StepperAttribute extends CommonMethod&lt;StepperAttribute&gt;

**起始版本：** 8

**废弃版本：** 22

**替代接口：** [SwiperAttribute](arkts-arkui-swiper-comp-attribute.md)

<!--Device-unnamed-declare class StepperAttribute extends CommonMethod<StepperAttribute>--><!--Device-unnamed-declare class StepperAttribute extends CommonMethod<StepperAttribute>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onChange

```TypeScript
onChange(callback: (prevIndex: number, index: number) => void)
```

点击切换标签时的回调。

**起始版本：** 8

**废弃版本：** 22

**替代接口：** onChange

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

<!--Device-StepperAttribute-onChange(callback: (prevIndex: number, index: number) => void): StepperAttribute--><!--Device-StepperAttribute-onChange(callback: (prevIndex: number, index: number) => void): StepperAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | (prevIndex: number, index: number) =&gt; void | 是 | 页面切换时触发的回调。<br>prevIndex: 切换前的步骤页索引值。<br>取值范围：[0, +∞)。<br>index: 切换后的步骤页（前一页或者下一页）索引值。<br>取值范围：[0, +∞)。 |

## onFinish

```TypeScript
onFinish(callback: () => void)
```

点击完成标签时的回调。

**起始版本：** 8

**废弃版本：** 22

**替代接口：** onChange

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

<!--Device-StepperAttribute-onFinish(callback: () => void): StepperAttribute--><!--Device-StepperAttribute-onFinish(callback: () => void): StepperAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | () =&gt; void | 是 | 当**Stepper**中最后一个**StepperItem**的**nextLabel**被点击，并且**ItemState**属性为**Normal**时调用。 |

## onNext

```TypeScript
onNext(callback: (index: number, pendingIndex: number) => void)
```

点击下一步标签时的回调。

**起始版本：** 8

**废弃版本：** 22

**替代接口：** onChange

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

<!--Device-StepperAttribute-onNext(callback: (index: number, pendingIndex: number) => void): StepperAttribute--><!--Device-StepperAttribute-onNext(callback: (index: number, pendingIndex: number) => void): StepperAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | (index: number, pendingIndex: number) =&gt; void | 是 | 页面切换时触发的回调。<br>index: 当前步骤页索引值。<br>pendingIndex: 下一步骤页索引值。 |

## onPrevious

```TypeScript
onPrevious(callback: (index: number, pendingIndex: number) => void)
```

点击上一步标签时的回调。

**起始版本：** 8

**废弃版本：** 22

**替代接口：** onChange

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

<!--Device-StepperAttribute-onPrevious(callback: (index: number, pendingIndex: number) => void): StepperAttribute--><!--Device-StepperAttribute-onPrevious(callback: (index: number, pendingIndex: number) => void): StepperAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | (index: number, pendingIndex: number) =&gt; void | 是 | 页面切换时触发的回调。<br>index: 当前步骤页索引值。<br>pendingIndex: 上一步骤页索引值。 |

## onSkip

```TypeScript
onSkip(callback: () => void)
```

点击跳过标签时的回调。

**起始版本：** 8

**废弃版本：** 22

**替代接口：** onChange

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

<!--Device-StepperAttribute-onSkip(callback: () => void): StepperAttribute--><!--Device-StepperAttribute-onSkip(callback: () => void): StepperAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | () =&gt; void | 是 | 当前显示的**StepperItem**状态为**ItemState.Skip**时，**nextLabel**被点击时调用。 |
