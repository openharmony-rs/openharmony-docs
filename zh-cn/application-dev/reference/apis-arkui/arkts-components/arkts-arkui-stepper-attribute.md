# Stepper属性/事件

无

**继承/实现关系：** StepperAttribute extends [CommonMethod<StepperAttribute>](CommonMethod<StepperAttribute>)

**起始版本：** 8

**废弃版本：** 22

**替代接口：** SwiperAttribute

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onChange

```TypeScript
onChange(callback: (prevIndex: number, index: number) => void)
```

Callback when the change label is clicked.

**起始版本：** 8

**废弃版本：** 22

**替代接口：** onChange

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | (prevIndex: number, index: number) =&gt; void | 是 | Callback triggered when the page is switched.<br/>prevIndex: Index of the step pagebefore the switching.<br>Value range:[0, +∞).<br/>index: Index of the step page after the switching, that is, index of the previous or next page.<br>Value range: [0, +∞). |

## onFinish

```TypeScript
onFinish(callback: () => void)
```

Callback when the finish label is clicked.

**起始版本：** 8

**废弃版本：** 22

**替代接口：** onChange

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | () =&gt; void | 是 | Invoked when the **nextLabel** of the last **StepperItem** in the **Stepper** isclicked and the **ItemState** attribute is set to **Normal**. |

## onNext

```TypeScript
onNext(callback: (index: number, pendingIndex: number) => void)
```

Callback when the next label is clicked.

**起始版本：** 8

**废弃版本：** 22

**替代接口：** onChange

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | (index: number, pendingIndex: number) =&gt; void | 是 | Callback triggered when the page is switched.<br/>index: Index of the current steppage.<br/>pendingIndex: Index of the next step page. |

## onPrevious

```TypeScript
onPrevious(callback: (index: number, pendingIndex: number) => void)
```

Callback when the previous label is clicked.

**起始版本：** 8

**废弃版本：** 22

**替代接口：** onChange

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | (index: number, pendingIndex: number) =&gt; void | 是 | Callback triggered when the page is switched.<br/>index: Index of the current steppage.<br/>pendingIndex: Index of the next step page. |

## onSkip

```TypeScript
onSkip(callback: () => void)
```

Callback when the skip label is clicked.

**起始版本：** 8

**废弃版本：** 22

**替代接口：** onChange

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | () =&gt; void | 是 | Invoked when the current **StepperItem** is **ItemState.Skip** and the **nextLabel**is clicked. |

