# Obtaining NearLink Coordinated Devices Set Information
<!--Kit: Connectivity Kit-->
<!--Subsystem: Communication-->
<!--Owner: @CCCZKing-->
<!--Designer: @lilong32; @CCCZKing-->
<!--Tester: @zhangjiaji111-->
<!--Adviser: @zhang_yixin13-->
<!-- md-trans-meta sourceCommit=0331a80a2631c55d2d3d88a8180d5918e41aad9c translatedAt=2026-09-29T10:56:35.301Z pushedAt=2026-09-30T06:11:51.450Z -->

## Overview

A Coordinated Devices Set (CDS) is a collection in which multiple member devices collaboratively provide a specific service. For example, a pair of NearLink earbuds consists of a left earbud and a right earbud. When a paired peripheral device belongs to a CDS, the [getPairedDevices()](../../reference/apis-connectivity-kit/js-apis-nearlink-manager.md#managergetpaireddevices) API can obtain only the first paired member device in the set, and cannot directly obtain information about other member devices. As a set user, you can use the Coordinated Devices Set Management (CDSM) capability to obtain the complete information of all member devices in the CDS by actively querying or subscribing to notifications.

Before development, complete the permission declaration and runtime request as described in [Getting Started](nearlink-preparations-guide.md), ensure that NearLink is enabled on the device (see [Getting Started > Querying the NearLink Switch State](nearlink-preparations-guide.md#querying-the-nearlink-switch-state)), ensure that the paired device belongs to a CDS, and obtain the address of the member device in the set through [getPairedDevices()](../../reference/apis-connectivity-kit/js-apis-nearlink-manager.md#managergetpaireddevices).

## Available APIs

The following describes how to obtain CDS information, actively query information, and subscribe to information changes. For the complete API description and sample code, see [@ohos.nearlink.cdsm (CDSM Capability)](../../reference/apis-connectivity-kit/js-apis-nearlink-cdsm.md).

| API | Description |
| -------- | -------- |
| createCdsmClient(address: string): CdsmClient | Creates a CDS client instance. |
| getCdsmInfo(): CdsmInfo | Actively queries the information of all member devices in the CDS. |
| onCdsmInfoChange(callback: Callback&lt;CdsmInfo&gt;): void | Subscribes to the CDS information change event of a remote device. This API uses an asynchronous callback. |
| offCdsmInfoChange(callback?: Callback&lt;CdsmInfo&gt;): void | Unsubscribes from the CDS information change event of a remote device. This API uses an asynchronous callback. |

## How to Develop

1. Import the required modules.

    <!-- @[cdsm_module_import](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ConnectivityKit/NearLink/entry/src/main/ets/nearlink/pages/CdsmPage.ets) -->
    
    ``` TypeScript
    import { hilog } from '@kit.PerformanceAnalysisKit';
    import { BusinessError } from '@kit.BasicServicesKit';
    import { cdsm } from '@kit.ConnectivityKit';
    ```

2. Define the CDSM client variable and the device address variable for use in subsequent steps. Here, `deviceAddress` is the device address obtained through [getPairedDevices()](../../reference/apis-connectivity-kit/js-apis-nearlink-manager.md#managergetpaireddevices), and the device is a member device of the CDS.

    <!-- @[cdsm_declare](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ConnectivityKit/NearLink/entry/src/main/ets/nearlink/pages/CdsmPage.ets) -->
    
    ``` TypeScript
    let cdsmClient: cdsm.CdsmClient;
    let deviceAddress: string;
    ```

3. Create a CDS client instance.

    <!-- @[cdsm_create_client](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ConnectivityKit/NearLink/entry/src/main/ets/nearlink/pages/CdsmPage.ets) -->
    
    ``` TypeScript
    try {
      cdsmClient = cdsm.createCdsmClient(deviceAddress);
      // ...
    } catch (err) {
      hilog.error(0x0000, 'testTag',
        `errCode: ${(err as BusinessError).code}, errMessage: ${(err as BusinessError).message}`);
      // ...
    }
    ```

4. Actively queries the information of all member devices in the CDS.

    <!-- @[cdsm_get_info](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ConnectivityKit/NearLink/entry/src/main/ets/nearlink/pages/CdsmPage.ets) -->
    
    ``` TypeScript
    try {
      let cdsmInfo: cdsm.CdsmInfo = cdsmClient.getCdsmInfo();
      // ...
    } catch (err) {
      hilog.error(0x0000, 'testTag',
        `errCode: ${(err as BusinessError).code}, errMessage: ${(err as BusinessError).message}`);
      // ...
    }
    ```

5. Subscribe to information changes of the member devices in the CDS by registering a callback.

    <!-- @[cdsm_on_info_change](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ConnectivityKit/NearLink/entry/src/main/ets/nearlink/pages/CdsmPage.ets) -->
    
    ``` TypeScript
    try {
      cdsmClient.onCdsmInfoChange((data: cdsm.CdsmInfo) => {
        hilog.info(0x0000, 'testTag', `CDSM info changed: ${JSON.stringify(data)}`);
        // ...
      });
    } catch (err) {
      hilog.error(0x0000, 'testTag',
        `errCode: ${(err as BusinessError).code}, errMessage: ${(err as BusinessError).message}`);
      // ...
    }
    ```

6. Unsubscribe from information changes of the member devices in the CDS.

    <!-- @[cdsm_off_info_change](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ConnectivityKit/NearLink/entry/src/main/ets/nearlink/pages/CdsmPage.ets) -->
    
    ``` TypeScript
    try {
      cdsmClient.offCdsmInfoChange();
    } catch (err) {
      hilog.error(0x0000, 'testTag',
        `errCode: ${(err as BusinessError).code}, errMessage: ${(err as BusinessError).message}`);
    }
    ```
