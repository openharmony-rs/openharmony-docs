# @ohos.customization.assessment (Assessment Management)

<!--Kit: Automatic Scene Configuration Kit-->
<!--Subsystem: Customization-->
<!--Owner: @weredust-->
<!--Designer: @weredust-->
<!--Tester: @weredust-->
<!--Adviser: @weredust-->
<!-- md-trans-meta sourceCommit=cc14201ef7bc3a53ad0dcc67c17be18bdbb0041d translatedAt=2026-11-04T11:59:07.817Z pushedAt=2026-11-04T12:06:27.018Z nl=1 -->

The Assessment Management module provides assessment scenario management capabilities, including starting an assessment, ending an assessment, querying the assessment status, obtaining the assessment configuration, and callbacks during the assessment process. When an application needs to enter an exam scenario, it can call the begin API to start the assessment. The system then displays a dialog to remind the user. After the user confirms entering the assessment mode, some system capabilities are restricted to prevent exam cheating or information leakage. After the assessment ends or is interrupted, the end API can be called to exit the assessment mode, ensuring exam fairness while protecting user rights.

**Since:** 26.0.1

## Modules to Import

```ts
import { assessment } from '@kit.AutomaticSceneConfigurationKit';
```

## AssessmentConfig

Assessment scenario configuration information.

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**System Capability**: SystemCapability.Customization.AssessmentConfiguration

| Name | Type | Read-Only | Optional | Description |
| -------- | -------- | -------- | -------- | -------- |
| duration | number | No | No | Maximum duration of the assessment, in milliseconds. The value ranges from 0 to 28800000 (that is, 0 to 8 hours). A value exceeding 8 hours takes effect as 8 hours. A value of 0 is processed as the default duration of 8 hours. |
| allowedApps | Array\<string\> | No | No | List of application package names allowed to run during the assessment period (allowlist). A maximum of 20 package names can be configured, and the total length of all concatenated package names must not exceed 2048 characters. |

## AssessmentErrorCode

Enumerates the assessment error codes.

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**System Capability**: SystemCapability.Customization.AssessmentConfiguration

| Name | Value | Description |
| -------- | -------- | -------- |
| OK | 0 | Success. |
| USER_CANCEL | 1 | Indicates that the user cancels. |
| TIMEOUT | 2 | Indicates timeout exit. |
| SYSTEM_ERROR | 3 | Indicates a system error. |
| ENV_ANOMALY | 4 | Indicates an environment anomaly. |

## AssessmentError

Assessment error information.

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**System Capability**: SystemCapability.Customization.AssessmentConfiguration

| Name | Type | Read-Only | Optional | Description |
| -------- | -------- | -------- | -------- | -------- |
| code | [AssessmentErrorCode](#assessmenterrorcode) | No | No | Error code. 0 indicates success, and a non-zero value indicates failure. |
| message | string | No | Yes | Error description information. This is an optional field. If not provided, it defaults to an empty string. |

## AssessmentInterruptInfo

Assessment interruption information.

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**System Capability**: SystemCapability.Customization.AssessmentConfiguration

| Name | Type | Read-Only | Optional | Description |
| -------- | -------- | -------- | -------- | -------- |
| code | [AssessmentErrorCode](#assessmenterrorcode) | No | No | Interruption reason code. |
| message | string | No | No | Detailed description of the interruption reason. |

## IAssessmentCallback

Assessment process callback interface, used to receive callbacks for assessment start, interrupt, and end events.

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**System Capability**: SystemCapability.Customization.AssessmentConfiguration

### onBegin

onBegin(error: AssessmentError): void

Callback invoked when the assessment starts.

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**System Capability**: SystemCapability.Customization.AssessmentConfiguration

**Parameters**

| Name | Type | Mandatory | Description |
| -------- | -------- | -------- | -------- |
| error | [AssessmentError](#assessmenterror) | Yes | Assessment error information. A code of 0 (OK) indicates that the assessment started successfully, and a non-zero code indicates that the assessment failed to start. |

### onInterrupted

onInterrupted(info: AssessmentInterruptInfo): void

Callback invoked when the assessment is interrupted. It is triggered when the assessment process is interrupted due to user cancellation, timeout exit, system error, security violation, or other reasons.

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**System Capability**: SystemCapability.Customization.AssessmentConfiguration

**Parameters**

| Name | Type | Mandatory | Description |
| -------- | -------- | -------- | -------- |
| info | [AssessmentInterruptInfo](#assessmentinterruptinfo) | Yes | Assessment interruption information, including the interruption reason code and the detailed description of the interruption reason. |

### onEnd

onEnd(): void

Callback when the assessment ends.

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**System Capability**: SystemCapability.Customization.AssessmentConfiguration

## assessment.begin

begin(context: UIAbilityContext, config: AssessmentConfig, callback: IAssessmentCallback): void

Starts an assessment. After this API is called, a confirmation dialog box is displayed, and the assessment starts only after the user confirms. The assessment result and the interruption and end events during the assessment are notified through the callback.

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**Permission required**: ohos.permission.ASSESSMENT_CONFIGURATION

**System Capability**: SystemCapability.Customization.AssessmentConfiguration

**Parameters**

| Name | Type | Mandatory | Description |
| -------- | -------- | -------- | -------- |
| context | [UIAbilityContext](../apis-ability-kit/js-apis-inner-application-uiAbilityContext.md) | Yes | Context of the application that needs to enter the assessment mode. |
| config | [AssessmentConfig](#assessmentconfig) | Yes | Assessment configuration, including the maximum assessment duration and the trustlist of applications allowed to run during the assessment. |
| callback | [IAssessmentCallback](#iassessmentcallback) | Yes | Assessment process callback, used to receive the assessment start, interruption, and end events. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Assessment Management Error Codes](errorcode-assessment.md).

| Error Code | Error Message |
| -------- | -------- |
| 201 | Permission denied. |
| 801 | Capability not supported. |
| 36700001 | Assessment internal error. Possible cause: IPC invocation failed internally. |
| 36700002 | Assessment configuration service is already active. Possible cause: Assessment resource conflict. |

**Example**

```ts
import { common } from '@kit.AbilityKit';
import { assessment } from '@kit.AutomaticSceneConfigurationKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

const DOMAIN: number = 0xFF00;
const TAG: string = '[Sample_Assessment]';

// Assessment process callback. Handle the onBegin, onInterrupted, and onEnd events in a unified manner.
const callback: assessment.IAssessmentCallback = {
  onBegin: (error: assessment.AssessmentError): void => {
    // AssessmentError.message is an optional field. Perform a null check before accessing its value.
    const message: string = error.message ?? '';
    if (error.code === assessment.AssessmentErrorCode.OK) {
      hilog.info(DOMAIN, TAG, '%{public}s', `onBegin, assessment began successfully, message: ${message}`);
    } else {
      hilog.error(DOMAIN, TAG, '%{public}s',
        `onBegin, assessment begin failed, code: ${error.code}, message: ${message}`);
    }
  },
  onInterrupted: (info: assessment.AssessmentInterruptInfo): void => {
    // The assessment is interrupted. The service side can handle it based on the interruption reason code, such as saving the answer records and then exiting the exam page.
    hilog.warn(DOMAIN, TAG, '%{public}s', `onInterrupted, code: ${info.code}, message: ${info.message}`);
  },
  onEnd: (): void => {
    hilog.info(DOMAIN, TAG, '%{public}s', 'onEnd, assessment ended');
  }
};

@Entry
@Component
struct Index {
  build() {
    Button('Start Assessment')
      .onClick(() => {
        this.beginAssessment();
      })
  }

  private beginAssessment(): void {
    // Obtain the context within the component, and ensure that this.getUIContext().getHostContext() returns UIAbilityContext.
    const host: common.Context | undefined = this.getUIContext().getHostContext();
    if (host === undefined) {
      hilog.error(DOMAIN, TAG, '%{public}s', 'begin failed, the host context is undefined');
      return;
    }
    const context: common.UIAbilityContext = host as common.UIAbilityContext;
    // Assessment configuration: maximum duration of 1 hour (3600000 milliseconds);
    // During assessment, the application with the package name com.samples.assessment is allowed to run.
    const config: assessment.AssessmentConfig = {
      duration: 3600000,
      allowedApps: ['com.samples.assessment']
    };
    try {
      assessment.begin(context, config, callback);
      hilog.info(DOMAIN, TAG, '%{public}s',
        `begin called, duration: ${config.duration}, allowedApps: ${config.allowedApps.join(',')}`);
    } catch (error) {
      const err: BusinessError = error as BusinessError;
      hilog.error(DOMAIN, TAG, '%{public}s', `begin failed, code: ${err.code}, message: ${err.message}`);
    }
  }
}
```

## assessment.end

end(context: UIAbilityContext): void

Ends the assessment and removes the restrictions on system capabilities in assessment mode.

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**Permission required**: ohos.permission.ASSESSMENT_CONFIGURATION

**System Capability**: SystemCapability.Customization.AssessmentConfiguration

**Parameters**

| Name | Type | Mandatory | Description |
| -------- | -------- | -------- | -------- |
| context | [UIAbilityContext](../apis-ability-kit/js-apis-inner-application-uiAbilityContext.md) | Yes | Application context that needs to exit assessment mode. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Assessment Management Error Codes](errorcode-assessment.md).

| Error Code | Error Message |
| -------- | -------- |
| 201 | Permission denied. |
| 801 | Capability not supported. |
| 36700001 | Assessment internal error. Possible cause: IPC invocation failed internally. |
| 36700003 | Assessment configuration service is not active. Possible cause: Not in assessment state. |
| 36700004 | Invalid operation. Possible cause: Cannot terminate another active assessment. |

**Example**

```ts
import { common } from '@kit.AbilityKit';
import { assessment } from '@kit.AutomaticSceneConfigurationKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

const DOMAIN: number = 0xFF00;
const TAG: string = '[Sample_Assessment]';

@Entry
@Component
struct Index {
  build() {
    Button('Submit')
      .onClick(() => {
        this.endAssessment();
      })
  }

  // End the assessment started by the current application. Only the application that started the assessment can end it.
  private endAssessment(): void {
    // Obtain the context within the component to ensure that this.getUIContext().getHostContext() returns UIAbilityContext.
    const host: common.Context | undefined = this.getUIContext().getHostContext();
    if (host === undefined) {
      hilog.error(DOMAIN, TAG, '%{public}s', 'end failed, the host context is undefined');
      return;
    }
    const context: common.UIAbilityContext = host as common.UIAbilityContext;
    try {
      assessment.end(context);
      hilog.info(DOMAIN, TAG, '%{public}s', 'end called');
    } catch (error) {
      const err: BusinessError = error as BusinessError;
      hilog.error(DOMAIN, TAG, '%{public}s', `end failed, code: ${err.code}, message: ${err.message}`);
    }
  }
}
```

## assessment.isActive

isActive(): boolean

Queries whether the device is currently in the assessment state.

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**Permission required**: ohos.permission.ASSESSMENT_CONFIGURATION

**System Capability**: SystemCapability.Customization.AssessmentConfiguration

**Return value**

| Type | Description |
| -------- | -------- |
| boolean | Returns true if the device is in the assessment state; returns false otherwise. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| Error Code | Error Message |
| -------- | -------- |
| 201 | Permission denied. |
| 801 | Capability not supported. |

**Example**

```ts
import { assessment } from '@kit.AutomaticSceneConfigurationKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

const DOMAIN: number = 0xFF00;
const TAG: string = '[Sample_Assessment]';

// Query whether the device is currently in the assessment state. Returns true if in assessment mode.
function queryActive(): boolean {
  try {
    const active: boolean = assessment.isActive();
    hilog.info(DOMAIN, TAG, '%{public}s', `isActive result: ${active}`);
    return active;
  } catch (error) {
    const err: BusinessError = error as BusinessError;
    hilog.error(DOMAIN, TAG, '%{public}s', `isActive failed, code: ${err.code}, message: ${err.message}`);
    return false;
  }
}
```

## assessment.getConfiguration

getConfiguration(): AssessmentConfig

Obtains the current assessment configuration.

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**Permission required**: ohos.permission.ASSESSMENT_CONFIGURATION

**System Capability**: SystemCapability.Customization.AssessmentConfiguration

**Return value**

| Type | Description |
| -------- | -------- |
| [AssessmentConfig](#assessmentconfig) | Current assessment configuration, including the maximum assessment duration and the trustlist of applications allowed to run during the assessment period. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| Error Code | Error Message |
| -------- | -------- |
| 201 | Permission denied. |
| 801 | Capability not supported. |

**Example**

```ts
import { assessment } from '@kit.AutomaticSceneConfigurationKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

const DOMAIN: number = 0xFF00;
const TAG: string = '[Sample_Assessment]';

// Query the current assessment configuration. Returns undefined if the query fails.
function queryConfiguration(): assessment.AssessmentConfig | undefined {
  try {
    const config: assessment.AssessmentConfig = assessment.getConfiguration();
    hilog.info(DOMAIN, TAG, '%{public}s',
      `getConfiguration duration: ${config.duration}, allowedApps: ${config.allowedApps.join(',')}`);
    return config;
  } catch (error) {
    const err: BusinessError = error as BusinessError;
    hilog.error(DOMAIN, TAG, '%{public}s', `getConfiguration failed, code: ${err.code}, message: ${err.message}`);
    return undefined;
  }
}
```
