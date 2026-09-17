# PasteButtonCallback

```TypeScript
type PasteButtonCallback = (event: ClickEvent, result: PasteButtonOnClickResult, error?: BusinessError<void>) => void
```

Triggered when the **PasteButton** component is clicked.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | [ClickEvent](arkts-arkui-clickevent-i.md) | Yes | Click event object, which includes information such as click position, timestamp and input device. |
| result | [PasteButtonOnClickResult](arkts-arkui-pastebuttononclickresult-e.md) | Yes | Authorization result for clipboard access permission.<br>A return value of **SUCCESS** means temporary read permission for current clipboard content is granted, and clipboard reading operations can proceed. A return value of **TEMPORARY_AUTHORIZATION_FAILED** means the authorization failed, and you must not attempt to read clipboard content. |
| error | [BusinessError](arkts-arkui-businesserror-t.md)&lt;void&gt; | No | Error code and message when the component is clicked.<br>Default value:undefined. <br>Use the **result** parameter to determine the authorization status.<br>Error code 1 indicates an internal system error. Check the system status and try again.<br>Error code 2 indicates property configuration errors, including but not limited to:<br>1. The font or icon size is too small.<br>2. The font or icon color is similar to the component background color.<br>3. The font or icon color is too transparent.<br>4. The padding is negative.<br>5. The component is obscured by other components or windows. <br>6. Text extends beyond the component background area.<br>7. The component exceeds the window or screen bounds.<br>8. The component size is too large.<br>9. The component text is truncated and not fully displayed. <br>10. Improper settings of some security component properties prevent the component from displaying correctly. |
