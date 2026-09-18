# Stepper properties/events

Defines the stepper attribute functions

@extends CommonMethod&lt;StepperAttribute&gt;

**Inheritance/Implementation:** StepperAttribute extends CommonMethod<StepperAttribute>

**Since:** 8

**Deprecated since:** 22

**Substitutes:** [SwiperAttribute](arkts-arkui-swiper-comp-attribute.md#swiperattribute)

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## onChange

```TypeScript
onChange(callback: (prevIndex: number, index: number) => void)
```

Triggered when the step navigation switches by clicking [prevLabel](arkts-arkui-stepperitem-comp-attribute.md#prevlabel) of the **StepperItem** component; or when clicking [nextLabel](arkts-arkui-stepperitem-comp-attribute.md#nextlabel) of the current **StepperItem** component, provided that the current page is not the last **StepperItem** in the stepper and the ItemState attribute is **Normal**.

> **NOTE:** 

**Since:** 8

**Deprecated since:** 22

**Substitutes:** onChange

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | (prevIndex: number, index: number) =&gt; void | Yes | Callback triggered when the page is switched.<br>prevIndex: Index of the step page before the switching.<br>Value range: [0, +∞).<br>index: Index of the step page after the switching, that is, index of the previous or next page. <br>Value range: [0, +∞). |

## onFinish

```TypeScript
onFinish(callback: () => void)
```

Triggered when [nextLabel](arkts-arkui-stepperitem-comp-attribute.md#nextlabel) of the last StepperItem in the stepper is clicked and the ItemState attribute is **Normal**.

> **NOTE:** 

**Since:** 8

**Deprecated since:** 22

**Substitutes:** onChange

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | () =&gt; void | Yes | Invoked when the **nextLabel** of the last **StepperItem** in the **Stepper** is clicked and the **ItemState** attribute is set to **Normal**. |

## onNext

```TypeScript
onNext(callback: (index: number, pendingIndex: number) => void)
```

Triggered when switching to the next step by clicking [nextLabel](arkts-arkui-stepperitem-comp-attribute.md#nextlabel) of a **StepperItem**, provided that the current page is not the last **StepperItem** in the stepper and the ItemState attribute is **Normal**.

> **NOTE:** 

**Since:** 8

**Deprecated since:** 22

**Substitutes:** onChange

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | (index: number, pendingIndex: number) =&gt; void | Yes | Callback triggered when the page is switched.<br>index: Index of the current step page.<br>pendingIndex: Index of the next step page. |

## onPrevious

```TypeScript
onPrevious(callback: (index: number, pendingIndex: number) => void)
```

Triggered when switching to the previous step by clicking [prevLabel](arkts-arkui-stepperitem-comp-attribute.md#prevlabel) of a **StepperItem**.

> **NOTE:** 

**Since:** 8

**Deprecated since:** 22

**Substitutes:** onChange

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | (index: number, pendingIndex: number) =&gt; void | Yes | Callback triggered when the page is switched.<br>index: Index of the current step page.<br>pendingIndex: Index of the next step page. |

## onSkip

```TypeScript
onSkip(callback: () => void)
```

Triggered when [nextLabel](arkts-arkui-stepperitem-comp-attribute.md#nextlabel) is clicked and the StepperItem status is **ItemState.Skip**.

> **NOTE:** 

**Since:** 8

**Deprecated since:** 22

**Substitutes:** onChange

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | () =&gt; void | Yes | Invoked when the current **StepperItem** is **ItemState.Skip** and the **nextLabel** is clicked. |
