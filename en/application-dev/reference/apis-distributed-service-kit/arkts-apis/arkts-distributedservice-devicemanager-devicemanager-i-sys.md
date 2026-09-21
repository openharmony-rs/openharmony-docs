# DeviceManager

```TypeScript
interface DeviceManager
```

Provides APIs to obtain information about trusted devices and local devices. Before calling any API in **DeviceManager**, you must use **createDeviceManager** to create a **DeviceManager** instance, for example, **dmInstance**.

**Since:** 7

**Deprecated since:** 11

**Substitutes:** [DeviceManager](arkts-distributedservice-distributeddevicemanager-devicemanager-i.md)

**System capability:** SystemCapability.DistributedHardware.DeviceManager

## Modules to Import

```TypeScript
import { deviceManager } from '@kit.DistributedServiceKit';
```

## authenticateDevice

```TypeScript
authenticateDevice(
      deviceInfo: DeviceInfo,
      authParam: AuthParam,
      callback: AsyncCallback<{ deviceId: string, pinToken?: number }>
    ): void
```

Authenticates a device.

**Since:** 7

**Deprecated since:** 11

**Substitutes:** [bindTarget](arkts-distributedservice-distributeddevicemanager-devicemanager-i.md#bindtarget)(deviceId: string, bindParam: { [key: string]: Object; }, callback: AsyncCallback&lt;{deviceId: string;}&gt;)

**Required permissions:** ohos.permission.ACCESS_SERVICE_DM

**System capability:** SystemCapability.DistributedHardware.DeviceManager

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| deviceInfo | [DeviceInfo](arkts-distributedservice-devicemanager-deviceinfo-i-sys.md) | Yes | Device information. |
| authParam | [AuthParam](arkts-distributedservice-devicemanager-authparam-i-sys.md) | Yes | Authentication parameter. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;{ deviceId: string, pinToken?: number }&gt; | Yes | Callback used to return the authentication result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter type; 3. Parameter verification failed. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |

**Examples**

For details about how to initialize  in the example, see deviceManager.createDeviceManager.

```TypeScript
import { BusinessError } from '@ohos.base';

class Data {
  deviceId: string = "";
  pinToken?: number = 0;
}

interface DeviceInfo {
  deviceId: string;
  deviceName: string;
  deviceType: number;
  networkId: string;
  range: number;
};

interface ExtraInfo {
  targetPkgName: string;
  appName: string;
  appDescription: string;
  business: string;
}

interface AuthParam {
  authType: number; // Authentication type. The value 1 means no account PIN authentication.
  extraInfo: ExtraInfo;
}

// Information about the device to authenticate. The information can be obtained from the device discovery result.
let deviceInfo: deviceManager.DeviceInfo = {
  deviceId: "XXXXXXXX",
  deviceName: "",
  deviceType: 0x0E,
  networkId: "xxxxxxx",
  range: 0,
  authForm: 0
};
let extraInfo: ExtraInfo = {
  targetPkgName: 'ohos.samples.xxx',
  appName: 'xxx',
  appDescription: 'xxx',
  business: '0'
};
let authParam: AuthParam = {
  authType: 1, // Authentication type. The value 1 means no account PIN authentication.
  extraInfo: extraInfo
};

try {
  dmInstance.authenticateDevice(deviceInfo, authParam, (err: BusinessError, data: Data) => {
    if (err) {
      console.error("authenticateDevice errCode:" + err.code + ",errMessage:" + err.message);
      return;
    }
    console.info("authenticateDevice result:" + JSON.stringify(data));
    let token = data.pinToken;
  });
} catch (err) {
  let e: BusinessError = err as BusinessError;
  console.error("authenticateDevice errCode:" + e.code + ",errMessage:" + e.message);
}
```

## deleteCredential

```TypeScript
deleteCredential(queryInfo: string, callback: AsyncCallback<{ resultInfo: string }>): void
```

Deletes credential information.

**Since:** 10

**Deprecated since:** 11

**Required permissions:** ohos.permission.ACCESS_SERVICE_DM

**System capability:** SystemCapability.DistributedHardware.DeviceManager

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| queryInfo | string | Yes | Credential information to delete. The value is a string of 1 to 64000 characters. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;{ resultInfo: string }&gt; | Yes | Callback used to return the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter type; 3. Parameter verification failed; 4. The size of specified queryInfo is greater than 5999. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |

**Examples**

For details about how to initialize  in the example, see deviceManager.createDeviceManager.

```TypeScript
import { BusinessError } from '@ohos.base';

class Data {
  resultInfo: string = "";
}

interface QueryInfo {
  processType: number;
  authType: number;
  userId: string;
}

let queryInfo: QueryInfo = {
  processType: 1,
  authType: 1,
  userId: "123"
};

try {
  let jsonQueryInfo = JSON.stringify(queryInfo);
  dmInstance.deleteCredential(jsonQueryInfo, (err: BusinessError, data: Data) => {
    if (data) {
      console.info("deleteCredential result:" + JSON.stringify(data));
    } else {
      console.info("deleteCredential result: data is null");
    }
  });
} catch (err) {
  let e: BusinessError = err as BusinessError;
  console.error("deleteCredential err:" + e.code + "," + e.message);
}
```

## getDeviceInfo

```TypeScript
getDeviceInfo(networkId: string, callback: AsyncCallback<DeviceInfo>): void
```

Obtains the information about a specific device based on the network ID. This API uses an asynchronous callback to return the result.

**Since:** 10

**Deprecated since:** 11

**Substitutes:** [getDeviceName](arkts-distributedservice-distributeddevicemanager-devicemanager-i.md#getdevicename)

**Required permissions:** ohos.permission.ACCESS_SERVICE_DM

**System capability:** SystemCapability.DistributedHardware.DeviceManager

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| networkId | string | Yes | Network ID of the device. The value is a string of 1 to 255 characters. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[DeviceInfo](arkts-distributedservice-devicemanager-deviceinfo-i-sys.md)&gt; | Yes | Callback used to return the information about the specified device. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter type; 3. Parameter verification failed; 4. The size of specified networkId is greater than 255. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |

**Examples**

For details about how to initialize  in the example, see deviceManager.createDeviceManager.

```TypeScript
import deviceManager from '@ohos.distributedHardware.deviceManager';
import { BusinessError } from '@ohos.base';

try {
  // Network ID of the device, which can be obtained from the trusted device list
  let networkId = "xxxxxxx";
  dmInstance.getDeviceInfo(networkId, (err: BusinessError, data: deviceManager.DeviceInfo) => {
    if (err) {
      console.error("getDeviceInfo errCode:" + err.code + ",errMessage:" + err.message);
      return;
    }
    console.info('get device info: ' + JSON.stringify(data));
  });
} catch (err) {
  let e: BusinessError = err as BusinessError;
  console.error("getDeviceInfo errCode:" + e.code + ",errMessage:" + e.message);
}
```

<a id="getdeviceinfo-1"></a>

## getDeviceInfo

```TypeScript
getDeviceInfo(networkId: string): Promise<DeviceInfo>
```

Obtains the information about a specific device based on the network ID. This API uses a promise to return the result.

**Since:** 10

**Deprecated since:** 11

**Substitutes:** [getDeviceName](arkts-distributedservice-distributeddevicemanager-devicemanager-i.md#getdevicename)

**Required permissions:** ohos.permission.ACCESS_SERVICE_DM

**System capability:** SystemCapability.DistributedHardware.DeviceManager

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| networkId | string | Yes | Network ID of the device. The value is a string of 1 to 255 characters. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[DeviceInfo](arkts-distributedservice-devicemanager-deviceinfo-i-sys.md)&gt; | Promise used to return the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter type; 3. Parameter verification failed; 4. The size of specified networkId is greater than 255. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |

**Examples**

For details about how to initialize  in the example, see deviceManager.createDeviceManager.

```TypeScript
import deviceManager from '@ohos.distributedHardware.deviceManager';
import { BusinessError } from '@ohos.base';

// Network ID of the device, which can be obtained from the trusted device list
let networkId = "xxxxxxx";
dmInstance.getDeviceInfo(networkId).then((data: deviceManager.DeviceInfo) => {
  console.info('get device info: ' + JSON.stringify(data));
}).catch((err: BusinessError) => {
  console.error("getDeviceInfo errCode:" + err.code + ",errMessage:" + err.message);
});
```

## getLocalDeviceInfo

```TypeScript
getLocalDeviceInfo(callback: AsyncCallback<DeviceInfo>): void
```

Obtains local device information. This API uses an asynchronous callback to return the result.

**Since:** 8

**Deprecated since:** 11

**Substitutes:** [getLocalDeviceNetworkId](arkts-distributedservice-distributeddevicemanager-devicemanager-i.md#getlocaldevicenetworkid)

**Required permissions:** ohos.permission.ACCESS_SERVICE_DM

**System capability:** SystemCapability.DistributedHardware.DeviceManager

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[DeviceInfo](arkts-distributedservice-devicemanager-deviceinfo-i-sys.md)&gt; | Yes | Callback used to return the local device information. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter type; 3. Parameter verification failed. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |

**Examples**

For details about how to initialize  in the example, see deviceManager.createDeviceManager.

```TypeScript
import deviceManager from '@ohos.distributedHardware.deviceManager';
import { BusinessError } from '@ohos.base';


try {
  dmInstance.getLocalDeviceInfo((err: BusinessError, data: deviceManager.DeviceInfo) => {
    if (err) {
      console.error("getLocalDeviceInfo errCode:" + err.code + ",errMessage:" + err.message);
      return;
    }
    console.info('get local device info: ' + JSON.stringify(data));
  });
} catch (err) {
  let e: BusinessError = err as BusinessError;
  console.error("getLocalDeviceInfo errCode:" + e.code + ",errMessage:" + e.message);
}
```

<a id="getlocaldeviceinfo-1"></a>

## getLocalDeviceInfo

```TypeScript
getLocalDeviceInfo(): Promise<DeviceInfo>
```

Obtains local device information. This API uses a promise to return the result.

**Since:** 8

**Deprecated since:** 11

**Substitutes:** [getLocalDeviceNetworkId](arkts-distributedservice-distributeddevicemanager-devicemanager-i.md#getlocaldevicenetworkid)

**Required permissions:** ohos.permission.ACCESS_SERVICE_DM

**System capability:** SystemCapability.DistributedHardware.DeviceManager

**System API:** This is a system API.

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[DeviceInfo](arkts-distributedservice-devicemanager-deviceinfo-i-sys.md)&gt; | Promise used to return the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |

**Examples**

For details about how to initialize  in the example, see deviceManager.createDeviceManager.

```TypeScript
import deviceManager from '@ohos.distributedHardware.deviceManager';
import { BusinessError } from '@ohos.base';

dmInstance.getLocalDeviceInfo().then((data: deviceManager.DeviceInfo) => {
  console.info('get local device info: ' + JSON.stringify(data));
}).catch((err: BusinessError) => {
  console.error("getLocalDeviceInfo errCode:" + err.code + ",errMessage:" + err.message);
});
```

## getLocalDeviceInfoSync

```TypeScript
getLocalDeviceInfoSync(): DeviceInfo
```

Obtains local device information synchronously.

**Since:** 8

**Deprecated since:** 11

**Substitutes:** [getLocalDeviceNetworkId](arkts-distributedservice-distributeddevicemanager-devicemanager-i.md#getlocaldevicenetworkid)

**Required permissions:** ohos.permission.ACCESS_SERVICE_DM

**System capability:** SystemCapability.DistributedHardware.DeviceManager

**System API:** This is a system API.

**Return value:**

| Type | Description |
| --- | --- |
| [DeviceInfo](arkts-distributedservice-devicemanager-deviceinfo-i-sys.md) | List of local devices obtained. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [11600101](../errorcode-device-manager.md#11600101-service-invoking-exception) | Failed to execute the function. |

**Examples**

For details about how to initialize  in the example, see deviceManager.createDeviceManager.

```TypeScript
import deviceManager from '@ohos.distributedHardware.deviceManager';
import { BusinessError } from '@ohos.base';

try {
  let deviceInfo: deviceManager.DeviceInfo = dmInstance.getLocalDeviceInfoSync();
} catch (err) {
  let e: BusinessError = err as BusinessError;
  console.error("getLocalDeviceInfoSync errCode:" + e.code + ",errMessage:" + e.message);
}
```

## getTrustedDeviceList

```TypeScript
getTrustedDeviceList(callback: AsyncCallback<Array<DeviceInfo>>): void
```

Obtains all trusted devices. This API uses an asynchronous callback to return the result.

**Since:** 8

**Deprecated since:** 11

**Substitutes:** [getAvailableDeviceList](arkts-distributedservice-distributeddevicemanager-devicemanager-i.md#getavailabledevicelist)(callback: AsyncCallback&lt;Array&lt;DeviceBasicInfo&gt;&gt;)

**Required permissions:** ohos.permission.ACCESS_SERVICE_DM

**System capability:** SystemCapability.DistributedHardware.DeviceManager

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;Array&lt;[DeviceInfo](arkts-distributedservice-devicemanager-deviceinfo-i-sys.md)&gt;&gt; | Yes | Callback used to return the list of trusted devices. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter type; 3. Parameter verification failed. |

**Examples**

For details about how to initialize  in the example, see deviceManager.createDeviceManager.

```TypeScript
import deviceManager from '@ohos.distributedHardware.deviceManager';
import { BusinessError } from '@ohos.base';

try {
  dmInstance.getTrustedDeviceList((err: BusinessError, data: Array<deviceManager.DeviceInfo>) => {
    if (err) {
      console.error("getTrustedDeviceList errCode:" + err.code + ",errMessage:" + err.message);
      return;
    }
    console.info('get trusted device info: ' + JSON.stringify(data));
  });
} catch (err) {
  let e: BusinessError = err as BusinessError;
  console.error("getTrustedDeviceList errCode:" + e.code + ",errMessage:" + e.message);
}
```

<a id="gettrusteddevicelist-1"></a>

## getTrustedDeviceList

```TypeScript
getTrustedDeviceList(): Promise<Array<DeviceInfo>>
```

Obtains all trusted devices. This API uses a promise to return the result.

**Since:** 8

**Deprecated since:** 11

**Substitutes:** [getAvailableDeviceList](arkts-distributedservice-distributeddevicemanager-devicemanager-i.md#getavailabledevicelist)()

**Required permissions:** ohos.permission.ACCESS_SERVICE_DM

**System capability:** SystemCapability.DistributedHardware.DeviceManager

**System API:** This is a system API.

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Array&lt;[DeviceInfo](arkts-distributedservice-devicemanager-deviceinfo-i-sys.md)&gt;&gt; | Promise used to return the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |

**Examples**

For details about how to initialize  in the example, see deviceManager.createDeviceManager.

```TypeScript
import deviceManager from '@ohos.distributedHardware.deviceManager';
import { BusinessError } from '@ohos.base';

dmInstance.getTrustedDeviceList().then((data: Array<deviceManager.DeviceInfo>) => {
  console.info('get trusted device info: ' + JSON.stringify(data));
  }).catch((err: BusinessError) => {
    console.error("getTrustedDeviceList errCode:" + err.code + ",errMessage:" + err.message);
});
```

## getTrustedDeviceListSync

```TypeScript
getTrustedDeviceListSync(): Array<DeviceInfo>
```

Obtains all trusted devices synchronously.

**Since:** 7

**Deprecated since:** 11

**Substitutes:** [getAvailableDeviceListSync](arkts-distributedservice-distributeddevicemanager-devicemanager-i.md#getavailabledevicelistsync)

**Required permissions:** ohos.permission.ACCESS_SERVICE_DM

**System capability:** SystemCapability.DistributedHardware.DeviceManager

**System API:** This is a system API.

**Return value:**

| Type | Description |
| --- | --- |
| Array&lt;[DeviceInfo](arkts-distributedservice-devicemanager-deviceinfo-i-sys.md)&gt; | List of trusted devices obtained. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [11600101](../errorcode-device-manager.md#11600101-service-invoking-exception) | Failed to execute the function. |

**Examples**

For details about how to initialize  in the example, see deviceManager.createDeviceManager.

```TypeScript
import deviceManager from '@ohos.distributedHardware.deviceManager';
import { BusinessError } from '@ohos.base';

try {
  let deviceInfoList: Array<deviceManager.DeviceInfo> = dmInstance.getTrustedDeviceListSync();
} catch (err) {
  let e: BusinessError = err as BusinessError;
  console.error("getTrustedDeviceListSync errCode:" + e.code + ",errMessage:" + e.message);
}
```

<a id="gettrusteddevicelistsync-1"></a>

## getTrustedDeviceListSync

```TypeScript
getTrustedDeviceListSync(isRefresh: boolean): Array<DeviceInfo>
```

Enables the DSoftBus heartbeat mode to quickly bring offline trusted devices online and updates the list of online trusted devices.

**Since:** 10

**Deprecated since:** 11

**Required permissions:** ohos.permission.ACCESS_SERVICE_DM

**System capability:** SystemCapability.DistributedHardware.DeviceManager

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| isRefresh | boolean | Yes | Whether to enable the heartbeat mode and update the list of online trusted devices. The value **true** means to enable the heartbeat mode and update the list of online trusted devices and the value **false** means the opposite. |

**Return value:**

| Type | Description |
| --- | --- |
| Array&lt;[DeviceInfo](arkts-distributedservice-devicemanager-deviceinfo-i-sys.md)&gt; | List of trusted devices obtained. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter type; 3. Parameter verification failed. |
| [11600101](../errorcode-device-manager.md#11600101-service-invoking-exception) | Failed to execute the function. |

**Examples**

For details about how to initialize  in the example, see deviceManager.createDeviceManager.

```TypeScript
import deviceManager from '@ohos.distributedHardware.deviceManager';
import { BusinessError } from '@ohos.base';

try {
  let deviceInfoList: Array<deviceManager.DeviceInfo> = dmInstance.getTrustedDeviceListSync(true);
} catch (err) {
  let e: BusinessError = err as BusinessError;
  console.error("getTrustedDeviceListSync errCode:" + e.code + ",errMessage:" + e.message);
}
```

## importCredential

```TypeScript
importCredential(credentialInfo: string, callback: AsyncCallback<{ resultInfo: string }>): void
```

Imports credential information.

**Since:** 10

**Deprecated since:** 11

**Required permissions:** ohos.permission.ACCESS_SERVICE_DM

**System capability:** SystemCapability.DistributedHardware.DeviceManager

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| credentialInfo | string | Yes | Credential information to import. The value is a string of 1 to 64000 characters. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;{ resultInfo: string }&gt; | Yes | Callback used to return the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter type; 3. Parameter verification failed; 4. The size of specified credentialInfo is greater than 5999. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |

**Examples**

For details about how to initialize  in the example, see deviceManager.createDeviceManager.

```TypeScript
import { BusinessError } from '@ohos.base';

class Data {
  resultInfo: string = "";
}

interface CredentialData {
  credentialType: number;
  credentialId: string;
  serverPk: string;
  pkInfoSignature : string;
  pkInfo: string;
  authCode: string;
  peerDeviceId: string;
}

interface CredentialInfo {
  processType: number;
  authType: number;
  userId: string;
  deviceId: string;
  version: string;
  devicePk : string;
  credentialData : CredentialData;
}

let credentialData: CredentialData = {
  credentialType: 2,
  credentialId: "102",
  serverPk: "3059301306072A8648CE3D020106082A8648CE3D03",
  pkInfoSignature : "30440220490BCB4F822004C9A76AB8D97F80041FC0E",
  pkInfo: "",
  authCode: "",
  peerDeviceId: ""
};


let credentialInfo: CredentialInfo = {
  processType: 1,
  authType: 1,
  userId: "123",
  deviceId: "aaa",
  version: "1.2.3",
  devicePk : "0000",
  credentialData : credentialData
};

try {
  let jsonCredentialInfo = JSON.stringify(credentialInfo);
  dmInstance.importCredential(jsonCredentialInfo, (err: BusinessError, data: Data) => {
    if (data) {
      console.info("importCredential result:" + JSON.stringify(data));
    } else {
      console.info("importCredential result: data is null");
    }
  });
} catch (err) {
  let e: BusinessError = err as BusinessError;
  console.error("importCredential err:" + e.code + "," + e.message);
}
```

## off('uiStateChange')

```TypeScript
off(type: 'uiStateChange', callback?: Callback<{ param: string }>): void
```

Unsubscribes from UI status changes.

**Since:** 9

**Deprecated since:** 11

**Substitutes:** off(type: 'replyResult', callback: Callback&lt;{ param: string; }&gt;)

**Required permissions:** ohos.permission.ACCESS_SERVICE_DM

**System capability:** SystemCapability.DistributedHardware.DeviceManager

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'uiStateChange' | Yes | Event type, which has a fixed value of **uiStateChange**. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;{ param: string }&gt; | No | Callback used to return the UI status. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter type; 3. Parameter verification failed; 4. The size of specified eventType is greater than 255. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |

**Examples**

For details about how to initialize  in the example, see deviceManager.createDeviceManager.

```TypeScript
import { BusinessError } from '@ohos.base';

try {
  dmInstance.off('uiStateChange');
} catch (err) {
  let e: BusinessError = err as BusinessError;
  console.error("uiStateChange errCode:" + e.code + ",errMessage:" + e.message);
}
```

## off('deviceStateChange')

```TypeScript
off(type: 'deviceStateChange', callback?: Callback<{ action: DeviceStateChangeAction, device: DeviceInfo }>): void
```

Unsubscribes from changes in the device state.

**Since:** 7

**Deprecated since:** 11

**Substitutes:** [off](arkts-distributedservice-distributeddevicemanager-devicemanager-i.md#offdevicestatechange)(type: 'deviceStateChange', callback?: Callback&lt;{ action: DeviceStateChange; device: DeviceBasicInfo; }&gt;)

**Required permissions:** ohos.permission.ACCESS_SERVICE_DM

**System capability:** SystemCapability.DistributedHardware.DeviceManager

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'deviceStateChange' | Yes | Event type, which has a fixed value of **deviceStateChange**. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;{ action: DeviceStateChangeAction, device: DeviceInfo }&gt; | No | Callback used to return the device information and state. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter type; 3. Parameter verification failed; 4. The size of specified eventType is greater than 255. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |

**Examples**

For details about how to initialize  in the example, see deviceManager.createDeviceManager.

```TypeScript
import deviceManager from '@ohos.distributedHardware.deviceManager';
import { BusinessError } from '@ohos.base';

class Data {
  action: deviceManager.DeviceStateChangeAction = 0;
  device: deviceManager.DeviceInfo = {
    deviceId: "",
    deviceName: "",
    deviceType: 0,
    networkId: "",
    range: 0,
    authForm:0
  };
}

try {
  dmInstance.off('deviceStateChange', (data: Data) => {
    console.info('deviceStateChange' + JSON.stringify(data));
  });
} catch (err) {
  let e: BusinessError = err as BusinessError;
  console.error("deviceStateChange errCode:" + e.code + ",errMessage:" + e.message);
}
```

## off('deviceFound')

```TypeScript
off(type: 'deviceFound', callback?: Callback<{ subscribeId: number, device: DeviceInfo }>): void
```

Unsubscribes from device discovery events.

**Since:** 7

**Deprecated since:** 11

**Substitutes:** off(type: 'discoverSuccess', callback: Callback&lt;{ device: DeviceBasicInfo; }&gt;)

**Required permissions:** ohos.permission.ACCESS_SERVICE_DM

**System capability:** SystemCapability.DistributedHardware.DeviceManager

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'deviceFound' | Yes | Event type, which has a fixed value of **deviceFound**. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;{ subscribeId: number, device: DeviceInfo }&gt; | No | Callback used to return the device information and state. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter type; 3. Parameter verification failed; 4. The size of specified eventType is greater than 255. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |

**Examples**

For details about how to initialize  in the example, see deviceManager.createDeviceManager.

```TypeScript
import deviceManager from '@ohos.distributedHardware.deviceManager';
import { BusinessError } from '@ohos.base';

class Data {
  subscribeId: number = 0;
  device: deviceManager.DeviceInfo = {
    deviceId: "",
    deviceName: "",
    deviceType: 0,
    networkId: "",
    range: 0,
    authForm:0
  };
}

try {
  dmInstance.off('deviceFound', (data: Data) => {
    console.info('deviceFound' + JSON.stringify(data));
  });
} catch (err) {
  let e: BusinessError = err as BusinessError;
  console.error("deviceFound errCode:" + e.code + ",errMessage:" + e.message);
}
```

## off('discoverFail')

```TypeScript
off(type: 'discoverFail', callback?: Callback<{ subscribeId: number, reason: number }>): void
```

Unsubscribes from device discovery failures.

**Since:** 7

**Deprecated since:** 11

**Substitutes:** off(type: 'discoverFailure', callback: Callback&lt;{ reason: number; }&gt;)

**Required permissions:** ohos.permission.ACCESS_SERVICE_DM

**System capability:** SystemCapability.DistributedHardware.DeviceManager

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'discoverFail' | Yes | Event type, which has a fixed value of **discoverFail**. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;{ subscribeId: number, reason: number }&gt; | No | Callback used for the device discovery failure. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter type; 3. Parameter verification failed; 4. The size of specified eventType is greater than 255. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |

**Examples**

For details about how to initialize  in the example, see deviceManager.createDeviceManager.

```TypeScript
import { BusinessError } from '@ohos.base';

class Data {
  subscribeId: number = 0;
  reason: number = 0;
}

try {
  dmInstance.off('discoverFail', (data: Data) => {
    console.info('discoverFail' + JSON.stringify(data));
  });
} catch (err) {
  let e: BusinessError = err as BusinessError;
  console.error("discoverFail errCode:" + e.code + ",errMessage:" + e.message);
}
```

## off('publishSuccess')

```TypeScript
off(type: 'publishSuccess', callback?: Callback<{ publishId: number }>): void
```

Unsubscribes from device information publication success events.

**Since:** 9

**Deprecated since:** 11

**Required permissions:** ohos.permission.ACCESS_SERVICE_DM

**System capability:** SystemCapability.DistributedHardware.DeviceManager

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'publishSuccess' | Yes | Event type, which has a fixed value of **publishSuccess**. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;{ publishId: number }&gt; | No | Callback used to return the publish ID. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter type; 3. Parameter verification failed; 4. The size of specified eventType is greater than 255. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |

**Examples**

For details about how to initialize  in the example, see deviceManager.createDeviceManager.

```TypeScript
import { BusinessError } from '@ohos.base';

class Data {
  publishId: number = 0;
}

try {
  dmInstance.off('publishSuccess', (data: Data) => {
    console.info('publishSuccess' + JSON.stringify(data));
  });
} catch (err) {
  let e: BusinessError = err as BusinessError;
  console.error("publishSuccess errCode:" + e.code + ",errMessage:" + e.message);
}
```

## off('publishFail')

```TypeScript
off(type: 'publishFail', callback?: Callback<{ publishId: number, reason: number }>): void
```

Unsubscribes from device information publication failures.

**Since:** 9

**Deprecated since:** 11

**Required permissions:** ohos.permission.ACCESS_SERVICE_DM

**System capability:** SystemCapability.DistributedHardware.DeviceManager

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'publishFail' | Yes | Event type, which has a fixed value of **publishFail**. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;{ publishId: number, reason: number }&gt; | No | Callback used for the device discovery failure. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter type; 3. Parameter verification failed; 4. The size of specified eventType is greater than 255. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |

**Examples**

For details about how to initialize  in the example, see deviceManager.createDeviceManager.

```TypeScript
import { BusinessError } from '@ohos.base';

class Data {
  publishId: number = 0;
  reason: number = 0;
}

try {
  dmInstance.off('publishFail', (data: Data) => {
    console.info('publishFail' + JSON.stringify(data));
  });
} catch (err) {
  let e: BusinessError = err as BusinessError;
  console.error("publishFail errCode:" + e.code + ",errMessage:" + e.message);
}
```

## off('serviceDie')

```TypeScript
off(type: 'serviceDie', callback?: () => void): void
```

Unsubscribes from dead events of the **DeviceManager** service.

**Since:** 7

**Deprecated since:** 11

**Substitutes:** [off](arkts-distributedservice-distributeddevicemanager-devicemanager-i.md#offservicedie)(type: 'serviceDie', callback?: Callback&lt;{}&gt;)

**Required permissions:** ohos.permission.ACCESS_SERVICE_DM

**System capability:** SystemCapability.DistributedHardware.DeviceManager

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'serviceDie' | Yes | Event type, which has a fixed value of **serviceDie**. |
| callback | () =&gt; void | No | Callback used to return the dead event of the **DeviceManager** service. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter type; 3. Parameter verification failed; 4. The size of specified eventType is greater than 255. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |

**Examples**

For details about how to initialize  in the example, see deviceManager.createDeviceManager.

```TypeScript
import { BusinessError } from '@ohos.base';

try {
  dmInstance.off("serviceDie", () => {
    console.info("serviceDie off");
  });
} catch (err) {
  let e: BusinessError = err as BusinessError;
  console.error("serviceDie errCode:" + e.code + ",errMessage:" + e.message);
}
```

## on('uiStateChange')

```TypeScript
on(type: 'uiStateChange', callback: Callback<{ param: string }>): void
```

Subscribes to UI status changes.

**Since:** 9

**Deprecated since:** 11

**Substitutes:** [on](arkts-distributedservice-distributeddevicemanager-devicemanager-i-sys.md#onreplyresult)(type: 'replyResult', callback: Callback&lt;{ param: string; }&gt;)

**Required permissions:** ohos.permission.ACCESS_SERVICE_DM

**System capability:** SystemCapability.DistributedHardware.DeviceManager

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'uiStateChange' | Yes | Event type, which has a fixed value of **uiStateChange**. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;{ param: string }&gt; | Yes | Callback used to return the UI status. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter type; 3. Parameter verification failed; 4. The size of specified eventType is greater than 255. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |

**Examples**

For details about how to initialize  in the example, see deviceManager.createDeviceManager.

```TypeScript
import { BusinessError } from '@ohos.base';

class Data {
  param: string = "";
}

interface TmpStr {
  verifyFailed: boolean;
}

try {
  dmInstance.on('uiStateChange', (data: Data) => {
    console.info("uiStateChange executed, dialog closed" + JSON.stringify(data));
    let tmpStr: TmpStr = JSON.parse(data.param);
    let isShow = tmpStr.verifyFailed;
    console.info("uiStateChange executed, dialog closed" + isShow);
  });
} catch (err) {
  let e: BusinessError = err as BusinessError;
  console.error("uiStateChange errCode:" + e.code + ",errMessage:" + e.message);
}
```

## on('deviceStateChange')

```TypeScript
on(type: 'deviceStateChange', callback: Callback<{ action: DeviceStateChangeAction, device: DeviceInfo }>): void
```

Subscribes to changes in the device state.

**Since:** 7

**Deprecated since:** 11

**Substitutes:** [on](arkts-distributedservice-distributeddevicemanager-devicemanager-i.md#ondevicestatechange)(type: 'deviceStateChange', callback: Callback&lt;{ action: DeviceStateChange; device: DeviceBasicInfo; }&gt;)

**Required permissions:** ohos.permission.ACCESS_SERVICE_DM

**System capability:** SystemCapability.DistributedHardware.DeviceManager

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'deviceStateChange' | Yes | Event type. The value is **deviceStateChange**, which indicates a device state change event. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;{ action: DeviceStateChangeAction, device: DeviceInfo }&gt; | Yes | Callback used to return the device information and state. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter type; 3. Parameter verification failed; 4. The size of specified eventType is greater than 255. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |

**Examples**

For details about how to initialize  in the example, see deviceManager.createDeviceManager.

```TypeScript
import deviceManager from '@ohos.distributedHardware.deviceManager';
import { BusinessError } from '@ohos.base';

class Data {
  action: deviceManager.DeviceStateChangeAction = 0;
  device: deviceManager.DeviceInfo = {
    deviceId: "",
    deviceName: "",
    deviceType: 0,
    networkId: "",
    range: 0,
    authForm:0
  };
}

try {
  dmInstance.on('deviceStateChange', (data: Data) => {
    console.info("deviceStateChange on:" + JSON.stringify(data));
  });
} catch (err) {
  let e: BusinessError = err as BusinessError;
  console.error("deviceStateChange errCode:" + e.code + ",errMessage:" + e.message);
}
```

## on('deviceFound')

```TypeScript
on(type: 'deviceFound', callback: Callback<{ subscribeId: number, device: DeviceInfo }>): void
```

Subscribes to device discovery events.

**Since:** 7

**Deprecated since:** 11

**Substitutes:** [on](arkts-distributedservice-distributeddevicemanager-devicemanager-i.md#ondiscoversuccess)(type: 'discoverSuccess', callback: Callback&lt;{ device: DeviceBasicInfo; }&gt;)

**Required permissions:** ohos.permission.ACCESS_SERVICE_DM

**System capability:** SystemCapability.DistributedHardware.DeviceManager

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'deviceFound' | Yes | Event type, which has a fixed value of **deviceFound**. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;{ subscribeId: number, device: DeviceInfo }&gt; | Yes | Callback used for device discovery. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter type; 3. Parameter verification failed; 4. The size of specified eventType is greater than 255. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |

**Examples**

For details about how to initialize  in the example, see deviceManager.createDeviceManager.

```TypeScript
import deviceManager from '@ohos.distributedHardware.deviceManager';
import { BusinessError } from '@ohos.base';

class Data {
  subscribeId: number = 0;
  device: deviceManager.DeviceInfo = {
    deviceId: "",
    deviceName: "",
    deviceType: 0,
    networkId: "",
    range: 0,
    authForm:0
  };
}

try {
  dmInstance.on('deviceFound', (data: Data) => {
    console.info("deviceFound:" + JSON.stringify(data));
  });
} catch (err) {
  let e: BusinessError = err as BusinessError;
  console.error("deviceFound errCode:" + e.code + ",errMessage:" + e.message);
}
```

## on('discoverFail')

```TypeScript
on(type: 'discoverFail', callback: Callback<{ subscribeId: number, reason: number }>): void
```

Subscribes to device discovery failures.

**Since:** 7

**Deprecated since:** 11

**Substitutes:** on(type: 'discoverFailure', callback: Callback&lt;{ reason: number; }&gt;)

**Required permissions:** ohos.permission.ACCESS_SERVICE_DM

**System capability:** SystemCapability.DistributedHardware.DeviceManager

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'discoverFail' | Yes | Event type, which has a fixed value of **discoverFail**. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;{ subscribeId: number, reason: number }&gt; | Yes | Callback used for the device discovery failure. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter type; 3. Parameter verification failed; 4. The size of specified eventType is greater than 255. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |

**Examples**

For details about how to initialize  in the example, see deviceManager.createDeviceManager.

```TypeScript
import { BusinessError } from '@ohos.base';

class Data {
  subscribeId: number = 0;
  reason: number = 0;
}

try {
  dmInstance.on('discoverFail', (data: Data) => {
    console.info("discoverFail on:" + JSON.stringify(data));
  });
} catch (err) {
  let e: BusinessError = err as BusinessError;
  console.error("discoverFail errCode:" + e.code + ",errMessage:" + e.message);
}
```

## on('publishSuccess')

```TypeScript
on(type: 'publishSuccess', callback: Callback<{ publishId: number }>): void
```

Subscribes to device information publication success events.

**Since:** 9

**Deprecated since:** 11

**Required permissions:** ohos.permission.ACCESS_SERVICE_DM

**System capability:** SystemCapability.DistributedHardware.DeviceManager

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'publishSuccess' | Yes | Event type, which has a fixed value of **publishSuccess**. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;{ publishId: number }&gt; | Yes | Callback used to return the publish ID. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter type; 3. Parameter verification failed; 4. The size of specified eventType is greater than 255. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |

**Examples**

For details about how to initialize  in the example, see deviceManager.createDeviceManager.

```TypeScript
import { BusinessError } from '@ohos.base';

class Data {
  publishId: number = 0;
}

try {
  dmInstance.on('publishSuccess', (data: Data) => {
    console.info("publishSuccess:" + JSON.stringify(data));
  });
} catch (err) {
  let e: BusinessError = err as BusinessError;
  console.error("publishSuccess errCode:" + e.code + ",errMessage:" + e.message);
}
```

## on('publishFail')

```TypeScript
on(type: 'publishFail', callback: Callback<{ publishId: number, reason: number }>): void
```

Subscribes to device information publication failures.

**Since:** 9

**Deprecated since:** 11

**Required permissions:** ohos.permission.ACCESS_SERVICE_DM

**System capability:** SystemCapability.DistributedHardware.DeviceManager

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'publishFail' | Yes | Event type, which has a fixed value of **publishFail**. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;{ publishId: number, reason: number }&gt; | Yes | Callback used for the publication failure. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter type; 3. Parameter verification failed; 4. The size of specified eventType is greater than 255. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |

**Examples**

For details about how to initialize  in the example, see deviceManager.createDeviceManager.

```TypeScript
import { BusinessError } from '@ohos.base';

class Data {
  publishId: number = 0;
  reason: number = 0;
}

try {
  dmInstance.on('publishFail', (data: Data) => {
    console.info("publishFail on:" + JSON.stringify(data));
  });
} catch (err) {
  let e: BusinessError = err as BusinessError;
  console.error("publishFail errCode:" + e.code + ",errMessage:" + e.message);
}
```

## on('serviceDie')

```TypeScript
on(type: 'serviceDie', callback: () => void): void
```

Subscribes to dead events of the **DeviceManager** service.

**Since:** 7

**Deprecated since:** 11

**Substitutes:** on(type: 'serviceDie', callback?: Callback&lt;{}&gt;)

**Required permissions:** ohos.permission.ACCESS_SERVICE_DM

**System capability:** SystemCapability.DistributedHardware.DeviceManager

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'serviceDie' | Yes | Event type, which has a fixed value of **serviceDie**. |
| callback | () =&gt; void | Yes | Callback invoked when a dead event of the **DeviceManager** service occurs. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter type; 3. Parameter verification failed; 4. The size of specified eventType is greater than 255. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |

**Examples**

For details about how to initialize  in the example, see deviceManager.createDeviceManager.

```TypeScript
import { BusinessError } from '@ohos.base';

try {
  dmInstance.on("serviceDie", () => {
    console.info("serviceDie on");
  });
} catch (err) {
  let e: BusinessError = err as BusinessError;
  console.error("serviceDie errCode:" + e.code + ",errMessage:" + e.message);
}
```

## publishDeviceDiscovery

```TypeScript
publishDeviceDiscovery(publishInfo: PublishInfo): void
```

Publishes device information for discovery purposes. The publish process lasts 2 minutes.

**Since:** 9

**Deprecated since:** 11

**Required permissions:** ohos.permission.ACCESS_SERVICE_DM

**System capability:** SystemCapability.DistributedHardware.DeviceManager

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| publishInfo | [PublishInfo](arkts-distributedservice-devicemanager-publishinfo-i-sys.md) | Yes | Device information to publish. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter type; 3. Parameter verification failed. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [11600105](../errorcode-device-manager.md#11600105-publish-unavailable) | Publish unavailable. |
| [11600101](../errorcode-device-manager.md#11600101-service-invoking-exception) | Failed to execute the function. |

**Examples**

For details about how to initialize  in the example, see deviceManager.createDeviceManager.

```TypeScript
import { BusinessError } from '@ohos.base';

interface PublishInfo {
  publishId: number;
  mode: number, // Active discovery
  freq: number,    // High frequency
  ranging: boolean // Whether the device supports reporting the distance to the discovery initiator.
};

// Automatically generate a unique subscription ID.
let publishId = Math.floor(Math.random() * 10000 + 1000);
let publishInfo: PublishInfo = {
  publishId: publishId,
  mode: 0xAA, // Active discovery
  freq: 2,    // High frequency
  ranging: true  // The device supports reporting the distance to the discovery initiator.
};

try {
  dmInstance.publishDeviceDiscovery(publishInfo); // A callback is invoked to notify the application when the device information is published.
} catch (err) {
  let e: BusinessError = err as BusinessError;
  console.error("publishDeviceDiscovery errCode:" + e.code + ",errMessage:" + e.message);
}
```

## release

```TypeScript
release(): void
```

Releases this **DeviceManager** instance when it is no longer used.

**Since:** 7

**Deprecated since:** 11

**Substitutes:** [releaseDeviceManager](arkts-distributedservice-distributeddevicemanager-releasedevicemanager-f.md)

**Required permissions:** ohos.permission.ACCESS_SERVICE_DM

**System capability:** SystemCapability.DistributedHardware.DeviceManager

**System API:** This is a system API.

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [11600101](../errorcode-device-manager.md#11600101-service-invoking-exception) | Failed to execute the function. |

**Examples**

For details about how to initialize  in the example, see deviceManager.createDeviceManager.

```TypeScript
import { BusinessError } from '@ohos.base';

try {
  dmInstance.release();
} catch (err) {
  let e: BusinessError = err as BusinessError;
  console.error("release errCode:" + e.code + ",errMessage:" + e.message);
}
```

## requestCredentialRegisterInfo

```TypeScript
requestCredentialRegisterInfo(requestInfo: string, callback: AsyncCallback<{ registerInfo: string }>): void
```

Obtains the registration information of the credential.

**Since:** 10

**Deprecated since:** 11

**Required permissions:** ohos.permission.ACCESS_SERVICE_DM

**System capability:** SystemCapability.DistributedHardware.DeviceManager

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| requestInfo | string | Yes | Request credential information. The value contains a maximum of 255 characters. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;{ registerInfo: string }&gt; | Yes | Callback used to return the credential registration information. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter type; 3. Parameter verification failed; 4. The size of specified requestInfo is greater than 255. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |

**Examples**

For details about how to initialize  in the example, see deviceManager.createDeviceManager.

```TypeScript
import { BusinessError } from '@ohos.base';

interface CredentialInfo {
  version: string;
  userId: string;
}

class Data {
  registerInfo: string = "";
}

let credentialInfo: CredentialInfo = {
  version: "1.2.3",
  userId: "123"
};
try {
  let jsonCredentialInfo = JSON.stringify(credentialInfo);
  dmInstance.requestCredentialRegisterInfo(jsonCredentialInfo, (err: BusinessError, data: Data) => {
    if (data) {
      console.info("requestCredentialRegisterInfo result:" + JSON.stringify(data));
    } else {
      console.info("requestCredentialRegisterInfo result: data is null");
    }
  });
} catch (err) {
  let e: BusinessError = err as BusinessError;
  console.error("requestCredentialRegisterInfo err:" + e.code + "," + e.message);
}
```

## setUserOperation

```TypeScript
setUserOperation(operateAction: number, params: string): void
```

Sets a user operation.

**Since:** 9

**Deprecated since:** 11

**Substitutes:** [replyUiAction](arkts-distributedservice-distributeddevicemanager-devicemanager-i-sys.md#replyuiaction)

**Required permissions:** ohos.permission.ACCESS_SERVICE_DM

**System capability:** SystemCapability.DistributedHardware.DeviceManager

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| operateAction | number | Yes | User operation. The value ranges from 0 to 5. |
| params | string | Yes | Input parameters of the user. The value is a string of 1 to 255 characters. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter type; 3. Parameter verification failed; 4. The size of specified params is greater than 255. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |

**Examples**

For details about how to initialize  in the example, see deviceManager.createDeviceManager.

```TypeScript
import { BusinessError } from '@ohos.base';

try {
  /*
    operateAction = 0 - Grant the permission.
    operateAction = 1 - Revoke the permission.
    operateAction = 2 - The user operation in the permission request dialog box times out.
    operateAction = 3 - Cancel the display of the PIN box.
    operateAction = 4 - Cancel the display of the PIN input box.
    operateAction = 5 - Confirm the input in the PIN input box.
  */
  let operation = 0;
  dmInstance.setUserOperation(operation, "extra");
} catch (err) {
  let e: BusinessError = err as BusinessError;
  console.error("setUserOperation errCode:" + e.code + ",errMessage:" + e.message);
}
```

## startDeviceDiscovery

```TypeScript
startDeviceDiscovery(subscribeInfo: SubscribeInfo): void
```

Starts to discover peripheral devices. The discovery process lasts 2 minutes. A maximum of 99 devices can be discovered.

**Since:** 8

**Deprecated since:** 11

**Substitutes:** [startDiscovering](arkts-distributedservice-distributeddevicemanager-devicemanager-i.md#startdiscovering)(discoverParam: { [key: string]: Object; }, filterOptions?: { [key: string]: Object; })

**Required permissions:** ohos.permission.ACCESS_SERVICE_DM

**System capability:** SystemCapability.DistributedHardware.DeviceManager

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| subscribeInfo | [SubscribeInfo](arkts-distributedservice-devicemanager-subscribeinfo-i-sys.md) | Yes | Subscription information. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter type; 3. Parameter verification failed; 4. The size of specified param is greater than 255. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [11600104](../errorcode-device-manager.md#11600104-discovery-unavailable) | Discovery unavailable. |
| [11600101](../errorcode-device-manager.md#11600101-service-invoking-exception) | Failed to execute the function. |

**Examples**

For details about how to initialize  in the example, see deviceManager.createDeviceManager.

```TypeScript
import { BusinessError } from '@ohos.base';

interface SubscribeInfo {
  subscribeId: number;
  mode: number, // Active discovery
  medium: number,  // Automatic. Multiple media can be used for device discovery.
  freq: number,    // High frequency
  isSameAccount: boolean;
  isWakeRemote: boolean;
  capability: number;
}

// Automatically generate a unique subscription ID.
let subscribeId = Math.floor(Math.random() * 10000 + 1000);
let subscribeInfo: SubscribeInfo = {
  subscribeId: subscribeId,
  mode: 0xAA, // Active discovery
  medium: 0,  // Automatic. Multiple media can be used for device discovery.
  freq: 2,    // High frequency
  isSameAccount: false,
  isWakeRemote: false,
  capability: 1
};
try {
  dmInstance.startDeviceDiscovery(subscribeInfo); // The deviceFound callback is called to notify the application when a device is discovered.
} catch (err) {
  let e: BusinessError = err as BusinessError;
  console.error("startDeviceDiscovery errCode:" + e.code + ",errMessage:" + e.message);
}
```

<a id="startdevicediscovery-1"></a>

## startDeviceDiscovery

```TypeScript
startDeviceDiscovery(subscribeInfo: SubscribeInfo, filterOptions?: string): void
```

Starts to discover peripheral devices. The discovery process lasts 2 minutes. A maximum of 99 devices can be discovered.

**Since:** 9

**Deprecated since:** 11

**Substitutes:** [startDiscovering](arkts-distributedservice-distributeddevicemanager-devicemanager-i.md#startdiscovering)(discoverParam: { [key: string]: Object; }, filterOptions?: { [key: string]: Object; })

**Required permissions:** ohos.permission.ACCESS_SERVICE_DM

**System capability:** SystemCapability.DistributedHardware.DeviceManager

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| subscribeInfo | [SubscribeInfo](arkts-distributedservice-devicemanager-subscribeinfo-i-sys.md) | Yes | Subscription information. |
| filterOptions | string | No | Options for filtering discovered devices. Optional. The default value is **undefined**, indicating that discovery of offline devices. The value is a string of 1 to 255 characters. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter type; 3. Parameter verification failed; 4. The size of specified param is greater than 255. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [11600104](../errorcode-device-manager.md#11600104-discovery-unavailable) | Discovery unavailable. |
| [11600101](../errorcode-device-manager.md#11600101-service-invoking-exception) | Failed to execute the function. |

**Examples**

For details about how to initialize  in the example, see deviceManager.createDeviceManager.

```TypeScript
import { BusinessError } from '@ohos.base';

interface Filters {
  type: string;
  value: number;
}

interface FilterOptions {
  filter_op: string, // Optional. The default value is OR.
  filters: Filters[];
}

interface SubscribeInfo {
  subscribeId: number;
  mode: number, // Active discovery
  medium: number,  // Automatic. Multiple media can be used for device discovery.
  freq: number,    // High frequency
  isSameAccount: boolean;
  isWakeRemote: boolean;
  capability: number;
}

// Automatically generate a unique subscription ID.
let subscribeId = Math.floor(Math.random() * 10000 + 1000);
let subscribeInfo: SubscribeInfo = {
  subscribeId: subscribeId,
  mode: 0xAA, // Active discovery
  medium: 0,  // Automatic. Multiple media can be used for device discovery.
  freq: 2,    // High frequency
  isSameAccount: false,
  isWakeRemote: false,
  capability: 1
};

let filters: Filters[] = [
  {
      type: "range",
      value: 50 // Filter discovered devices based on the distance (in cm).
  }
];

let filterOptions: FilterOptions = {
  filter_op: "OR", // Optional. The default value is OR.
  filters: filters
};
try {
  dmInstance.startDeviceDiscovery(subscribeInfo, JSON.stringify(filterOptions)); // The deviceFound callback is invoked to notify the application when a device is discovered.
} catch (err) {
  let e: BusinessError = err as BusinessError;
  console.error("startDeviceDiscovery errCode:" + e.code + ",errMessage:" + e.message);
}
```

## stopDeviceDiscovery

```TypeScript
stopDeviceDiscovery(subscribeId: number): void
```

Stops device discovery.

**Since:** 7

**Deprecated since:** 11

**Substitutes:** [stopDiscovering](arkts-distributedservice-distributeddevicemanager-devicemanager-i.md#stopdiscovering)

**Required permissions:** ohos.permission.ACCESS_SERVICE_DM

**System capability:** SystemCapability.DistributedHardware.DeviceManager

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| subscribeId | number | Yes | Subscription ID. The value ranges from 1 to 65535. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter type; 3. Parameter verification failed; 4. The size of specified param is greater than 255. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [11600101](../errorcode-device-manager.md#11600101-service-invoking-exception) | Failed to execute the function. |

**Examples**

For details about how to initialize  in the example, see deviceManager.createDeviceManager.

```TypeScript
import { BusinessError } from '@ohos.base';

try {
  // stopDeviceDiscovery and startDeviceDiscovery must be used in pairs, and the input parameter **subscribeId** passed in them must be the same.
  let subscribeId = 12345;
  dmInstance.stopDeviceDiscovery(subscribeId);
} catch (err) {
  let e: BusinessError = err as BusinessError;
  console.error("stopDeviceDiscovery errCode:" + e.code + ",errMessage:" + e.message);
}
```

## unAuthenticateDevice

```TypeScript
unAuthenticateDevice(deviceInfo: DeviceInfo): void
```

Deauthenticates a device.

**Since:** 8

**Deprecated since:** 11

**Substitutes:** [unbindTarget](arkts-distributedservice-distributeddevicemanager-devicemanager-i.md#unbindtarget)

**Required permissions:** ohos.permission.ACCESS_SERVICE_DM

**System capability:** SystemCapability.DistributedHardware.DeviceManager

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| deviceInfo | [DeviceInfo](arkts-distributedservice-devicemanager-deviceinfo-i-sys.md) | Yes | Device information. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter type; 3. Parameter verification failed. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [11600101](../errorcode-device-manager.md#11600101-service-invoking-exception) | Failed to execute the function. |

**Examples**

For details about how to initialize  in the example, see deviceManager.createDeviceManager.

```TypeScript
import { BusinessError } from '@ohos.base';

interface DeviceInfo {
  deviceId: string;
  deviceName: string;
  deviceType: number;
  networkId: string;
  range: number;
}

try {
  let deviceInfo: deviceManager.DeviceInfo = {
    deviceId: "XXXXXXXX",
    deviceName: "",
    deviceType: 0x0E,
    networkId: "xxxxxxx",
    range: 0,
    authForm: 0
  };
  dmInstance.unAuthenticateDevice(deviceInfo);
} catch (err) {
  let e: BusinessError = err as BusinessError;
  console.error("unAuthenticateDevice errCode:" + e.code + ",errMessage:" + e.message);
}
```

## unPublishDeviceDiscovery

```TypeScript
unPublishDeviceDiscovery(publishId: number): void
```

Stops publishing device information.

**Since:** 9

**Deprecated since:** 11

**Required permissions:** ohos.permission.ACCESS_SERVICE_DM

**System capability:** SystemCapability.DistributedHardware.DeviceManager

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| publishId | number | Yes | Publish ID. The value ranges from 1 to 2147483647. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter type; 3. Parameter verification failed. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [11600101](../errorcode-device-manager.md#11600101-service-invoking-exception) | Failed to execute the function. |

**Examples**

For details about how to initialize  in the example, see deviceManager.createDeviceManager.

```TypeScript
import { BusinessError } from '@ohos.base';

try {
  // unPublishDeviceDiscovery and publishDeviceDiscovery must be used in pairs, and the input parameter **publishId** passed in them must be the same.
  let publishId = 12345;
  dmInstance.unPublishDeviceDiscovery(publishId);
} catch (err) {
  let e: BusinessError = err as BusinessError;
  console.error("unPublishDeviceDiscovery errCode:" + e.code + ",errMessage:" + e.message);
}
```

## verifyAuthInfo

```TypeScript
verifyAuthInfo(authInfo: AuthInfo, callback: AsyncCallback<{ deviceId: string, level: number }>): void
```

Verifies authentication information.

**Since:** 7

**Deprecated since:** 11

**Required permissions:** ohos.permission.ACCESS_SERVICE_DM

**System capability:** SystemCapability.DistributedHardware.DeviceManager

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| authInfo | [AuthInfo](arkts-distributedservice-devicemanager-authinfo-i-sys.md) | Yes | Authentication information. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;{ deviceId: string, level: number }&gt; | Yes | Callback used to return the verification result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter type; 3. Parameter verification failed. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |

**Examples**

For details about how to initialize  in the example, see deviceManager.createDeviceManager.

```TypeScript
import { BusinessError } from '@ohos.base';

interface ExtraInfo {
  authType: number;
  token: number;
}

interface AuthInfo {
  authType: number;
  token: number;
  extraInfo: ExtraInfo;
}

class Data {
  deviceId: string = "";
  level: number = 0;
}

let extraInfo: ExtraInfo = {
  authType: 0,
  token: 0
};

let authInfo: AuthInfo = {
  authType: 1,
  token: 123456,
  extraInfo: extraInfo
};
try {
  dmInstance.verifyAuthInfo(authInfo, (err: BusinessError, data: Data) => {
    if (err) {
      console.error("verifyAuthInfo errCode:" + err.code + ",errMessage:" + err.message);
      return;
    }
  console.info("verifyAuthInfo result:" + JSON.stringify(data));
  });
} catch (err) {
  let e: BusinessError = err as BusinessError;
  console.error("verifyAuthInfo errCode:" + e.code + ",errMessage:" + e.message);
}
```
