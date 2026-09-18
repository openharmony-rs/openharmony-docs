# begin

## Modules to Import

```TypeScript
```

## begin

```TypeScript
function begin(context: UIAbilityContext, config: AssessmentConfig, callback: IAssessmentCallback): void
```

Begins an assessment session. A confirmation dialog box will be displayed for the user to confirm before the assessment session starts.

**Since:** 26.1.0

**Required permissions:** ohos.permission.ASSESSMENT_CONFIGURATION

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.AssessmentConfiguration

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| context | [UIAbilityContext](../../apis-ability-kit/arkts-apis/arkts-ability-uiabilitycontext-c.md) | Yes | Context of the UIAbility that needs to enter assessment mode. |
| config | [AssessmentConfig](arkts-automatic-assessment-assessmentconfig-i.md) | Yes | Assessment configuration. |
| callback | [IAssessmentCallback](arkts-automatic-assessment-iassessmentcallback-i.md) | Yes | Assessment callback. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |
| 36700001 | Assessment internal error. Possible cause: IPC invocation failed internally. |
| 36700002 | Assessment configuration service is already active. Possible cause: Assessment resource conflict. |
