# KeyCommandCallback (System API)

```TypeScript
type KeyCommandCallback = (keyOptions: KeyOptions, keyEvent: KeyEvent) => void
```

Callback function when the shortcut key registered by the system application meets the conditions.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.MultimodalInput.Input.InputConsumer

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| keyOptions | [KeyOptions](arkts-input-inputconsumer-keyoptions-i-sys.md) | Yes | Options for registering shortcut keys when the system applies. |
| keyEvent | [KeyEvent](arkts-input-multimodalinput-keyevent-keyevent-i.md) | Yes | Key event when a shortcut key is triggered. |
