# animateToImmediately

## animateToImmediately

```TypeScript
declare function animateToImmediately(value: AnimateParam, event: () => void): void
```

Delivers an explicit animation immediately. This interface depends on the UI context and cannot be used when the UI context is unclear. It is recommended to use [animateToImmediately](../arkts-apis/arkts-arkui-arkui-uicontext-uicontext-c.md#animatetoimmediately) to explicitly specify the UI context.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-unnamed-declare function animateToImmediately(value: AnimateParam, event: () => void): void--><!--Device-unnamed-declare function animateToImmediately(value: AnimateParam, event: () => void): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [AnimateParam](arkts-arkui-common-comp-animateparam-i.md) | Yes | Animation settings. |
| event | () =&gt; void | Yes | Closure function that displays the animation. The system automatically inserts a transition animation for state changes caused by the closure function. |
