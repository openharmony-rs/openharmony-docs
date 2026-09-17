# GetWantParamsCallback (System API)

```TypeScript
type GetWantParamsCallback = (formInfo: Array<formInfo.FormInfo>) => Array<Record<string, Object>>
```

Get want parameters callback.

@typedef { function }

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.Form

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| formInfo | Array&lt;[formInfo.FormInfo](arkts-form-forminfo-forminfo-i.md)&gt; | Yes | The list of the form information. |

**Return value:**

| Type | Description |
| --- | --- |
| Array&lt;Record&lt;string, Object&gt;&gt; | The want parameters list of the forms. |
