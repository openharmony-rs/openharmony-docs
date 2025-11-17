# UI-based Driver Development
<!--Kit: Driver Development Kit-->
<!--Subsystem: Driver-->
<!--Owner: @lixinsheng2-->
<!--Designer: @w00373942-->
<!--Tester: @dong-dongzhen-->
<!--Adviser: @w_Machine_cc-->

## When to Use

UI-based basic drivers are applicable to a wide variety of composite devices. When developing these drivers, you may set the corresponding unique driver capabilities through the UI, or display the information retrieved from the devices on the UI. Examples of such devices include mice with side buttons, handwriting tablets, and ID card readers.

## Environment Setup

Before you get started, make necessary preparations by following instructions in [Environment Preparation](environmental-preparation.md).

## Available APIs

The following table describes the basic peripheral management capabilities. For details, see [API Reference](../../reference/apis-driverdevelopment-kit/js-apis-driver-deviceManager.md).

**Table 1** APIs for basic peripheral management

| Name                                                      | Description                                                        |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| queryDevices(busType?: number): Array&lt;Readonly&lt;Device&gt;&gt; | Queries the peripheral list.                                          |
| bindDriverWithDeviceId(deviceId: number, onDisconnect: AsyncCallback&lt;number&gt;): Promise&lt;RemoteDeviceDriver&gt;; | Binds a peripheral. This API uses a promise to return the result. It is supported since API version 18.                      |
| unbindDriverWithDeviceId(deviceId: number): Promise&lt;number&gt; | Unbinds a peripheral device. This API uses a promise to return the result. It is supported since API version 18.                      |

<!--Del-->
The following table lists the APIs for extended peripheral management. For details, see [deviceManager API Reference](../../reference/apis-driverdevelopment-kit/js-apis-driver-deviceManager-sys.md).

**Table 2** APIs for extended peripheral management

| Name                                                                         | Description             |
|------------------------------------------------------------------------------|-----------------|
| queryDeviceInfo(deviceId?: number): Array&lt;Readonly&lt;DeviceInfo&gt;&gt;  | Obtains the list of detailed information about peripherals.  |
| queryDriverInfo(driverUid?: string): Array&lt;Readonly&lt;DriverInfo&gt;&gt; | Obtains the list of detailed information about peripheral drivers.|
<!--DelEnd-->

## How to Develop

You can use the APIs to query and bind peripheral devices so as to use the customized driver capabilities of the peripherals.

The following sample code is a demo that illustrates how to develop both the client and server and implement IPC.

1. Create a project following instructions in [Creating a Project](https://developer.huawei.com/consumer/en/doc/harmonyos-guides/ide-create-new-project).

    **NOTE**

    > To develop a driver client, select the **Empty Ability** template.
    >
    > To develop the driver server, select the **Native C++** template.
    >
    >To develop both the driver client and server, select the **Native C++** template.


2. Import the related kit, and declare the product ID, vendor ID, and code of the USB device to be bound.

    **NOTE**

    > Write following sample code in the **entry/src/main/ets/pages/Index.ets** file.

    <!-- @[driver_ui_step2](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/DriverDevelopmentKit/DriverDemo/entry/src/main/ets/pages/Index.ets) -->

``` TypeScript
import { hilog } from '@kit.PerformanceAnalysisKit';
import { deviceManager } from '@kit.DriverDevelopmentKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { rpc } from '@kit.IPCKit';

const REQUEST_CODE: number = 99; // Custom communication code, which is for reference only.
const productId: number = 4258; // Declare the product ID of the connected USB device.
const vendorId: number = 4817; // Declare the vendor ID of the connected USB device.
const DOMAIN = 0x0000;
```


3. Define the **message** variable and remote object variable for communication with the driver.

    **NOTE**

    > The following APIs are defined in **struct Index{}**.

    <!-- @[driver_ui_step3](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/DriverDevelopmentKit/DriverDemo/entry/src/main/ets/pages/Index.ets) -->

``` TypeScript
  @State message: string = 'Hello';
  private remote: rpc.IRemoteObject | null = null;
```


4. Define the **queryDevices** API, and use it to obtain the device ID of the peripheral.

    <!-- @[driver_ui_step4](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/DriverDevelopmentKit/DriverDemo/entry/src/main/ets/pages/Index.ets) -->

``` TypeScript
  private async queryTargetDeviceId(): Promise<number> {
    try {
      const devices: deviceManager.Device[] = deviceManager.queryDevices(deviceManager.BusType.USB);
      const index = devices.findIndex((item: deviceManager.Device) => {
        let usbDevice = item as deviceManager.USBDevice;
        // If the product ID and vendor ID of the peripheral are unknown, you can view the information about the connected USB device in the log.
        hilog.info(DOMAIN, 'testTag', `usbDevice.productId = ${usbDevice.productId}, usbDevice.vendorId = ${usbDevice.vendorId}`);
        return usbDevice.productId === productId && usbDevice.vendorId === vendorId;
      });
      hilog.info(DOMAIN, 'testTag', `queryTargetDeviceId index = ${index}, deviceId = ${devices[index].deviceId}`);
      if (index < 0) {
        hilog.error(DOMAIN, 'testTag', 'can not find device');
        return -1;
      }
      return devices[index].deviceId;
    } catch (error) {
      hilog.error(DOMAIN, 'testTag', `queryDevice failed, err: ${JSON.stringify(error)}`);
    }
    return -1;
  }
```


5. Define the **bindDriverWithDeviceId** API, and use it to obtain the remote object.

    <!-- @[driver_ui_step5](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/DriverDevelopmentKit/DriverDemo/entry/src/main/ets/pages/Index.ets) -->

``` TypeScript
  private async getDriverRemote(deviceId: number): Promise<rpc.IRemoteObject | null> {
    try {
      let remoteDeviceDriver: deviceManager.RemoteDeviceDriver = await deviceManager.bindDeviceDriver(deviceId,
        (err: BusinessError, id: number) => {
          hilog.info(DOMAIN, 'testTag', `device[${id}] id disconnect, err: ${JSON.stringify(err)}`);
        });
      return remoteDeviceDriver.remote;
    } catch (error) {
      hilog.error(DOMAIN, 'testTag', `bindDriverWithDeviceId failed, err: ${JSON.stringify(error)}`);
    }
    return null;
  }
```


6. Defines the **sendMessageRequest** API, and use it to perform IPC with the remote object.

    <!-- @[driver_ui_step6](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/DriverDevelopmentKit/DriverDemo/entry/src/main/ets/pages/Index.ets) -->

``` TypeScript
  private async communicateWithRemote(): Promise<void> {
    const deviceId: number = await this.queryTargetDeviceId();
    hilog.info(DOMAIN, 'testTag', `queryTargetDeviceId, deviceId=${deviceId}`);
    if (deviceId < 0) {
      hilog.error(DOMAIN, 'testTag', 'can not find target device');
      return;
    }
    this.remote = await this.getDriverRemote(deviceId);
    if (this.remote === null) {
      hilog.error(DOMAIN, 'testTag', `getDriverRemote failed`);
      return;
    }

    let option = new rpc.MessageOption();
    let data = new rpc.MessageSequence();
    let reply = new rpc.MessageSequence();

    // Send "Hello" to the driver.
    hilog.info(DOMAIN, 'testTag', `communicateWithRemote, message=${this.message}`);
    data.writeString(this.message);

    try {
      await this.remote.sendMessageRequest(REQUEST_CODE, data, reply, option);
      // Obtain the "Hello world" information returned by the driver.
      this.message = reply.readString();
      hilog.info(DOMAIN, 'testTag', `sendMessageRequest, message: ${this.message}`);
    } catch (error) {
      hilog.error(DOMAIN, 'testTag', `sendMessageRequest failed, err: ${JSON.stringify(error)}`);
    }
  }
```


7. Render the UI. For details about UI development, see [UI Development](https://developer.huawei.com/consumer/en/doc/harmonyos-guides/arkts-ui-development).

    <!-- @[driver_ui_step7](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/DriverDevelopmentKit/DriverDemo/entry/src/main/ets/pages/Index.ets) -->

``` TypeScript
  build() {
    Row() {
      Column() {
        Text(this.message)
          .fontSize($r('app.float.page_text_font_size'))
          .fontWeight(FontWeight.Bold)
          .onClick(() => {
            // Click Hello to communicate with the remote object. The message "Hello World" is displayed.
            this.communicateWithRemote();
          })
      }
      .width('100%')
    }
    .height('100%')
  }
```


8. Develop peripheral drivers by following instructions in [UI-free Driver Development](driverextensionability.md).

<!--RP1-->
## Application Signing

**NOTE**<br>Configure the permission before enabling automatic signing.

You need to configure a signature file for your application to run on a device. Besides, to develop a peripheral driver client, you need to declare the **ohos.permission.ACCESS_EXTENSIONAL_DEVICE_DRIVER** and **ohos.permission.ACCESS_DDK_DRIVERS** permissions for the peripheral.
- ohos.permission.ACCESS_EXTENSIONAL_DEVICE_DRIVER (This permission is required for API version 10 or later.)

  To obtain authorization on this access permission, [declare it](../../security/AccessToken/declare-permissions.md) in the **requestPermissions** field in the **module.json5** file.

- ohos.permission.ACCESS_DDK_DRIVERS (This permission is required for API version 18 or later.)

  1. [Declare the required permissions](../../security/AccessToken/declare-permissions.md) in the **requestPermissions** field in the **module.json5** file.
  2. Modify the **acls** field in the **HarmonyAppProvision** configuration file to request permissions via ACL. For details, see [Requesting Restricted Permissions](../../security/AccessToken/declare-permissions-in-acl.md).
  3. In the **HarmonyAppProvision** configuration file (that is, **Sdk/openharmony/_{Version} _/toolchains /lib/UnsgnedReleasedProfileTemplate.json** file), configure the bundle name of the driver server to connect. If there are multiple servers, separate their bundle names with a comma.

      The configuration procedure is as follows:

      Add the **app-services-capabilities** node to the root node of the file and configure the node as follows:
      ```json
      "app-services-capabilities": {
        "ohos.permission.ACCESS_DDK_DRIVERS": {"bundleNames": "bundleName0,bundleName1,bundleName2"}
      }
      ```

Automatic signing: [Signing Your App/Service Automatically](https://developer.huawei.com/consumer/en/doc/harmonyos-guides/ide-signing#section18815157237)
<!--RP1End-->
