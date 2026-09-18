# OnTrackChangeHandler

```TypeScript
type OnTrackChangeHandler = (index: number, isSelected: boolean) => void
```

Describes the callback invoked for the track change event.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Multimedia.Media.AVPlayer

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| index | number | Yes | Index of the track that has changed. |
| isSelected | boolean | Yes | Whether the track at the current index is selected. **true** if selected, **false** otherwise. |
