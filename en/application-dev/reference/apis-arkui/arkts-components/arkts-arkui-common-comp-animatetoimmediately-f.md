# animateToImmediately

## animateToImmediately

```TypeScript
declare function animateToImmediately(value: AnimateParam, event: () => void): void
```

Delivers an explicit animation immediately.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [AnimateParam](arkts-arkui-common-comp-animateparam-i.md) | Yes | Animation settings. |
| event | () =&gt; void | Yes | Closure function that displays the animation. The system automatically inserts a transition animation for state changes caused by the closure function. |
