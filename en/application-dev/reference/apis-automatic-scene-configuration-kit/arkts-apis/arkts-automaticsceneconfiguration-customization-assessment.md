# @ohos.customization.assessment

The **assessment** module provides APIs for assessment scenario management.

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-unnamed-declare namespace assessment--><!--Device-unnamed-declare namespace assessment-End-->

**System capability:** SystemCapability.Customization.AssessmentConfiguration

## Modules to Import

```TypeScript
import { assessment } from '@kit.AutomaticSceneConfigurationKit';
```

## Summary

### Functions

| Name | Description |
| --- | --- |
| [begin](arkts-automaticsceneconfiguration-assessment-begin-f.md#begin-1) | Begins an assessment session. A confirmation dialog box will be displayed for the user to confirm before the assessment session starts. |
| [end](arkts-automaticsceneconfiguration-assessment-end-f.md#end-1) | Ends an assessment session. |
| [getConfiguration](arkts-automaticsceneconfiguration-assessment-getconfiguration-f.md#getconfiguration-1) | Queries the current assessment configuration. |
| [isActive](arkts-automaticsceneconfiguration-assessment-isactive-f.md#isactive-1) | Queries whether an assessment session is active. |

### Interfaces

| Name | Description |
| --- | --- |
| [AssessmentConfig](arkts-automaticsceneconfiguration-assessment-assessmentconfig-i.md) | Assessment scenario configuration information. |
| [AssessmentError](arkts-automaticsceneconfiguration-assessment-assessmenterror-i.md) | Assessment error information. |
| [AssessmentInterruptInfo](arkts-automaticsceneconfiguration-assessment-assessmentinterruptinfo-i.md) | Assessment interrupt information. |
| [IAssessmentCallback](arkts-automaticsceneconfiguration-assessment-iassessmentcallback-i.md) | Assessment callback interface. |

### Enums

| Name | Description |
| --- | --- |
| [AssessmentErrorCode](arkts-automaticsceneconfiguration-assessment-assessmenterrorcode-e.md) | Assessment error code. |
