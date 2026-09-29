# AssessmentError

```TypeScript
interface AssessmentError
```

Assessment error information.

**Since:** 26.0.1

<!--Device-assessment-interface AssessmentError--><!--Device-assessment-interface AssessmentError-End-->

**System capability:** SystemCapability.Customization.AssessmentConfiguration

## Modules to Import

```TypeScript
```

## code

```TypeScript
code: AssessmentErrorCode
```

Error code. The value 0 indicates success, and a non-zero value indicates failure.

**Type:** [AssessmentErrorCode](arkts-automatic-assessment-assessmenterrorcode-e.md)

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-AssessmentError-code: AssessmentErrorCode--><!--Device-AssessmentError-code: AssessmentErrorCode-End-->

**System capability:** SystemCapability.Customization.AssessmentConfiguration

## message

```TypeScript
message?: string
```

Error description. This field is optional and defaults to an empty string if not provided.

**Type:** string

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-AssessmentError-message?: string--><!--Device-AssessmentError-message?: string-End-->

**System capability:** SystemCapability.Customization.AssessmentConfiguration
