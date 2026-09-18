# PublishFormCrossBundleControlCallback (System API)

```TypeScript
type PublishFormCrossBundleControlCallback = (info: PublishFormCrossBundleInfo) => boolean
```

publish form cross bundle control callback.

@typedef { function } PublishFormCrossBundleControlCallback

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.Form

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| info | [PublishFormCrossBundleInfo](arkts-form-forminfo-publishformcrossbundleinfo-i-sys.md) | Yes | Publish form cross bundle info. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Publish form cross bundle control result, true indicates success, false indicates failure. |
