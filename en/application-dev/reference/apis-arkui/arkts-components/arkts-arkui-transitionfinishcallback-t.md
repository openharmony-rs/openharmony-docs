# TransitionFinishCallback

```TypeScript
declare type TransitionFinishCallback = (transitionIn: boolean) => void
```

Represents the type of callback for the end of a component's transition animation.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| transitionIn | boolean | Yes | Type of callback for the end of the transition animation.<br>The value **true** indicates that the callback is for the end of an appearance animation, and **false** indicates that the callback is for the end of a disappearance animation. |
