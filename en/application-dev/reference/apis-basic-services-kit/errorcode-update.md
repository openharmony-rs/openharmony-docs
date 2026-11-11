# Update Error Codes
<!--Kit: Basic Services Kit-->
<!--Subsystem: Update-->
<!--Owner: @RainyDay_005; @huangsiping3-->
<!--Designer: @zhangzhengxue; @jackd320-->
<!--Tester: @mamba-ting-->
<!--Adviser: @fang-jinxu-->
<!-- md-trans-meta sourceCommit=a2b11cb9ad5cf80fecbaf1af3bdcb5eed45d81ac translatedAt=2026-11-10T04:00:05.931Z pushedAt=2026-11-10T06:07:41.874Z nl=1 -->

> **NOTE**
>
> This module defines the error codes that may be returned by the Update Service and the corresponding handling suggestions. It mainly covers IPC communication errors that occur when calling Update Service APIs, helping developers quickly locate and resolve upgrade issues such as system upgrade failures, firmware update exceptions, and application version management errors.
>
> Applicable scenarios: system upgrade, firmware update, application version management, and so on. These help developers integrate upgrade capabilities, monitor upgrade status, handle upgrade errors, and improve system maintainability and user experience.
>
> This document describes only the error codes related to the update module. For general error codes, see [Universal Error Code Description](../errorcode-universal.md).

## Error Code List

| Error Code ID | Error Message | Description | Possible Causes | Handling Suggestions |
| --- | --- | --- | --- | --- |
| 11500104 | IPC error | IPC communication error that occurs when calling the update service APIs in scenarios such as system upgrade and firmware update. | 1. The update service fails to start or exits abnormally.<br>2. The service process crashes abnormally and fails to be restarted. | 1. Run `hidumper -s 3006` to check whether the update service is running.<br>2. If it is not started, restart the device or start the service by going to **Settings > System & updates > Software update**.<br>3. Check the hilog logs, search for the `SA:3006` keyword, and analyze the service running status.<br>4. If the service is running properly, search for the `C02E00` keyword to analyze the specific cause of the IPC communication error.<br>5. Based on the analysis result, release system resources, check the permission configuration, and restart the related service or the update service process. |

## Related APIs

When the following APIs are called, error code 11500104 (IPC error) may be returned if the update service is not started or exits abnormally:

- `checkNewVersion`
- `getNewVersionInfo`
- `getNewVersionDescription`
- `getCurrentVersionInfo`
- `getCurrentVersionDescription`
- `getTaskInfo`
- `download`
- `pauseDownload`
- `resumeDownload`
- `upgrade`
- `clearError`
- `getUpgradePolicy`
- `setUpgradePolicy`
- `terminateUpgrade`
- `factoryReset`
- `forceFactoryReset`
- `deepFactoryReset`
- `getDeepFactoryResetInfo`
- `verifyUpgradePackage`
- `applyNewVersion`

For details, see **@ohos.update (Update) (System API)**.