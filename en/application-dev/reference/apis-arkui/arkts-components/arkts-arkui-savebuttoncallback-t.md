# SaveButtonCallback

```TypeScript
type SaveButtonCallback = (event: ClickEvent, result: SaveButtonOnClickResult, error?: BusinessError<void>) => void
```

Triggered when the **SaveButton** component is clicked.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | [ClickEvent](arkts-arkui-clickevent-i.md) | Yes | Click event object, which includes information such as click position, timestamp, and input device. |
| result | [SaveButtonOnClickResult](arkts-arkui-savebuttononclickresult-e.md) | Yes | Authorization result. <br>Returns **SUCCESS** if temporary authorization is granted for the save operation, and media library APIs can be accessed. Returns **TEMPORARY_AUTHORIZATION_FAILED** if temporary authorization fails and users cannot proceed with subsequent save actions. Returns **CANCELED_BY_USER** if users manually cancel authorization in the dialog box. This result is returned only when [userCancelEvent](arkts-arkui-savebutton-comp-attribute.md#usercancelevent) is called with its parameter set to **true**. If **userCancelEvent** is not set to **true**, **TEMPORARY_AUTHORIZATION_FAILED** is returned when users cancel authorization instead. |
| error | [BusinessError](arkts-arkui-businesserror-t.md)&lt;void&gt; | No | Error code and message when the component is clicked. If this parameter is not specified, the value is **undefined**. Use the **result** parameter to determine the authorization status.<br> Error code 1 indicates an internal system error. Possible causes and solutions are as follows: <br>1. Inter-Process Communication (IPC) failure. Check the system status and try again. <br>2. Failed to display the security component dialog box. Check whether the save button is blocked or complies with style constraints for security components. Correct the issues and retry. <br>Error code 2 indicates invalid property settings. Possible causes are as follows: <br>1. The font or icon size is too small. <br>2. The font or icon color is too similar to the background color. <br>3. The font or icon color is too transparent. <br>4. The padding is negative. <br>5. The component is obscured by other components or windows. <br>6. Text extends beyond the component background area. <br>7. The component exceeds the window or screen bounds. <br>8. The component size is too large. <br>9. The component text is truncated and not fully displayed. <br>10. Other improper property settings affect the display of the security component. |
