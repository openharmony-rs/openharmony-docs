# InputKeyEventCallback

```TypeScript
export type InputKeyEventCallback = (event: InputKeyEvent) => boolean
```

The callback of 'keyEvent' event.

**Since:** 26.1.0

<!--Device-inputMethodEngine-export type InputKeyEventCallback = (event: InputKeyEvent) => boolean--><!--Device-inputMethodEngine-export type InputKeyEventCallback = (event: InputKeyEvent) => boolean-End-->

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | [InputKeyEvent](../../apis-input-kit/arkts-apis/arkts-input-multimodalinput-keyevent.md) | Yes | the key event. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | whether to consume this key event. |
