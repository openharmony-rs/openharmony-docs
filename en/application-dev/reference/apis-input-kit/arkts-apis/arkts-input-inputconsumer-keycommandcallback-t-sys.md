# KeyCommandCallback (System API)

```TypeScript
type KeyCommandCallback = (keyOptions: KeyOptions, keyEvent: KeyEvent) => void
```

Defines the key command callback function type, which is triggered when the hotkey registration conditions are met.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-inputConsumer-type KeyCommandCallback = (keyOptions: KeyOptions, keyEvent: KeyEvent) => void--><!--Device-inputConsumer-type KeyCommandCallback = (keyOptions: KeyOptions, keyEvent: KeyEvent) => void-End-->

**System capability:** SystemCapability.MultimodalInput.Input.InputConsumer

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| keyOptions | [KeyOptions](arkts-input-inputconsumer-keyoptions-i-sys.md) | Yes | Key combination options when the callback is triggered. |
| keyEvent | [KeyEvent](arkts-input-multimodalinput-keyevent-keyevent-i.md) | Yes | Key event object, which contains detailed key information. |
