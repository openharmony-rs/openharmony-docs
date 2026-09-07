# 使用星闪传输数据
<!--Kit: Connectivity Kit-->
<!--Subsystem: Communication-->
<!--Owner: @CCCZKing-->
<!--Designer: @lilong32; @CCCZKing-->
<!--Tester: @zhangjiaji111-->
<!--Adviser: @zhang_yixin13-->

提供星闪数传相关的端口通道建立和数据传输等功能，同一设备可以同时承担数据发送端和接收端的角色。

## 场景介绍

在星闪设备间已建立起逻辑链路的基础上，支持应用基于星闪技术进行设备间的数据传输。逻辑链路是星闪接入层的逻辑信道，为设备间的数据传输提供承载，由系统在设备连接过程中建立，开发者无需直接管理。

开发前需按[开发准备](nearlink-preparations-guide.md)完成权限声明与运行时申请，并确保设备已开启星闪（参见[开发准备 > 查询星闪开关状态](nearlink-preparations-guide.md#查询星闪开关状态)）；端口UUID必须为自定义UUID（参见[星闪常见问题 > 标准UUID与自定义UUID有什么区别](nearlink-faq-guide.md#标准uuid与自定义uuid有什么区别)），发送端与接收端UUID必须相同。

> **说明：**
>
> 1. 数据传输通道不保证链路加密。如需加密数传，需先进行配对流程，通过[startPairing()](../../reference/apis-connectivity-kit/js-apis-nearlink-remote-device.md#startpairing)接口发起。
> 2. 链路是否加密可通过[getAcbState()](../../reference/apis-connectivity-kit/js-apis-nearlink-remote-device.md#getacbstate)接口查询，ENCRYPTED状态表示链路已加密。

## 接口说明

使用星闪传输数据，完整的API说明以及示例代码请参考：[@ohos.nearlink.dataTransfer (星闪数传能力)](../../reference/apis-connectivity-kit/js-apis-nearlink-data-transfer-api.md)。

| 接口名 | 描述 |
| -------- | -------- |
| createPort(uuid: string): void | 注册端口服务。 |
| destroyPort(uuid: string): void | 销毁端口服务。 |
| connect(params: ConnectionParams): Promise&lt;void&gt; | 连接远端设备，建立端口通道。使用Promise异步回调。 |
| disconnect(params: ConnectionParams): Promise&lt;void&gt; | 断开端口通道连接。使用Promise异步回调。 |
| writeData(params: DataParams): Promise&lt;void&gt; | 通过设备地址和UUID向远端设备发数据。使用Promise异步回调。 |
| onConnectionStateChanged(callback: Callback&lt;ConnectionResult&gt;): void | 订阅端口通道连接状态变更事件。使用callback异步回调。 |
| onReadData(callback: Callback&lt;DataParams&gt;): void | 订阅端口通道数据接收事件。使用callback异步回调。 |

## 开发步骤

1. 导入相关模块。

    <!-- @[datatransfer_module_import](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ConnectivityKit/NearLink/entry/src/main/ets/nearlink/pages/DataTransferPage.ets) -->

    ```ts
    import { hilog } from '@kit.PerformanceAnalysisKit';
    import { BusinessError } from '@kit.BasicServicesKit';
    import { dataTransfer } from '@kit.ConnectivityKit';
    ```

2. 定义端口UUID与设备地址变量，供后续步骤使用。

    <!-- @[datatransfer_declare](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ConnectivityKit/NearLink/entry/src/main/ets/nearlink/pages/DataTransferPage.ets) -->

    ```ts
    let serviceUuid: string = 'FFFFFFFF-1234-5678-ABCD-000000001244';
    let chosenDeviceAddr: string;
    ```

3. 注册端口通道，发送端和接收端均需注册。

    <!-- @[datatransfer_create_port](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ConnectivityKit/NearLink/entry/src/main/ets/nearlink/pages/DataTransferPage.ets) -->

    ```ts
    try {
      dataTransfer.createPort(serviceUuid);
      // ...
    } catch (err) {
      hilog.error(0x0000, 'testTag',
        `errCode: ${(err as BusinessError).code}, errMessage: ${(err as BusinessError).message}`);
      // ...
    }
    ```

4. 订阅端口通道连接状态变更事件。不再需要订阅事件时，调用[offConnectionStateChanged()](../../reference/apis-connectivity-kit/js-apis-nearlink-data-transfer-api.md#datatransferoffconnectionstatechanged)取消订阅。

    <!-- @[datatransfer_on_conn_state](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ConnectivityKit/NearLink/entry/src/main/ets/nearlink/pages/DataTransferPage.ets) -->

    ```ts
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

5. 订阅端口通道数据接收事件。不再需要订阅事件时，调用[offReadData()](../../reference/apis-connectivity-kit/js-apis-nearlink-data-transfer-api.md#datatransferoffreaddata)取消订阅。

    <!-- @[datatransfer_on_read_data](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ConnectivityKit/NearLink/entry/src/main/ets/nearlink/pages/DataTransferPage.ets) -->

    ```ts
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

6. 连接远端设备，建立端口通道。其中chosenDeviceAddr为从[发起星闪扫描](nearlink-device-discovery-guide.md#发起星闪扫描)结果中选择的设备地址，UUID需与步骤3中注册的保持一致。

    <!-- @[datatransfer_connect](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ConnectivityKit/NearLink/entry/src/main/ets/nearlink/pages/DataTransferPage.ets) -->

    ```ts
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

7. 通过设备地址和UUID向远端设备发数据。

    > **说明：**
    >
    > 连续多次调用writeData可能导致发送队列拥塞而发送失败。建议通过setInterval设置数据发送时间间隔，推荐间隔为10ms（参见[星闪常见问题 > 连续调用writeData为什么会发送失败](nearlink-faq-guide.md#连续调用writedata为什么会发送失败)）。

    <!-- @[datatransfer_write_data](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ConnectivityKit/NearLink/entry/src/main/ets/nearlink/pages/DataTransferPage.ets) -->

    ```ts
    try {
      // 使用固定示例数据填充负载，实际开发中替换为业务数据
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

8. 断开端口通道连接。

    <!-- @[datatransfer_disconnect](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ConnectivityKit/NearLink/entry/src/main/ets/nearlink/pages/DataTransferPage.ets) -->

    ```ts
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

9. 销毁端口。数据传输完成后，应用销毁端口，释放端口通道及相关资源。

    <!-- @[datatransfer_destroy_port](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ConnectivityKit/NearLink/entry/src/main/ets/nearlink/pages/DataTransferPage.ets) -->

    ```ts
    try {
      dataTransfer.destroyPort(serviceUuid);
      // ...
    } catch (err) {
      hilog.error(0x0000, 'testTag',
        `errCode: ${(err as BusinessError).code}, errMessage: ${(err as BusinessError).message}`);
      // ...
    }
    ```
