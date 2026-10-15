# OnNativeLoadCallback

```TypeScript
declare type OnNativeLoadCallback = (event?: object) => void
```

Callback event triggered after the native loading of the **XComponent** is complete, used to pass the context of the **XComponent** instance object to the developer. Difference from [onSurfaceCreated](arkts-arkui-xcomponent-comp-xcomponentcontroller-c.md#onsurfacecreated): the **onLoad** callback parameter is the **context** object, which applies to the scenario where the **libraryname** parameter is set; the **onSurfaceCreated** callback parameter is **surfaceId**, which applies to the scenario where the **libraryname** parameter is not set. **onLoad** is triggered earlier than **onSurfaceCreated**.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-unnamed-declare type OnNativeLoadCallback = (event?: object) => void--><!--Device-unnamed-declare type OnNativeLoadCallback = (event?: object) => void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | object | No | Context of the XComponent instance object. The methods mounted on the context are defined by the developer on the native layer. Pass this parameter when the methods defined on the native layer need to be used in the callback; if it is not passed, the context object cannot be obtained in the callback. |
