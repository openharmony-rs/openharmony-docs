# USB批量传输

## 场景介绍

批量传输主要应用在传输和接收大量数据同时又没有带宽和间隔时间要求的情况下，例如传输文件、图像等场景，打印机和扫描仪等设备属于这种类型的设备。

## 环境准备

### 环境要求

- 开发工具及配置：

  DevEco Studio作为驱动开发工具，是进行驱动开发必备条件之一，开发者可以使用该工具进行开发、调试、打包等操作。请[下载安装](https://developer.huawei.com/consumer/cn/download/)该工具，并参考[DevEco Studio使用指南](https://developer.huawei.com/consumer/cn/doc/harmonyos-guides/ide-tools-overview)中的[创建工程及运行](https://developer.huawei.com/consumer/cn/doc/harmonyos-guides/ide-create-new-project)进行基本的操作验证，保证DevEco Studio可正常运行。


- SDK版本配置：

  扩展外设管理提供的ArkTs接口，所需SDK版本为API16及以上才可使用。


- HDC配置：

  HDC（HarmonyOS Device Connector）是为开发人员提供的用于调试的命令行工具，通过该工具可以在Windows/Linux/Mac系统上与真实设备或者模拟器进行交互，详细参考[HDC配置](https://developer.huawei.com/consumer/cn/doc/harmonyos-guides/hdc)。

### 搭建环境

- 在PC上安装[DevEco Studio](https://developer.huawei.com/consumer/cn/download/deveco-studio)，要求版本在4.1及以上。
- 将public-SDK更新到API 16或以上<!--Del-->，更新SDK的具体操作可参见[更新指南](https://gitee.com/openharmony/docs/blob/master/zh-cn/application-dev/faqs/full-sdk-switch-guide.md)<!--DelEnd-->。
- PC安装HDC工具，通过该工具可以在Windows/Linux/Mac系统上与真实设备或者模拟器进行交互。
- 用USB线缆将搭载OpenHarmony的设备连接到PC。

## 开发指导

### 接口说明

| 接口名                                                                                                               | 描述                    |
|-------------------------------------------------------------------------------------------------------------------|-----------------------|
| bulkTransfer(pipe: USBDevicePipe, endpoint: USBEndpoint, buffer: Uint8Array, timeout ?: number): Promise&lt;number&gt;  | 批量传输。                 |

更多关于设备管理和传输模式的详细接口介绍，请查阅[API参考文档](../../../../reference/apis-basic-services-kit/js-apis-usbManager.md)。

### 开发步骤

主机（Host）连接设备（Device），通过`bulkTransfer`接口进行数据传输。以下步骤描述了如何使用批量传输方式来传输数据：

> **说明：** 
>
> 以下示例代码只是使用批量传输方式来传输数据的必要流程，需要放入具体的方法中执行。在实际调用时，设备开发者需要遵循设备相关协议进行调用，确保数据的正确传输和设备的兼容性。

1. 导入模块。

   ```ts
   // 导入usbManager模块。
   import { usbManager } from '@kit.BasicServicesKit';
   import { BusinessError } from '@kit.BasicServicesKit';
   ```
   
2. 获取设备列表。
   
    ```ts
   // 获取设备列表。
   let deviceList : Array<usbManager.USBDevice> = usbManager.getDevices();
   console.info(`deviceList: ${deviceList}`);
   if(deviceList.length === 0) {
     console.error('deviceList is empty');
     return;
   }
   /*
   deviceList结构示例
   [
     {
       name: "1-1",
       serial: "",
       manufacturerName: "",
       productName: "",
       version: "",
       vendorId: 7531,
       productId: 2,
       clazz: 9,
       subClass: 0,
       protocol: 1,
       devAddress: 1,
       busNum: 1,
       configs: [
         {
           id: 1,
           attributes: 224,
           isRemoteWakeup: true,
           isSelfPowered: true,
           maxPower: 0,
           name: "1-1",
           interfaces: [
             {
               id: 0,
               protocol: 0,
               clazz: 9,
               subClass: 0,
               alternateSetting: 0,
               name: "1-1",
               endpoints: [
                 {
                   address: 129,
                   attributes: 3,
                   interval: 12,
                   maxPacketSize: 4,
                   direction: 128,
                   number: 1,
                   type: 3,
                   interfaceId: 0,
                 }
               ]
             }
           ]
         }
       ]
     }
   ]
   */
   ```

3. 获取设备操作权限。

   ```ts
   let deviceName : string = deviceList[0].name;
   // 申请操作指定的device的操作权限。
   usbManager.requestRight(deviceName).then((hasRight : boolean) => {
     console.info(`usb device request right result: ${hasRight}`);
   }).catch((error : BusinessError)=> {
     console.error(`usb device request right failed : ${error}`);
   });
   ```

4. 打开设备。

   ```ts
   // 打开设备，获取数据传输通道。
   let pipe : usbManager.USBDevicePipe = usbManager.connectDevice(deviceList[0]);
   let interface1 : usbManager.USBInterface = deviceList[0].configs[0].interfaces[0];
   /*
    打开对应接口，在设备信息（deviceList）中选取对应的interface。
   interface1为设备配置中的一个接口。
   */
   usbManager.claimInterface(pipe, interface1, true);
   ```

5. 数据传输。

    ```ts
    /*
      读取数据，在device信息中选取对应数据接收的endpoint来做数据传输
    （endpoint.direction == 0x80）；dataUint8Array是要读取的数据，类型为Uint8Array。
    */
    let inEndpoint : usbManager.USBEndpoint = interface1.endpoints[2];
    let outEndpoint : usbManager.USBEndpoint = interface1.endpoints[1];
    let dataUint8Array : Uint8Array = new Uint8Array(1024);
    usbManager.bulkTransfer(pipe, inEndpoint, dataUint8Array, 15000).then((dataLength : number) => {
    if (dataLength >= 0) {
      console.info(`usb readData result Length : ${dataLength}`);
    } else {
      console.error("usb readData failed");
    }
    }).catch((error : BusinessError) => {
    console.error(`usb readData error : ${error}`);
    });
    // 发送数据，在device信息中选取对应数据发送的endpoint来做数据传输。（endpoint.direction == 0）
    usbManager.bulkTransfer(pipe, outEndpoint, dataUint8Array, 15000).then((dataLength : number) => {
      if (dataLength >= 0) {
        console.info(`usb writeData result write length : ${dataLength}`);
      } else {
        console.error("usb writeData failed");
      }
    }).catch((error : BusinessError) => {
      console.error(`usb writeData error : ${error}`);
    });
    ```

6. 释放接口，关闭设备。

   ```ts
   usbManager.releaseInterface(pipe, interface1);
   usbManager.closePipe(pipe);
   ```