# postCardAction

## postCardAction

```TypeScript
declare function postCardAction(component: Object, action: Object): void
```

Post Card Action.

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

<!--Device-unnamed-declare function postCardAction(component: Object, action: Object): void--><!--Device-unnamed-declare function postCardAction(component: Object, action: Object): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| component | Object | Yes | indicate the card entry component. |
| action | Object | Yes | indicate the router, message or call event.<!--Del-->Since API version 26.0.1, for system applications,the action support insightIntent event.<!--DelEnd--> |
