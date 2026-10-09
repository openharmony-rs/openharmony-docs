# Getting Started
<!--Kit: Connectivity Kit-->
<!--Subsystem: Communication-->
<!--Owner: @CCCZKing-->
<!--Designer: @lilong32; @CCCZKing-->
<!--Tester: @zhangjiaji111-->
<!--Adviser: @zhang_yixin13-->
<!-- md-trans-meta sourceCommit=0458a0f5fa8bb493715466c0613b81e48e740e33 translatedAt=2026-09-29T11:00:52.368Z pushedAt=2026-09-30T06:34:31.310Z -->

Before developing a NearLink application, complete preparations such as device confirmation, environment setup, and permission request. You can also use the query APIs to confirm that the device supports NearLink and that the NearLink switch is turned on. Before development, you are advised to read the descriptions of service UUIDs, event subscription, SSAP property descriptors, and device addresses in [NearLink FAQs](nearlink-faq-guide.md).

## Pre-Development Check

1. First, confirm that the device supports NearLink. To confirm, go to **Settings > NearLink & Bluetooth** (on some products or system versions, this may be **Settings > Multi-Device Collaboration**) and check whether the **NearLink** option is present. If the option is absent, the device does not support NearLink.
2. Refer to [Application Development Preparation](https://developer.huawei.com/consumer/en/develop-novice-guide/) to complete basic preparations such as developer registration, application creation, development environment setup, and signing information configuration before proceeding with the following development activities.

## Requesting NearLink Permissions

You need to dynamically request the NearLink permission `ohos.permission.ACCESS_NEARLINK` in your application, including declaring the permission in the application configuration file and requesting authorization from the user. This permission uses the user_grant authorization mode. The procedure is as follows:

1. Declare the permission in the `module.json5` configuration file. For details, see [Declaring Permissions](../../security/AccessToken/declare-permissions.md).
2. Request authorization from the user when the application starts. For details, see [Requesting User Authorization](../../security/AccessToken/request-user-authorization.md).

> **NOTE**
>
> - It is recommended that you complete the permission request once when the Ability is created and check the authorization result (`authResults`). If the user rejects the request, calling a NearLink API that requires the `ohos.permission.ACCESS_NEARLINK` permission returns error 201 (API permission verification failed).
> - For the permission behavior of event subscription APIs, see [NearLink FAQs > Permission Requirements for Event Subscription APIs](nearlink-faq-guide.md#permission-requirements-for-event-subscription-apis). Subscribing without the permission does not report an error, but no events are received.

## Querying Whether a Device Supports NearLink

Since not all devices support NearLink, you can actively query whether the current device supports NearLink before using NearLink-related features.

### Available APIs

The following table lists the API for querying whether a device supports NearLink. For the complete API description and sample code, see [@ohos.nearlink.manager (Basic NearLink Management Capability)](../../reference/apis-connectivity-kit/js-apis-nearlink-manager.md).

| API | Description |
| -------- | -------- |
| isNearLinkSupported(): boolean | Actively queries whether the current device supports NearLink. |

### How to Develop

1. Import the required modules.

    <!-- @[manager_module_import](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ConnectivityKit/NearLink/entry/src/main/ets/nearlink/pages/ManagerPage.ets) -->

    ```ts
    import { hilog } from '@kit.PerformanceAnalysisKit';
    import { BusinessError } from '@kit.BasicServicesKit';
    import { manager } from '@kit.ConnectivityKit';
    ```

2. Query whether the current device supports NearLink.

    <!-- @[manager_issupported](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ConnectivityKit/NearLink/entry/src/main/ets/nearlink/pages/ManagerPage.ets) -->
    
    ``` TypeScript
    try {
      let supported: boolean = manager.isNearLinkSupported();
      // ...
    } catch (err) {
      hilog.error(0x0000, 'testTag',
        `errCode: ${(err as BusinessError).code}, errMessage: ${(err as BusinessError).message}`);
    }
    ```

## Querying the NearLink Switch State

Before using NearLink, you must manually enable NearLink in **Settings**. You can obtain the NearLink switch state through active query or event subscription. When the NearLink switch state changes to `STATE_ON`, you can proceed with the corresponding service process.

### Available APIs

Two methods are provided for obtaining the NearLink switch state: active query and event subscription. For the complete API description and sample code, see [@ohos.nearlink.manager (Basic NearLink Management Capabilities)](../../reference/apis-connectivity-kit/js-apis-nearlink-manager.md).

| API | Description |
| -------- | -------- |
| getState(): NearlinkState | Actively queries the NearLink switch state. |
| onStateChange(callback: Callback&lt;NearlinkState&gt;): void | Subscribes to NearLink switch state change events. This API uses a callback to return the result asynchronously. |
| offStateChange(callback?: Callback&lt;NearlinkState&gt;): void | Unsubscribes from NearLink switch state change events. This API uses a callback to return the result asynchronously. |

### How to Develop

1. Import the required modules.

    <!-- @[manager_module_import](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ConnectivityKit/NearLink/entry/src/main/ets/nearlink/pages/ManagerPage.ets) -->
    
    ``` TypeScript
    import { hilog } from '@kit.PerformanceAnalysisKit';
    import { BusinessError } from '@kit.BasicServicesKit';
    import { manager } from '@kit.ConnectivityKit';
    ```

2. Query the NearLink switch state.

    <!-- @[manager_getstate](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ConnectivityKit/NearLink/entry/src/main/ets/nearlink/pages/ManagerPage.ets) -->
    
    ``` TypeScript
    try {
      let state: manager.NearlinkState = manager.getState();
      // ...
    } catch (err) {
      hilog.error(0x0000, 'testTag',
        `errCode: ${(err as BusinessError).code}, errMessage: ${(err as BusinessError).message}`);
    }
    ```

3. Subscribe to NearLink switch state changes.

    <!-- @[manager_on_state_change](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ConnectivityKit/NearLink/entry/src/main/ets/nearlink/pages/ManagerPage.ets) -->
    
    ``` TypeScript
    try {
      manager.onStateChange((state: manager.NearlinkState) => {
        hilog.info(0x0000, 'testTag', `NearLink state changed: ${state}`);
        // ...
      });
    } catch (err) {
      hilog.error(0x0000, 'testTag',
        `errCode: ${(err as BusinessError).code}, errMessage: ${(err as BusinessError).message}`);
    }
    ```

4. Unsubscribe from NearLink switch state changes.

    <!-- @[manager_off_state_change](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ConnectivityKit/NearLink/entry/src/main/ets/nearlink/pages/ManagerPage.ets) -->
    
    ``` TypeScript
    try {
      manager.offStateChange();
    } catch (err) {
      hilog.error(0x0000, 'testTag',
        `errCode: ${(err as BusinessError).code}, errMessage: ${(err as BusinessError).message}`);
    }
    ```
