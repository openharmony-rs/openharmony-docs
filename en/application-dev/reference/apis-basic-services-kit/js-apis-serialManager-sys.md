# @ohos.usbManager.serial (Serial Port Management) (System API)

<!--Kit: Basic Services Kit-->
<!--Subsystem: USB-->
<!--Owner: @hwymlgitcode-->
<!--Designer: @w00373942-->
<!--Tester: @dong-dongzhen-->
<!--Adviser: @fang-jinxu-->
<!-- md-trans-meta sourceCommit=4a75817f654bf9f2913fe0e82b0afc55f92a210e translatedAt=2026-09-01T04:14:40.543Z pushedAt=2026-09-01T12:00:27.096Z -->

The serial port management module uses a system-level permission control mechanism. The system manages and verifies the access permissions of serial port devices in a centralized manner. Apps can read data from and write data to serial port devices only after obtaining the access permissions through system APIs. This ensures secure access control and device isolation.

> **NOTE**
>
> The initial APIs of this module are supported since API version 19. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
> This topic describes only the system APIs provided by the module. For details about its public APIs, see [@ohos.usbManager.serial (Serial Port Management)](js-apis-serialManager.md).

## Modules to Import

```ts
import { serialManager } from '@kit.BasicServicesKit';
```

## serialManager.addSerialRight

addSerialRight(tokenId: number, portId: number): void

Adds the permission to an app for accessing the serial port device. Before using this method, you need to call [getPortList](js-apis-serialManager.md#serialmanagergetportlist) to obtain the serial port list and obtain a valid port ID from the list. If the call is successful, the app obtains the permission to access the specified serial port device and can perform operations such as opening, reading data, and writing data. If the call fails, an error code is returned, and the app cannot access the serial port device.

**Use scenarios**
- This method is used by system apps when silent authorization is required while user confirmation is not needed. Silent authorization enables system apps to directly obtain the permission to access serial port devices through system APIs without requiring user interaction. This is applicable to scenarios such as communication between internal components of the system and automatic connection between the background server and the serial port device. The system checks whether silent authorization is allowed based on **ohos.permission.MANAGE_USB_CONFIG** and grants the permission without requiring user confirmation.
- Unlike requestSerialRight, [serialManager.requestSerialRight](js-apis-serialManager.md#serialmanagerrequestserialright) triggers a dialog box to request user authorization, which is applicable when explicit user authorization is required. addSerialRight does not trigger a dialog box but directly adds the permission for the app to access the device, which is applicable to automatic management of system apps. After the application exits, the system automatically removes the access permission on the serial port device. After the application is restarted, the application needs to request the permission again.

**System API:** This is a system API.

**Required permissions:** ohos.permission.MANAGE_USB_CONFIG

**System capability**: SystemCapability.USB.USBManager.Serial

**Parameters**

| Name     | Type     | Required | Description                                  |
|---------|--------|----|-------------------------------------|
| tokenId | number | Yes  | App access token ID, which identifies the app that requires the permission to access the serial port device. It can be obtained using [bundleManager.getBundleInfoForSelf](../apis-ability-kit/js-apis-bundleManager.md#bundlemanagergetbundleinfoforself).                  |
| portId  | number | Yes  | Port number of the serial port device, which uniquely identifies the serial port device. A valid port number can be obtained using [serialManager.getPortList](js-apis-serialManager.md#serialmanagergetportlist). Ensure that the port number exists. Otherwise, error code 31400003 will be returned. |

**Return value**

| Type | Description |
| --- | --- |
| void | No value is returned. |

**Error codes:**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [USB Error Codes](errorcode-usb.md).

| ID | error message                                                     |
| -------- | ------------------------------------------------------------ |
| 201      | Permission verification failed. The application does not have the permission required to call the API. |
| 202      | Permission verification failed. A non-system application calls a system API. |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 14400005 | Database operation exception. |
| 31400001 | Serial port management exception. |
| 31400003 | PortId does not exist. |

**Example**
```ts
import { bundleManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { serialManager } from '@kit.BasicServicesKit';


function addSerialRight() {
  // Obtain the serial port list.
  let portList: serialManager.SerialPort[] = serialManager.getPortList();
  console.info('portList: ', JSON.stringify(portList));
  if (portList === undefined || portList.length === 0) {
    console.info('portList is empty');
    return;
  }

  let portId: number = portList[0].portId;
  let bundleFlags = bundleManager.BundleFlag.GET_BUNDLE_INFO_WITH_APPLICATION;

  bundleManager.getBundleInfoForSelf(bundleFlags).then((bundleInfo) => {
    console.info('getBundleInfoForSelf successfully. Data: %{public}s', JSON.stringify(bundleInfo));
    let tokenId = bundleInfo.appInfo.accessTokenId;
    try {
      // Add the permission to the serial port.
      serialManager.addSerialRight(tokenId, portId);
      console.info('addSerialRight success, portId: ' + portId);
    } catch (error) {
      const err: BusinessError = error as BusinessError;
      console.error(`Failed to add serial right. Code: ${err.code}, message: ${err.message}`);
    }
  }).catch((error: BusinessError) => {
    console.error(`Failed to get bundle info for self. Code: ${error.code}, message: ${error.message}`);
  });
}
```
