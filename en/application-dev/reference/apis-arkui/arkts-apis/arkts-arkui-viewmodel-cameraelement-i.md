# CameraElement

The &lt;camera&gt; component provides preview and photographing functions.

@extends Element @interface CameraElement

**Inheritance/Implementation:** CameraElement extends [Element](arkts-arkui-viewmodel-element-i.md)

**Since:** 6

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## takePhoto

```TypeScript
takePhoto(options: CameraTakePhotoOptions): void
```

Take photos with specified parameters.

**Since:** 6

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [CameraTakePhotoOptions](arkts-arkui-viewmodel-cameratakephotooptions-i.md) | Yes | the parameters of camera. |
