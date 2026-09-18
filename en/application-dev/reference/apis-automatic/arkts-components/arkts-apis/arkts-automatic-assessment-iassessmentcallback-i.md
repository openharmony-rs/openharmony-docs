# IAssessmentCallback

Assessment callback interface.

**Since:** 26.1.0

**System capability:** SystemCapability.Customization.AssessmentConfiguration

## Modules to Import

```TypeScript
```

## onBegin

```TypeScript
onBegin(error: AssessmentError): void
```

Assessment start notification.

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.AssessmentConfiguration

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| error | [AssessmentError](arkts-automatic-assessment-assessmenterror-i.md) | Yes | Error information. code=0 indicates success. |

## onEnd

```TypeScript
onEnd(): void
```

Assessment end notification.

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.AssessmentConfiguration

## onInterrupted

```TypeScript
onInterrupted(info: AssessmentInterruptInfo): void
```

Assessment interrupt notification.

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.AssessmentConfiguration

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| info | [AssessmentInterruptInfo](arkts-automatic-assessment-assessmentinterruptinfo-i.md) | Yes | Interrupt information, including the reason and detailed description. |
