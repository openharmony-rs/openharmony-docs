# AssessmentConfig

```TypeScript
interface AssessmentConfig
```

Assessment scenario configuration information.

**Since:** 26.0.1

<!--Device-assessment-interface AssessmentConfig--><!--Device-assessment-interface AssessmentConfig-End-->

**System capability:** SystemCapability.Customization.AssessmentConfiguration

## Modules to Import

```TypeScript
```

## allowedApps

```TypeScript
allowedApps: Array<string>
```

List of application bundle names allowed to run during the assessment (whitelist).

**Type:** Array&lt;string&gt;

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-AssessmentConfig-allowedApps: Array<string>--><!--Device-AssessmentConfig-allowedApps: Array<string>-End-->

**System capability:** SystemCapability.Customization.AssessmentConfiguration

## duration

```TypeScript
duration: number
```

Maximum assessment duration (in milliseconds). The value 0 indicates no time limit.

**Type:** number

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-AssessmentConfig-duration: int--><!--Device-AssessmentConfig-duration: int-End-->

**System capability:** SystemCapability.Customization.AssessmentConfiguration
