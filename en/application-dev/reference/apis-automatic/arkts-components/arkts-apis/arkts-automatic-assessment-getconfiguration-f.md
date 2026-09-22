# getConfiguration

## Modules to Import

```TypeScript
```

## getConfiguration

```TypeScript
function getConfiguration(): AssessmentConfig
```

Queries the current assessment configuration.

**Since:** 26.0.1

**Required permissions:** ohos.permission.ASSESSMENT_CONFIGURATION

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.AssessmentConfiguration

**Return value:**

| Type | Description |
| --- | --- |
| [AssessmentConfig](arkts-automatic-assessment-assessmentconfig-i.md) | Returns the current assessment configuration. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |
