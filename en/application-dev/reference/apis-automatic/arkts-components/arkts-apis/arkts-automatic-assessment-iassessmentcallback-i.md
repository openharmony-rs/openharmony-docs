# IAssessmentCallback

```TypeScript
interface IAssessmentCallback
```

Assessment callback interface.

**Since:** 26.0.1

<!--Device-assessment-interface IAssessmentCallback--><!--Device-assessment-interface IAssessmentCallback-End-->

**System capability:** SystemCapability.Customization.AssessmentConfiguration

## Modules to Import

```TypeScript
```

## onBegin

```TypeScript
onBegin(error: AssessmentError): void
```

Assessment start notification.

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-IAssessmentCallback-onBegin(error: AssessmentError): void--><!--Device-IAssessmentCallback-onBegin(error: AssessmentError): void-End-->

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

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-IAssessmentCallback-onEnd(): void--><!--Device-IAssessmentCallback-onEnd(): void-End-->

**System capability:** SystemCapability.Customization.AssessmentConfiguration

## onInterrupted

```TypeScript
onInterrupted(info: AssessmentInterruptInfo): void
```

Assessment interrupt notification.

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-IAssessmentCallback-onInterrupted(info: AssessmentInterruptInfo): void--><!--Device-IAssessmentCallback-onInterrupted(info: AssessmentInterruptInfo): void-End-->

**System capability:** SystemCapability.Customization.AssessmentConfiguration

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| info | [AssessmentInterruptInfo](arkts-automatic-assessment-assessmentinterruptinfo-i.md) | Yes | Interrupt information, including the reason and detailed description. |
