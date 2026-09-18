# addSerialRight (System API)

## Modules to Import

```TypeScript
import { serialManager } from '@kit.BasicServicesKit';
```

## addSerialRight

```TypeScript
function addSerialRight(tokenId: number, portId: number): void
```

Adds the permission to an app for accessing the serial port device. Before using this method, you need to call [getPortList](arkts-basicservices-serialmanager-getportlist-f.md) to obtain the serial port list and obtain a valid port ID from the list. If the call is successful, the app obtains the permission to access the specified serial port device and can perform operations such as opening, reading data, and writing data. If the call fails, an error code is returned, and the app cannot access the serial port device.

**Use scenarios**  
- This method is used by system apps when silent authorization is required while user confirmation is not  
needed. Silent authorization enables system apps to directly obtain the permission to access serial port devices through system APIs without requiring user interaction. This is applicable to scenarios such as communication between internal components of the system and automatic connection between the background server and the serial port device. The system checks whether silent authorization is allowed based on **ohos.permission.MANAGE_USB_CONFIG** and grants the permission without requiring user confirmation.  
- Unlike requestSerialRight,serialManager.requestSerialRight triggers a dialog box to request user authorization, which is applicable when explicit user authorization is required. addSerialRight does not trigger a dialog box but directly adds the permission for the app to access the device, which is applicable to automatic management of system apps. After the application exits, the system automatically removes the access permission on the serial port device. After the application is restarted, the application needs to request the permission again.

**Since:** 19

**Required permissions:** ohos.permission.MANAGE_USB_CONFIG

**System capability:** SystemCapability.USB.USBManager.Serial

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| tokenId | number | Yes | App access token ID, which identifies the app that requires the permission to access the serial port device. It can be obtained using [bundleManager.getBundleInfoForSelf](../../apis-ability-kit/arkts-apis/arkts-ability-bundlemanager-getbundleinfoforself-f.md). |
| portId | number | Yes | Port number of the serial port device, which uniquely identifies the serial port device. A valid port number can be obtained using [serialManager.getPortList](arkts-basicservices-serialmanager-getportlist-f.md). Ensure that the port number exists. Otherwise, error code 31400003 will be returned. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) |  |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) |  |
| [401](../../errorcode-universal.md#401-parameter-check-failed) |  |
| [14400005](../errorcode-usb.md#14400005-database-operation-exception) |  |
| [31400001](../errorcode-usb.md#31400001-serial-port-service-error) |  |
| [31400003](../errorcode-usb.md#31400003-port-number-not-exist) |  |

**Examples**

```TypeScript
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
