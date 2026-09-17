# DeviceManager

Provides APIs to obtain information about trusted devices and local devices. Before calling any API in **DeviceManager**, you must use **createDeviceManager** to create a **DeviceManager** instance, for example, **dmInstance**.

**Since:** 10

**System capability:** SystemCapability.DistributedHardware.DeviceManager

## Modules to Import

```TypeScript
import { distributedDeviceManager } from '@kit.DistributedServiceKit';
```

## getDeviceIconInfo

```TypeScript
getDeviceIconInfo(filterOptions: DeviceIconInfoFilterOptions): Promise<DeviceIconInfo>
```

Obtains the device icon. This API uses a promise to return the result.

**Since:** 18

**Required permissions:** ohos.permission.ACCESS_SERVICE_DM

**System capability:** SystemCapability.DistributedHardware.DeviceManager

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| filterOptions | [DeviceIconInfoFilterOptions](arkts-distributedservice-distributeddevicemanager-deviceiconinfofilteroptions-i-sys.md) | Yes | Filter options. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[DeviceIconInfo](arkts-distributedservice-distributeddevicemanager-deviceiconinfo-i-sys.md)&gt; | Promise used to return the device icon information. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter type; 3. Parameter verification failed; |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [11600102](../errorcode-device-manager.md#11600102-failed-to-obtain-the-service) | Failed to obtain service. |
| [11600106](../errorcode-device-manager.md#11600106-failed-to-obtain-data-from-the-cloud) | Get data from cloud fail. |

**Examples**

```TypeScript
import { distributedDeviceManager } from '@kit.DistributedServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let dmInstance = distributedDeviceManager.createDeviceManager('ohos.samples.jsHelloWorld');
  let productIds:Array<string> = ['M0D2', 'M0D3', 'M0D5', 'M0AB', 'M0BD', 'M0E9', 'M0BC', 'M0EA'];
  let options:distributedDeviceManager.DeviceIconInfoFilterOptions = {
    productId: 'P14U',
    imageType: 'ID',
    specName: 'lg',
  };
  if (productIds.indexOf(options.productId) != -1) {
    options.internalModel = '';
  } else {
    options.subProductId = '';
  }
  dmInstance.getDeviceIconInfo(options).then((data: distributedDeviceManager.DeviceIconInfo) => {
    console.info('getDeviceIconInfo' + JSON.stringify(data));
  }).catch((e : BusinessError) => {
    console.error('getDeviceIconInfo errCode:' + e.code + ',errMessage:' + e.message);
  });
} catch (err) {
  let e: BusinessError = err as BusinessError;
  console.error('getDeviceIconInfo errCode:' + e.code + ',errMessage:' + e.message);
}
```

## getDeviceNetworkIdList

```TypeScript
getDeviceNetworkIdList(filterOptions: NetworkIdQueryFilter): Promise<Array<string>>
```

Obtains the list of network devices according to the specified filter options.

**Since:** 18

**Required permissions:** ohos.permission.ACCESS_SERVICE_DM

**System capability:** SystemCapability.DistributedHardware.DeviceManager

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| filterOptions | [NetworkIdQueryFilter](arkts-distributedservice-distributeddevicemanager-networkidqueryfilter-i-sys.md) | Yes | Filter options. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Array&lt;string&gt;&gt; | Promise used to return the device list. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Parameter verification failed; |
| [11600102](../errorcode-device-manager.md#11600102-failed-to-obtain-the-service) | Failed to obtain service. |
| [11600107](../errorcode-device-manager.md#11600107-login-account-required) | A login account is required. |

**Examples**

```TypeScript
import { distributedDeviceManager } from '@kit.DistributedServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let queryFiler: distributedDeviceManager.NetworkIdQueryFilter = {
    wiseDeviceId: '',
    onlineStatus: 1,
  }
  let dmInstance = distributedDeviceManager.createDeviceManager('ohos.samples.jsHelloWorld');
  dmInstance.getDeviceNetworkIdList(queryFiler).then((data:Array<string>) => {
    console.info('getDeviceNetworkIdList name:' + JSON.stringify(data));
  }).catch((e: BusinessError) => {
    console.error('getDeviceNetworkIdList errCode:' + e.code + ',errMessage:' + e.message);
  })
} catch (err) {
  let e: BusinessError = err as BusinessError;
  console.error('getDeviceNetworkIdList errCode:' + e.code + ',errMessage:' + e.message);
}
```

## getDeviceProfileInfoList

```TypeScript
getDeviceProfileInfoList(filterOptions: DeviceProfileInfoFilterOptions): Promise<Array<DeviceProfileInfo>>
```

Obtains the list of devices under the same account. This API uses a promise to return the result.

**Since:** 15

**Required permissions:** ohos.permission.ACCESS_SERVICE_DM

**System capability:** SystemCapability.DistributedHardware.DeviceManager

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| filterOptions | [DeviceProfileInfoFilterOptions](arkts-distributedservice-distributeddevicemanager-deviceprofileinfofilteroptions-i-sys.md) | Yes | Filter options. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Array&lt;[DeviceProfileInfo](arkts-distributedservice-distributeddevicemanager-deviceprofileinfo-i-sys.md)&gt;&gt; | Promise used to return the device list. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter type; 3. Parameter verification failed; 4. The size of specified type is greater than 500. |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [11600102](../errorcode-device-manager.md#11600102-failed-to-obtain-the-service) | Failed to obtain service. |
| [11600106](../errorcode-device-manager.md#11600106-failed-to-obtain-data-from-the-cloud) | Get data from cloud fail. |
| [11600107](../errorcode-device-manager.md#11600107-login-account-required) | A login account is required. |

**Examples**

```TypeScript
import { distributedDeviceManager } from '@kit.DistributedServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let dmInstance = distributedDeviceManager.createDeviceManager('ohos.samples.jsHelloWorld');
  dmInstance.getDeviceProfileInfoList({"isCloud": false}).then((data: Array<distributedDeviceManager.DeviceProfileInfo>) => {
    console.info('getDeviceProfileInfoList' + JSON.stringify(data));
  }).catch((e: BusinessError) => {
    console.error('getDeviceProfileInfoList errCode:' + e.code + ',errMessage:' + e.message);
  });
} catch (err) {
  let e: BusinessError = err as BusinessError;
  console.error('getDeviceProfileInfoList errCode:' + e.code + ',errMessage:' + e.message);
}
```

## getIdentificationByDeviceIds

```TypeScript
getIdentificationByDeviceIds(deviceIds: Array<string>): Array<DeviceIdentification>
```

Query device identification by device IDs.

**Since:** 24

**Required permissions:** ohos.permission.DISTRIBUTED_DATASYNC and ohos.permission.ACCESS_SERVICE_DM and ohos.permission.sec.ACCESS_UDID

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedHardware.DeviceManager

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| deviceIds | Array&lt;string&gt; | Yes | A list of device IDs that could be obtained by the application, with a maximum list size of 50.<br>The maximum length is 96 character and cannot be empty. |

**Return value:**

| Type | Description |
| --- | --- |
| Array&lt;[DeviceIdentification](arkts-distributedservice-distributeddevicemanager-deviceidentification-i-sys.md)&gt; | Returns a list of DeviceIdentification. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [11600101](../errorcode-device-manager.md#11600101-service-invoking-exception) | Failed to execute the function. |

**Examples**

```TypeScript
import { distributedDeviceManager } from '@kit.DistributedServiceKit'
private idsLists: undefined|Array<distributedDeviceManager.DeviceIdentification> = [];
getDeviceUdids(deviceIds: Array<string>): void {
  let deviceManager: distributedDeviceManager.DeviceManager | null = null;
  try {
    deviceManager = distributedDeviceManager.createDeviceManager('com.example.myapplication');
    this.idsLists = deviceManager?.getIdentificationByDeviceIds(deviceIds);
    console.info("Successfully retrieved UDID list");
  } catch (error) {
    console.error('Get device UDID failed:', error);
    this.idsLists = [];
  } finally {
    if (deviceManager) {
      try {
        distributedDeviceManager.releaseDeviceManager(deviceManager);
        console.info("deviceManager released successfully");
      } catch (releaseError) {
        console.error('Release device manager failed:', releaseError);
      }
    }
  }
}
```

## getLocalDisplayDeviceName

```TypeScript
getLocalDisplayDeviceName(maxNameLength: number): Promise<string>
```

Obtains the local device's display name with the specified length. This API uses a promise to return the result.

**Since:** 18

**Required permissions:** ohos.permission.ACCESS_SERVICE_DM

**System capability:** SystemCapability.DistributedHardware.DeviceManager

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| maxNameLength | number | Yes | Length of the local device's display name, in bytes. The value range is [18, 100]. If the value is **0**, the length is not limited. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;string&gt; | Maximum number of bytes in the local device's display name. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter type; 3. Parameter verification failed; |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [11600102](../errorcode-device-manager.md#11600102-failed-to-obtain-the-service) | Failed to obtain service. |

**Examples**

```TypeScript
import { distributedDeviceManager } from '@kit.DistributedServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let dmInstance = distributedDeviceManager.createDeviceManager('ohos.samples.jsHelloWorld');
  let maxNameLength:number = 21;
  dmInstance.getLocalDisplayDeviceName(maxNameLength).then((data:string)=>{
    console.info('getLocalDisplayDeviceName name:' + JSON.stringify(data));
  }).catch((e: BusinessError)=>{
    console.error('getLocalDisplayDeviceName errCode:' + e.code + ',errMessage:' + e.message);
  });
} catch (err) {
  let e: BusinessError = err as BusinessError;
  console.error('getLocalDisplayDeviceName errCode:' + e.code + ',errMessage:' + e.message);
}
```

## getOsTypeByNetworkId

```TypeScript
getOsTypeByNetworkId(networkId: string): number
```

Query the device operating system type by device network ID.

**Since:** 26.1.0

**Required permissions:** ohos.permission.DISTRIBUTED_DATASYNC and ohos.permission.ACCESS_SERVICE_DM

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedHardware.DeviceManager

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| networkId | string | Yes | The device's network ID |

**Return value:**

| Type | Description |
| --- | --- |
| number | Returns the device operating system type. Possible return:   1. 10: Operating system based on OpenHarmony 2. 11: Operating system not based on OpenHarmony 3. -1: Unknown |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [11600102](../errorcode-device-manager.md#11600102-failed-to-obtain-the-service) | Failed to obtain service. |
| 11600110 | Invalid network ID. |

## off('replyResult')

```TypeScript
off(type: 'replyResult', callback?: Callback<{ param: string; }>): void
```

Unsubscribes from the reply to the UI operation result.

**Since:** 10

**Required permissions:** ohos.permission.ACCESS_SERVICE_DM

**System capability:** SystemCapability.DistributedHardware.DeviceManager

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'replyResult' | Yes | Event type, which has a fixed value of **replyResult**. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;{ param: string; }&gt; | No | Callback to unregister. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter type; 3. Parameter verification failed; 4. The size of specified type is greater than 255. |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |

## on('replyResult')

```TypeScript
on(type: 'replyResult', callback: Callback<{ param: string; }>): void
```

Subscribes to the reply to the UI operation result.

**Since:** 10

**Required permissions:** ohos.permission.ACCESS_SERVICE_DM

**System capability:** SystemCapability.DistributedHardware.DeviceManager

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'replyResult' | Yes | Event type, which has a fixed value of **replyResult**. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;{ param: string; }&gt; | Yes | Callback invoked to return the UI status change. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter type; 3. Parameter verification failed; 4. The size of specified type is greater than 255. |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |

## putDeviceProfileInfoList

```TypeScript
putDeviceProfileInfoList(deviceProfileInfoList: Array<DeviceProfileInfo>): Promise<number>
```

Updates the device list. This API uses a promise to return the result.

**Since:** 18

**Required permissions:** ohos.permission.ACCESS_SERVICE_DM

**System capability:** SystemCapability.DistributedHardware.DeviceManager

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| deviceProfileInfoList | Array&lt;[DeviceProfileInfo](arkts-distributedservice-distributeddevicemanager-deviceprofileinfo-i-sys.md)&gt; | Yes | Device list. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;number&gt; | Operation result. The value **0** indicates that the operation is successful. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter type; 3. Parameter verification failed; 4. The size of specified type is greater than 500. |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [11600102](../errorcode-device-manager.md#11600102-failed-to-obtain-the-service) | Failed to obtain service. |

**Examples**

```TypeScript
import { distributedDeviceManager } from '@kit.DistributedServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let dmInstance = distributedDeviceManager.createDeviceManager('ohos.samples.jsHelloWorld');
  let deviceProfileInfoList:Array<distributedDeviceManager.DeviceProfileInfo> = [];
  dmInstance.putDeviceProfileInfoList(deviceProfileInfoList).then((data:number) => {
    console.info('put device profile info:' + JSON.stringify(data));
  }).catch((e: BusinessError) => {
    console.error('putDeviceProfileInfoList errCode:' + e.code + ',errMessage:' + e.message);
  });
} catch (err) {
  let e: BusinessError = err as BusinessError;
  console.error('putDeviceProfileInfoList errCode:' + e.code + ',errMessage:' + e.message);
}
```

## replyUiAction

```TypeScript
replyUiAction(action: number, actionResult: string): void
```

Replies to the user's UI operation. This API can be used only by the PIN HAP of the **deviceManager**.

**Since:** 10

**Required permissions:** ohos.permission.ACCESS_SERVICE_DM

**System capability:** SystemCapability.DistributedHardware.DeviceManager

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| action | number | Yes | User operation.<br>- **0**: Grant the permission. <br>- **1**. Remove the permission. <br>-**2**: Time out the user operation in the permission request dialog. <br>- **3**: Cancel the display of the PIN box. <br>- **4**: Cancel the display of the PIN input box. <br>- **5**: Confirm the input in the PIN input box. |
| actionResult | string | Yes | User operation result. The value is a string of 1 to 255 characters. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter type; 3. Parameter verification failed; 4. The size of specified actionResult is greater than 255. |

**Examples**

```TypeScript
import { distributedDeviceManager } from '@kit.DistributedServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  /**
   * action = 0 - Grant the permission.
   * action = 1 - Revoke the permission.
   * action = 2 - Time out the user operation in the permission request dialog.
   * action = 3 - Cancel the display of the PIN box.
   * action = 4 - Cancel the display of the PIN input box.
   * action = 5 - Confirm the input in the PIN input box.
   */
  let operation = 0;
  let dmInstance = distributedDeviceManager.createDeviceManager('ohos.samples.jsHelloWorld');
  dmInstance.replyUiAction(operation, 'extra');
} catch (err) {
  let e: BusinessError = err as BusinessError;
  console.error('replyUiAction errCode:' + e.code + ',errMessage:' + e.message);
}
```

## restoreLocalDeivceName

```TypeScript
restoreLocalDeivceName(): void
```

Restores the local device name by resetting the network settings.

**Since:** 18

**Deprecated since:** 24

**Substitutes:** [restoreLocalDeviceName](#restorelocaldevicename)

**Required permissions:** ohos.permission.ACCESS_SERVICE_DM

**System capability:** SystemCapability.DistributedHardware.DeviceManager

**System API:** This is a system API.

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [11600102](../errorcode-device-manager.md#11600102-failed-to-obtain-the-service) | Failed to obtain the service. |

**Examples**

```TypeScript
import { distributedDeviceManager } from '@kit.DistributedServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let dmInstance = distributedDeviceManager.createDeviceManager('ohos.samples.jsHelloWorld');
  dmInstance.restoreLocalDeivceName();
} catch (err) {
  let e: BusinessError = err as BusinessError;
  console.error('restoreLocalDeivceName errCode:' + e.code + ',errMessage:' + e.message);
}
```

## restoreLocalDeviceName

```TypeScript
restoreLocalDeviceName(): void
```

Restores the local device name.

**Since:** 24

**Required permissions:** ohos.permission.ACCESS_SERVICE_DM

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedHardware.DeviceManager

**System API:** This is a system API.

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [11600102](../errorcode-device-manager.md#11600102-failed-to-obtain-the-service) | Failed to obtain the service. |

**Examples**

```TypeScript
import { distributedDeviceManager } from '@kit.DistributedServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let dmInstance = distributedDeviceManager.createDeviceManager('ohos.samples.jsHelloWorld');
  dmInstance.restoreLocalDeviceName();
} catch (err) {
  let e: BusinessError = err as BusinessError;
  console.error('restoreLocalDeviceName errCode:' + e.code + ',errMessage:' + e.message);
}
```

## setHeartbeatPolicy

```TypeScript
setHeartbeatPolicy(policy: StrategyForHeartbeat, delayTime: number): void
```

Sets the heartbeat broadcast policy.

**Since:** 15

**Required permissions:** ohos.permission.ACCESS_SERVICE_DM

**System capability:** SystemCapability.DistributedHardware.DeviceManager

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| policy | [StrategyForHeartbeat](arkts-distributedservice-distributeddevicemanager-strategyforheartbeat-e-sys.md) | Yes | Heartbeat broadcast policy. |
| delayTime | number | Yes | Duration for temporarily disabling heartbeat broadcast. The value ranges from 1000 to 15000, in milliseconds. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [11600102](../errorcode-device-manager.md#11600102-failed-to-obtain-the-service) | Failed to obtain service. |

**Examples**

```TypeScript
import { distributedDeviceManager } from '@kit.DistributedServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let policy = distributedDeviceManager.StrategyForHeartbeat.TEMP_STOP_HEARTBEAT;
  let delayTime = 1000;
  let dmInstance = distributedDeviceManager.createDeviceManager('ohos.samples.jsHelloWorld');
  dmInstance.setHeartbeatPolicy(policy, delayTime);
} catch (err) {
  let e: BusinessError = err as BusinessError;
  console.error('setHeartbeatPolicy errCode:' + e.code + ',errMessage:' + e.message);
}
```

## setLocalDeviceName

```TypeScript
setLocalDeviceName(deviceName: string): Promise<number>
```

Sets the local device name. This API uses a promise to return the result.

**Since:** 18

**Required permissions:** ohos.permission.ACCESS_SERVICE_DM

**System capability:** SystemCapability.DistributedHardware.DeviceManager

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| deviceName | string | Yes | Device name to set. The value is a string of 1 to 255 characters. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;number&gt; | Operation result. The value **0** indicates that the operation is successful. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter type; 3. Parameter verification failed; |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [11600102](../errorcode-device-manager.md#11600102-failed-to-obtain-the-service) | Failed to obtain service. |
| [11600106](../errorcode-device-manager.md#11600106-failed-to-obtain-data-from-the-cloud) | Failed to get data from the cloud. |
| [11600107](../errorcode-device-manager.md#11600107-login-account-required) | A login account is required. |
| [11600108](../errorcode-device-manager.md#11600108-unlawful-information-in-device-name) | The device name contains non-compliant content. |

**Examples**

```TypeScript
import { distributedDeviceManager } from '@kit.DistributedServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let dmInstance = distributedDeviceManager.createDeviceManager('ohos.samples.jsHelloWorld');
  let deviceName:string = 'xxx';
  dmInstance.setLocalDeviceName(deviceName).then((data:number)=>{
    console.info('setLocalDeviceName name:' + JSON.stringify(data));
  }).catch((e: BusinessError)=>{
    console.error('setLocalDeviceName errCode:' + e.code + ',errMessage:' + e.message);
  });
} catch (err) {
  let e: BusinessError = err as BusinessError;
  console.error('setLocalDeviceName errCode:' + e.code + ',errMessage:' + e.message);
}
```

## setRemoteDeviceName

```TypeScript
setRemoteDeviceName(deviceId: string, deviceName: string): Promise<number>
```

Sets the remote device name. This API uses a promise to return the result.

**Since:** 18

**Required permissions:** ohos.permission.ACCESS_SERVICE_DM

**System capability:** SystemCapability.DistributedHardware.DeviceManager

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| deviceId | string | Yes | UDID of the remote device. If the device does not have a UDID, the MAC address or SN of the device is used as the device ID. The SN is used preferentially. |
| deviceName | string | Yes | Device name to set. The value is a string of 1 to 255 characters. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;number&gt; | Operation result. The value **0** indicates that the operation is successful. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter type; 3. Parameter verification failed; |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [11600102](../errorcode-device-manager.md#11600102-failed-to-obtain-the-service) | Failed to obtain service. |
| [11600106](../errorcode-device-manager.md#11600106-failed-to-obtain-data-from-the-cloud) | Failed to get data from the cloud. |
| [11600107](../errorcode-device-manager.md#11600107-login-account-required) | A login account is required. |
| [11600108](../errorcode-device-manager.md#11600108-unlawful-information-in-device-name) | The device name contains non-compliant content. |

**Examples**

```TypeScript
import { distributedDeviceManager } from '@kit.DistributedServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let dmInstance = distributedDeviceManager.createDeviceManager('ohos.samples.jsHelloWorld');
  let deviceId:string = 'xxx';
  let deviceName:string = 'xxx';
  dmInstance.setRemoteDeviceName(deviceId, deviceName).then((data:number)=>{
    console.info('setRemoteDeviceName name:' + JSON.stringify(data));
  }).catch((e: BusinessError)=>{
    console.error('setRemoteDeviceName errCode:' + e.code + ',errMessage:' + e.message);
  });
} catch (err) {
  let e: BusinessError = err as BusinessError;
  console.error('setRemoteDeviceName errCode:' + e.code + ',errMessage:' + e.message);
}
```
