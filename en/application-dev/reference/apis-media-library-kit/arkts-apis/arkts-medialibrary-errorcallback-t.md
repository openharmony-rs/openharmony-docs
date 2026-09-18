# ErrorCallback

```TypeScript
export type ErrorCallback = (pickerError: PickerError) => void
```

Callback to be invoked when an error occurs in the **PhotoPickerComponent**.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 23.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| pickerError | [PickerError](arkts-medialibrary-file-photopickercomponent-pickererror-c.md) | Yes | Basic information about the error. |
