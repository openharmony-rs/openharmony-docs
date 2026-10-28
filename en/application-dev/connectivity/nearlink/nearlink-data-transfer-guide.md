# Transferring Data over NearLink
<!--Kit: Connectivity Kit-->
<!--Subsystem: Communication-->
<!--Owner: @CCCZKing-->
<!--Designer: @lilong32; @CCCZKing-->
<!--Tester: @zhangjiaji111-->
<!--Adviser: @zhang_yixin13-->
<!-- md-trans-meta sourceCommit=b0496895a7bfb2583dccb5b6cde02296fbec733b translatedAt=2026-09-29T10:56:49.398Z pushedAt=2026-09-30T06:12:44.713Z -->

Provides NearLink data transfer capabilities such as port channel establishment and data sending/receiving. A device can act as both the data sender and the data receiver at the same time.

## Overview

Once a logical link is established between NearLink devices, applications can transfer data between devices using NearLink technology. A logical link is a logical channel at the NearLink access layer that carries data transfer between devices. It is established by the system during device connection and does not require direct management by developers.

Before development, complete the permission declaration and runtime request as described in [Getting Started](nearlink-preparations-guide.md), and ensure that NearLink is enabled on the device (see [Getting Started > Querying the NearLink Switch State](nearlink-preparations-guide.md#querying-the-nearlink-switch-state)). The port UUID must be a custom UUID (see [NearLink FAQs > What Is the Difference Between Standard UUIDs and Custom UUIDs](nearlink-faq-guide.md#what-is-the-difference-between-standard-uuids-and-custom-uuids)), and the sender and the receiver must use the same UUID.

> **NOTE**
>
> 1. A port channel does not guarantee link encryption. To encrypt data transfer, perform the pairing process first and initiate it through the [startPairing()](../../reference/apis-connectivity-kit/js-apis-nearlink-remote-device.md#startpairing) API.
> 2. You can query whether the link is encrypted through the [getAcbState()](../../reference/apis-connectivity-kit/js-apis-nearlink-remote-device.md#getacbstate) API. The `ENCRYPTED` state indicates that the link is encrypted.

## Available APIs

For the complete API description and sample code for transferring data over NearLink, see [@ohos.nearlink.dataTransfer (NearLink Data Transfer Capability)](../../reference/apis-connectivity-kit/js-apis-nearlink-data-transfer-api.md).

| API | Description |
| -------- | -------- |
| createPort(uuid: string): void | Registers a port channel. |
| destroyPort(uuid: string): void | Destroys a port channel. |
| connect(params: ConnectionParams): Promise&lt;void&gt; | Connects to a remote device and establishes a port channel. This API uses a Promise to return the result asynchronously. |
| disconnect(params: ConnectionParams): Promise&lt;void&gt; | Disconnects a port channel. This API uses a Promise to return the result asynchronously. |
| writeData(params: DataParams): Promise&lt;void&gt; | Sends data to a remote device by device address and UUID. This API uses a Promise to return the result asynchronously. |
| onConnectionStateChanged(callback: Callback&lt;ConnectionResult&gt;): void | Subscribes to port channel connection state change events. This API uses a callback to return the result asynchronously. |
| onReadData(callback: Callback&lt;DataParams&gt;): void | Subscribes to port channel data receiving events. This API uses a callback to return the result asynchronously. |

## How to Develop

1. Import the required modules.

    <!-- @[datatransfer_module_import](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ConnectivityKit/NearLink/entry/src/main/ets/nearlink/pages/DataTransferPage.ets) -->
    
    ``` TypeScript
    import { hilog } from '@kit.PerformanceAnalysisKit';
    import { BusinessError } from '@kit.BasicServicesKit';
    import { dataTransfer } from '@kit.ConnectivityKit';
    ```

2. Define the port UUID and device address variables for use in subsequent steps.

    <!-- @[datatransfer_declare](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ConnectivityKit/NearLink/entry/src/main/ets/nearlink/pages/DataTransferPage.ets) -->
    
    ``` TypeScript
    let serviceUuid: string = 'FFFFFFFF-1234-5678-ABCD-000000001244';
    let chosenDeviceAddr: string;
    ```

3. Register the port channel for both the sender and the receiver.

    <!-- @[datatransfer_create_port](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ConnectivityKit/NearLink/entry/src/main/ets/nearlink/pages/DataTransferPage.ets) -->
    
    ``` TypeScript
    try {
      dataTransfer.createPort(serviceUuid);
      // ...
    } catch (err) {
      hilog.error(0x0000, 'testTag',
        `errCode: ${(err as BusinessError).code}, errMessage: ${(err as BusinessError).message}`);
      // ...
    }
    ```

4. Subscribe to port channel connection state change events. When the subscription is no longer needed, call [offConnectionStateChanged()](../../reference/apis-connectivity-kit/js-apis-nearlink-data-transfer-api.md#datatransferoffconnectionstatechanged) to unsubscribe.

    <!-- @[datatransfer_on_conn_state](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ConnectivityKit/NearLink/entry/src/main/ets/nearlink/pages/DataTransferPage.ets) -->
    
    ``` TypeScript
    try {
      dataTransfer.onConnectionStateChanged((data: dataTransfer.ConnectionResult) => {
        hilog.info(0x0000, 'testTag', `Connection state: ${JSON.stringify(data)}`);
        // ...
      });
    } catch (err) {
      hilog.error(0x0000, 'testTag',
        `errCode: ${(err as BusinessError).code}, errMessage: ${(err as BusinessError).message}`);
    }
    ```

5. Subscribe to port channel data receive events. When the event is no longer needed, call [offReadData()](../../reference/apis-connectivity-kit/js-apis-nearlink-data-transfer-api.md#datatransferoffreaddata) to unsubscribe.

    <!-- @[datatransfer_on_read_data](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ConnectivityKit/NearLink/entry/src/main/ets/nearlink/pages/DataTransferPage.ets) -->
    
    ``` TypeScript
    try {
      dataTransfer.onReadData((data: dataTransfer.DataParams) => {
        hilog.info(0x0000, 'testTag', `Data received: ${JSON.stringify(data)}`);
        // ...
      });
    } catch (err) {
      hilog.error(0x0000, 'testTag',
        `errCode: ${(err as BusinessError).code}, errMessage: ${(err as BusinessError).message}`);
    }
    ```

6. Connect to the remote device to establish a port channel. Here, `chosenDeviceAddr` is the device address selected from the results of the [NearLink scan](nearlink-device-discovery-guide.md#initiating-a-nearlink-scan), and the UUID must be consistent with the one registered in step 3.

    <!-- @[datatransfer_connect](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ConnectivityKit/NearLink/entry/src/main/ets/nearlink/pages/DataTransferPage.ets) -->
    
    ``` TypeScript
    try {
      let params: dataTransfer.ConnectionParams = {
        address: chosenDeviceAddr,
        uuid: serviceUuid,
        transferMode: dataTransfer.TransferMode.BASIC
      };
      await dataTransfer.connect(params);
      // ...
    } catch (err) {
      hilog.error(0x0000, 'testTag',
        `errCode: ${(err as BusinessError).code}, errMessage: ${(err as BusinessError).message}`);
      // ...
    }
    ```

7. Send data to the remote device by device address and UUID.

    > **NOTE**
    >
    > Repeatedly calling `writeData` may cause the send queue to become congested, resulting in send failures. It is recommended that you set the data send interval using `setInterval`, with a recommended interval of 10 ms. For details, see [NearLink FAQs > Why Does Calling writeData() Consecutively Cause Send Failures?](nearlink-faq-guide.md#why-does-calling-writedata-consecutively-cause-send-failures)).

    <!-- @[datatransfer_write_data](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ConnectivityKit/NearLink/entry/src/main/ets/nearlink/pages/DataTransferPage.ets) -->
    
    ``` TypeScript
    try {
      // Fill the payload with fixed sample data. Replace it with service data in actual development.
      let dataBuffer = new ArrayBuffer(4);
      let data = new Uint8Array(dataBuffer);
      data[0] = 0x01;
      data[1] = 0x02;
      data[2] = 0x03;
      data[3] = 0x04;
    
      let params: dataTransfer.DataParams = {
        address: chosenDeviceAddr,
        uuid: serviceUuid,
        data: dataBuffer
      };
      await dataTransfer.writeData(params);
      // ...
    } catch (err) {
      hilog.error(0x0000, 'testTag',
        `errCode: ${(err as BusinessError).code}, errMessage: ${(err as BusinessError).message}`);
      // ...
    }
    ```

8. Disconnect the port channel.

    <!-- @[datatransfer_disconnect](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ConnectivityKit/NearLink/entry/src/main/ets/nearlink/pages/DataTransferPage.ets) -->
    
    ``` TypeScript
    try {
      let params: dataTransfer.ConnectionParams = {
        address: chosenDeviceAddr,
        uuid: serviceUuid
      };
      await dataTransfer.disconnect(params);
      // ...
    } catch (err) {
      hilog.error(0x0000, 'testTag',
        `errCode: ${(err as BusinessError).code}, errMessage: ${(err as BusinessError).message}`);
      // ...
    }
    ```

9. Destroy the port. After data transfer is complete, destroy the port to release the port channel and related resources.

    <!-- @[datatransfer_destroy_port](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ConnectivityKit/NearLink/entry/src/main/ets/nearlink/pages/DataTransferPage.ets) -->
    
    ``` TypeScript
    try {
      dataTransfer.destroyPort(serviceUuid);
      // ...
    } catch (err) {
      hilog.error(0x0000, 'testTag',
        `errCode: ${(err as BusinessError).code}, errMessage: ${(err as BusinessError).message}`);
      // ...
    }
    ```
