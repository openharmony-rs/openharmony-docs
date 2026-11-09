# Assessment Management Development Guide

<!--Kit: Automatic Scene Configuration Kit-->
<!--Subsystem: Customization-->
<!--Owner: @weredust-->
<!--Designer: @weredust-->
<!--Tester: @weredust-->
<!--Adviser: @weredust-->
<!-- md-trans-meta sourceCommit=3194fdbc42d6357f420eb498f6d963c04a35b419 translatedAt=2026-11-06T12:35:54.128Z pushedAt=2026-11-09T12:10:00.564Z nl=1 -->

## Introduction

This document guides developers in integrating the assessment management capability to complete the development of starting an assessment, querying the assessment status, and ending an assessment. For the Kit-level capability scope and constraints, see [Automatic Scene Configuration Kit Introduction](assessment-kit-intro.md). For term definitions, see [Automatic Scene Configuration Kit Glossary](assessment-glossary.md).

The assessment management module provides the following capabilities:

- Start Assessment: Call the begin API to initiate an assessment. The system displays a confirmation dialog, and after user confirmation, the device enters assessment mode. You can specify the maximum assessment duration and the trustlist of applications allowed to run during the assessment through the assessment configuration.
- End Assessment: Call the end API to end the assessment. The system releases the restrictions on system capabilities in assessment mode.
- Assessment Status Query and Configuration Retrieval: Call the isActive API to query whether the device is currently in assessment status, and call the getConfiguration API to obtain the current assessment configuration.
- Assessment Process Callback: Receive assessment start (onBegin), assessment interruption (onInterrupted), and assessment end (onEnd) events through IAssessmentCallback.

## Constraints

After entering assessment mode, device functions are significantly restricted. To prevent third-party applications from abusing this capability, calling the assessment management APIs requires the permission [ohos.permission.ASSESSMENT_CONFIGURATION](../security/AccessToken/restricted-permissions.md#ohospermissionassessment_configuration).

**Table 1** Permission information

| Permission Name | Permission Level | Authorization Mode | Application Open Scope |
| -------- | -------- | -------- | -------- |
| ohos.permission.ASSESSMENT_CONFIGURATION | system_basic | system_grant | Normal application |

This permission is a restricted permission. An application can obtain it only after approval. For the request method, see [Requesting Restricted Permissions](../security/AccessToken/declare-permissions-in-acl.md). Approval must satisfy the following rules:

1. The application entity is an enterprise, educational institution, or formal examination service provider. Applications from individual accounts are not supported.
2. The application's secondary category in the application market is Education.
3. The core purpose of the application is high-risk formal examination or assessment scenarios (such as academic proficiency tests, professional certification, and standardized tests). It is not used for ordinary classroom exercises, check-in, attendance, question drilling, screen recording monitoring, or similar scenarios. When applying, page screenshots of the examination scenario must be provided.
4. The application has no historical violations, and the developer account has no records of serious review violations, fraud, or cheating.

Other constraints are as follows:

- Starting an assessment requires user confirmation in the confirmation dialog. If the user cancels, the assessment will not start.
- Only one ongoing assessment is allowed on the same device at the same time. Calling the begin API again while already in the assessment state will report an error.
- Only the application that started the assessment can end it. Calling the end API to end an assessment started by another application will report an error.

The specification constraints of the assessment configuration are as follows:

- The maximum value of duration is 8 hours (28800000 milliseconds). Values exceeding this limit take effect at the upper limit. When the value is 0, the default duration of 8 hours is applied.
- allowedApps supports configuring up to 20 application bundle names, and the total length of all concatenated bundle names must not exceed 2048 characters.

## Development Process

1. Request the permission ohos.permission.ASSESSMENT_CONFIGURATION in the configuration file.
2. Import the assessment management module.
3. Configure the assessment parameters, call the begin API to start the assessment, and register the assessment process callback.
4. As required by the business, call the isActive and getConfiguration APIs to query the assessment status and configuration.
5. After the assessment is complete, call the end API to end the assessment.

## Available APIs

The key APIs of assessment management are shown in the following table. For details about the APIs, see [@ohos.customization.assessment (Assessment Management)](../reference/apis-assessment-kit/js-apis-customization-assessment.md).

**Table 2** Assessment management API functions

| API | Description |
| -------- | -------- |
| [begin(context, config, callback)](../reference/apis-assessment-kit/js-apis-customization-assessment.md#assessmentbegin): void | Starts the assessment, displays a confirmation dialog, and enters assessment mode after user confirmation. |
| [end(context)](../reference/apis-assessment-kit/js-apis-customization-assessment.md#assessmentend): void | Ends the assessment and removes the restrictions on system capabilities in assessment mode. |
| [isActive()](../reference/apis-assessment-kit/js-apis-customization-assessment.md#assessmentisactive): boolean | Queries whether the device is currently in the assessment state. |
| [getConfiguration()](../reference/apis-assessment-kit/js-apis-customization-assessment.md#assessmentgetconfiguration): AssessmentConfig | Obtains the current assessment configuration. |

## How to Develop

### Request Permission

In the module.json5 file of the module, request the permission [ohos.permission.ASSESSMENT_CONFIGURATION](../security/AccessToken/restricted-permissions.md#ohospermissionassessment_configuration). This permission is a system_basic-level system_grant restricted permission. You must first complete the application by following [Request Restricted Permission](../security/AccessToken/declare-permissions-in-acl.md). After declaration, it is automatically granted when the application is installed. For details about declaring permissions, see [Declare Permission](../security/AccessToken/declare-permissions.md). The example is as follows:

```json5
{
  "module": {
    "requestPermissions": [
      {
        "name": "ohos.permission.ASSESSMENT_CONFIGURATION"
      }
    ]
  }
}
```

### Import the Assessment Management Module

After importing the assessment module, you can call the Assessment Management APIs.

```ts
import { assessment } from '@kit.AutomaticSceneConfigurationKit';
```

### Start Assessment

Configure the assessment parameters, call the begin API to start the assessment, and register the assessment process callback through IAssessmentCallback.

After begin is called, the system displays a confirmation dialog. The assessment can start only after the user confirms. The assessment result and the interruption and end events during the assessment are all notified through the callback. For how to obtain the context, see [Context Acquisition Method](../application-models/application-context-stage.md#acquisition-of-context). The sample code is as follows:

```ts
import { common } from '@kit.AbilityKit';
import { assessment } from '@kit.AutomaticSceneConfigurationKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

const DOMAIN: number = 0xFF00;
const TAG: string = '[Sample_Assessment]';

// Assessment process callback.
const assessmentCallback: assessment.IAssessmentCallback = {
  onBegin: (error: assessment.AssessmentError): void => {
    // AssessmentError.message is an optional field. Perform a null check before reading its value.
    const message: string = error.message ?? '';
    if (error.code === assessment.AssessmentErrorCode.OK) {
      hilog.info(DOMAIN, TAG, '%{public}s', `onBegin, assessment began successfully, message: ${message}`);
    } else {
      hilog.error(DOMAIN, TAG, '%{public}s',
        `onBegin, assessment begin failed, code: ${error.code}, message: ${message}`);
    }
  },
  onInterrupted: (info: assessment.AssessmentInterruptInfo): void => {
    // The assessment is interrupted. The service side can handle it based on the interruption reason code, such as saving the answer records.
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
    // Obtain the context within the component and ensure that this.getUIContext().getHostContext() returns UIAbilityContext.
    const host: common.Context | undefined = this.getUIContext().getHostContext();
    if (host === undefined) {
      hilog.error(DOMAIN, TAG, '%{public}s', 'begin failed, the host context is undefined');
      return;
    }
    const context: common.UIAbilityContext = host as common.UIAbilityContext;
    // Assessment configuration: maximum duration 1 hour (3600000 milliseconds);
    // During the assessment, allow the application with the package name com.samples.assessment to run.
    const config: assessment.AssessmentConfig = {
      duration: 3600000,
      allowedApps: ['com.samples.assessment']
    };
    try {
      assessment.begin(context, config, assessmentCallback);
      hilog.info(DOMAIN, TAG, '%{public}s', 'begin called, waiting for user confirmation');
    } catch (error) {
      const err: BusinessError = error as BusinessError;
      hilog.error(DOMAIN, TAG, '%{public}s', `begin failed, code: ${err.code}, message: ${err.message}`);
    }
  }
}
```

### Query Assessment Status and Configuration

During assessment, call the isActive API to query the current assessment status, and call the getConfiguration API to obtain the current assessment configuration. The sample code is as follows:

```ts
import { assessment } from '@kit.AutomaticSceneConfigurationKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

const DOMAIN: number = 0xFF00;
const TAG: string = '[Sample_Assessment]';

try {
  const active: boolean = assessment.isActive();
  hilog.info(DOMAIN, TAG, '%{public}s', `isActive result: ${active}`);
  if (active) {
    const config: assessment.AssessmentConfig = assessment.getConfiguration();
    hilog.info(DOMAIN, TAG, '%{public}s',
      `getConfiguration result, duration: ${config.duration}, allowedApps: ${config.allowedApps.join(',')}`);
  }
} catch (error) {
  const err: BusinessError = error as BusinessError;
  hilog.error(DOMAIN, TAG, '%{public}s', `query failed, code: ${err.code}, message: ${err.message}`);
}
```

### End Assessment

After the assessment is complete, the application that started the assessment calls the end API to end the assessment. The system releases the restrictions on system capabilities in assessment mode and triggers the onEnd callback. The sample code is as follows:

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
    // Obtain the context within the component, and ensure that this.getUIContext().getHostContext() returns UIAbilityContext.
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

## Application-Side Hardening Suggestions

The assessment mode centrally manages some system capabilities, but the application window form, screen capture and screen recording of the application window, the clipboard, and the input method panel are outside the scope of system management. The application must harden these aspects on its own to prevent assessment content from leaking or being used for cheating through external input. It is recommended to enable hardening uniformly when entering the assessment page and restore it when exiting the assessment page.

**Table 3** Application-side hardening measures

| Hardening Measure | API | Description |
| -------- | -------- | -------- |
| Immersive window | setWindowLayoutFullScreen | Extends content to the status bar and navigation bar areas, reducing exposure of system entries outside the assessment page |
| Privacy mode | setWindowPrivacyMode | Prevents the window from being captured or recorded, and displays a privacy mask in the recent tasks view when the app goes to the background |
| Clear clipboard | clearData | Clears residual clipboard data to prevent answers from being passed in through the clipboard |
| Simple keyboard mode | setSimpleKeyboardEnabled | Keeps only basic keys in the input method panel and collapses the candidate bar and extended function entries |

Privacy mode requires the permission ohos.permission.PRIVACY_WINDOW, which is a normal-level system_grant permission. Its declaration method is the same as that in [Request Permission](#request-permission). Window-related APIs require obtaining the current window first. The key implementation of hardening and restoration is as follows:

```ts
import { common } from '@kit.AbilityKit';
import { window } from '@kit.ArkUI';
import { BusinessError, pasteboard } from '@kit.BasicServicesKit';
import { inputMethod } from '@kit.IMEKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

const DOMAIN: number = 0xFF00;
const TAG: string = '[Sample_Assessment]';

export class ExamHardeningUtil {
  // Enable all hardening measures when entering the assessment page.
  public static async applyHardening(context: common.UIAbilityContext): Promise<void> {
    await ExamHardeningUtil.setWindowHardening(context, true);
    ExamHardeningUtil.setSimpleKeyboard(true);
    await ExamHardeningUtil.clearPasteboard();
  }

  // Restore the window form and input method when exiting the assessment page, and clear the clipboard again.
  public static async releaseHardening(context: common.UIAbilityContext): Promise<void> {
    await ExamHardeningUtil.setWindowHardening(context, false);
    ExamHardeningUtil.setSimpleKeyboard(false);
    await ExamHardeningUtil.clearPasteboard();
  }

  // Catch exceptions for the two window measures separately so that a failure in one does not affect the other.
  private static async setWindowHardening(context: common.UIAbilityContext, enable: boolean): Promise<void> {
    let currentWindow: window.Window | undefined = undefined;
    try {
      currentWindow = await window.getLastWindow(context);
    } catch (error) {
      const err: BusinessError = error as BusinessError;
      hilog.error(DOMAIN, TAG, '%{public}s', `getLastWindow failed, code: ${err.code}, message: ${err.message}`);
    }
    if (currentWindow === undefined) {
      return;
    }
    try {
      await currentWindow.setWindowLayoutFullScreen(enable);
    } catch (error) {
      const err: BusinessError = error as BusinessError;
      hilog.error(DOMAIN, TAG, '%{public}s',
        `setWindowLayoutFullScreen failed, code: ${err.code}, message: ${err.message}`);
    }
    try {
      await currentWindow.setWindowPrivacyMode(enable);
    } catch (error) {
      const err: BusinessError = error as BusinessError;
      hilog.error(DOMAIN, TAG, '%{public}s',
        `setWindowPrivacyMode failed, code: ${err.code}, message: ${err.message}`);
    }
  }

  // setSimpleKeyboard calls inputMethod.setSimpleKeyboardEnabled,
  // clearPasteboard calls pasteboard.getSystemPasteboard().clearData, and both also catch exceptions separately.
  // ...
}
```

Call the hardening and restoration APIs in the lifecycle of the assessment page. The sample code is as follows:

```ts
aboutToAppear(): void {
  this.applyHardening();
}

aboutToDisappear(): void {
  this.releaseHardening();
}

private applyHardening(): void {
  const context: common.UIAbilityContext | undefined = this.getAbilityContext();
  if (context === undefined) {
    return;
  }
  ExamHardeningUtil.applyHardening(context).catch((error: BusinessError) => {
    hilog.error(DOMAIN, TAG, '%{public}s', `applyHardening failed, code: ${error.code}, message: ${error.message}`);
  });
}
```

For the complete implementation, see [Samples](#samples).

## Debugging and Verification

1. After the begin API is called, the device displays the assessment confirmation dialog. After the user confirms, the device enters assessment mode, system capabilities are restricted, and the onBegin callback returns code 0 (OK).

2. Call the isActive API, which returns true, indicating that the device is currently in the assessment state.

3. Try to open an application that is not in the allowedApps trustlist, and verify that it cannot run during assessment.

4. Call the end API to end the assessment. The isActive API returns false, the system capability restrictions are released, and the onEnd callback is triggered.

## FAQs

### How to Design the allowedApps Trustlist to Ensure Business Availability During Assessment

allowedApps is used to specify the package names of applications allowed to run during assessment. Applications not in the trustlist cannot run during assessment. The following principles are recommended when designing the trustlist:

- Add applications that must be used during the assessment to the trustlist, such as the input method and accessibility assistance applications that an exam application depends on, as well as the audio playback application required for listening assessment.
- The package name of the application that initiates the assessment must be added to allowedApps. When begin is called, the application is in the foreground. If it is not in the trustlist, the environment check before starting the assessment fails, and the assessment cannot start.

For the specific specification restrictions of the trustlist, see [Constraints](#constraints). For the configuration method, see [Start Assessment](#start-assessment).

### How Does the Assessment Exit When duration Is Set to 0

When duration is 0, the system processes it with the default duration, which is the same as the upper limit of duration. After this duration is reached, the assessment is interrupted due to timeout and the onInterrupted callback is triggered, with the interruption reason code TIMEOUT. For the specific value, see [Constraints](#constraints).

During the assessment, the application that started the assessment can also call the end API at any time to actively end the assessment. The system then releases the restrictions on system capabilities and triggers the onEnd callback. To prevent the assessment from occupying the device for a long time, it is recommended that you set duration based on the actual answering time of the service. For details, see [End Assessment](#end-assessment).

### What Should an Application Do After Assessment Is Interrupted

The trigger timing of onEnd and onInterrupted differs: onEnd is triggered after the application calls the end API to end the assessment normally; onInterrupted is triggered when the assessment is actively interrupted by the system, carrying the interruption reason code and description information.

When the assessment is interrupted, the system has automatically released the restrictions on system capabilities. The application does not need to call the end API again. It is recommended to complete the following processing:

- Save business data such as answer records and remaining duration in the onInterrupted callback to avoid data loss.
- Handle differently based on the interruption reason code. For example, submit the answered content when exiting due to timeout, and prompt the user that the assessment has ended when the user cancels.
- If reassessment is required after interruption, call the begin API again to initiate it, and the user confirms it in the confirmation dialog.

### Why Does the Device Not Enter Assessment Mode Immediately After Calling begin

The device does not enter assessment mode immediately after the begin API is called successfully. The system first displays a confirmation dialog. The device enters assessment mode only after the user confirms in the dialog. If the user cancels, the assessment does not start.

The return value of the begin API only indicates that the request has been submitted. Whether the assessment actually starts must be determined through the onBegin callback: a code of OK in the callback indicates that the assessment has started, and USER_CANCEL indicates that the user has canceled. It is recommended that you update the UI state and start business timing in the onBegin callback. For the configuration method, see [Start Assessment](#start-assessment).

## Samples

For assessment management development, the following related examples are available for reference:

- [Assessment Management (ArkTS)](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/AutomaticSceneConfigurationKit/Assessment)
