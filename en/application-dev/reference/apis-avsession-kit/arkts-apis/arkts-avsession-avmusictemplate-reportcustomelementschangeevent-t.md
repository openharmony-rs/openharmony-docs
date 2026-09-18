# ReportCustomElementsChangeEvent

```TypeScript
type ReportCustomElementsChangeEvent = (actionType: ActionType, customType: CustomType,
    customElement: CustomElement) => void
```

The report custom elements change event.

@typedef { function } ReportCustomElementsChangeEvent

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| actionType | [ActionType](arkts-avsession-avmusictemplate-actiontype-t.md) | Yes | action type |
| customType | [CustomType](arkts-avsession-avmusictemplate-customtype-t.md) | Yes | custom type |
| customElement | [CustomElement](arkts-avsession-avmusictemplate-customelement-i.md) | Yes | custom element |
