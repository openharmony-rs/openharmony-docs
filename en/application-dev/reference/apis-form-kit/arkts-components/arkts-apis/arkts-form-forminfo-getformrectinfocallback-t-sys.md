# GetFormRectInfoCallback (System API)

```TypeScript
type GetFormRectInfoCallback = (formId: string) => Promise<formInfo.Rect>
```

Get form rect info callback

@typedef { function } GetFormRectInfoCallback

**Since:** 20

**System capability:** SystemCapability.Ability.Form

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| formId | string | Yes |  |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[formInfo.Rect](arkts-form-forminfo-rect-i.md)&gt; | form rect info |
