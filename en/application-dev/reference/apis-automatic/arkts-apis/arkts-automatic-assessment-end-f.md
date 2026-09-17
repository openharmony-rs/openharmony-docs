# end

## Modules to Import

```TypeScript
```

## end

```TypeScript
function end(context: UIAbilityContext): void
```

Ends an assessment session.

**Since:** 26.1.0

**Required permissions:** ohos.permission.ASSESSMENT_CONFIGURATION

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.AssessmentConfiguration

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| context | [UIAbilityContext](../../apis-ability-kit/arkts-apis/arkts-ability-uiabilitycontext-c.md) | Yes | Context of the UIAbility that needs to exit assessment mode. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |
| 36700001 | Assessment internal error. Possible cause: IPC invocation failed internally. |
| 36700003 | Assessment configuration service is not active. Possible cause: Not in assessment state. |
| 36700004 | Invalid operation. Possible cause: Cannot terminate another active assessment. |
