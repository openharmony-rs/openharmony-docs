# isActive

## Modules to Import

```TypeScript
```

## isActive

```TypeScript
function isActive(): boolean
```

Queries whether an assessment session is active.

**Since:** 26.1.0

**Required permissions:** ohos.permission.ASSESSMENT_CONFIGURATION

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.AssessmentConfiguration

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Returns true if active, false otherwise. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |
