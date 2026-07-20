# DeviceManager

设备管理实例，用于获取可信设备和本地设备的相关信息。在调用DeviceManager的方法前，需要先通过createDeviceManager构建一个DeviceManager实例dmInstance。

**起始版本：** 7

**废弃版本：** 11

**替代接口：** [DeviceManager](arkts-distributedservice-distributeddevicemanager-devicemanager-i.md)

<!--Device-deviceManager-interface DeviceManager--><!--Device-deviceManager-interface DeviceManager-End-->

**系统能力：** SystemCapability.DistributedHardware.DeviceManager

## 导入模块

```TypeScript
import { deviceManager } from '@kit.DistributedServiceKit';
```

<a id="authenticatedevice"></a>
## authenticateDevice

```TypeScript
authenticateDevice(
      deviceInfo: DeviceInfo,
      authParam: AuthParam,
      callback: AsyncCallback<{ deviceId: string, pinToken?: number }>
    ): void
```

认证设备。

**起始版本：** 7

**废弃版本：** 11

**替代接口：** [bindTarget(deviceId:](arkts-distributedservice-distributeddevicemanager-devicemanager-i.md#bindtarget-1)

**需要权限：** ohos.permission.ACCESS_SERVICE_DM

<!--Device-DeviceManager-authenticateDevice(
      deviceInfo: DeviceInfo,
      authParam: AuthParam,
      callback: AsyncCallback<{ deviceId: string, pinToken?: number }>
    ): void--><!--Device-DeviceManager-authenticateDevice(
      deviceInfo: DeviceInfo,
      authParam: AuthParam,
      callback: AsyncCallback<{ deviceId: string, pinToken?: number }>
    ): void-End-->

**系统能力：** SystemCapability.DistributedHardware.DeviceManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| deviceInfo | [DeviceInfo](../../apis-avsession-kit/arkts-apis/arkts-avsession-avsession-deviceinfo-i-sys.md) | 是 | 设备信息。 |
| authParam | [AuthParam](../../apis-user-authentication-kit/arkts-apis/arkts-userauthentication-userauth-authparam-i-sys.md) | 是 | 认证参数。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;{ deviceId: string, pinToken?: number }&gt; | 是 |  |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter type;3. Parameter verification failed. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |

**示例：**

示例中的初始化请参见[deviceManager.createDeviceManager](#devicemanagercreatedevicemanager)。

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
  authType: number; // 认证类型： 1 - 无账号PIN码认证
  extraInfo: ExtraInfo;
}

// 认证的设备信息，可以从发现的结果中获取
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
  authType: 1,// 认证类型： 1 - 无账号PIN码认证
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

<a id="deletecredential"></a>
## deleteCredential

```TypeScript
deleteCredential(queryInfo: string, callback: AsyncCallback<{ resultInfo: string }>): void
```

删除凭据信息。

**起始版本：** 10

**废弃版本：** 11

**需要权限：** ohos.permission.ACCESS_SERVICE_DM

<!--Device-DeviceManager-deleteCredential(queryInfo: string, callback: AsyncCallback<{ resultInfo: string }>): void--><!--Device-DeviceManager-deleteCredential(queryInfo: string, callback: AsyncCallback<{ resultInfo: string }>): void-End-->

**系统能力：** SystemCapability.DistributedHardware.DeviceManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| queryInfo | string | 是 | 删除凭据信息。长度范围1~64000字符。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;{ resultInfo: string }&gt; | 是 |  |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter type;3. Parameter verification failed;4. The size of specified queryInfo is greater than 5999. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |

**示例：**

示例中的初始化请参见[deviceManager.createDeviceManager](#devicemanagercreatedevicemanager)。

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

<a id="getdeviceinfo"></a>
## getDeviceInfo

```TypeScript
getDeviceInfo(networkId: string, callback: AsyncCallback<DeviceInfo>): void
```

通过指定设备的网络标识获取该设备的信息。使用callback异步回调。

**起始版本：** 10

**废弃版本：** 11

**替代接口：** [getDeviceName](arkts-distributedservice-distributeddevicemanager-devicemanager-i.md#getdevicename-1)

**需要权限：** ohos.permission.ACCESS_SERVICE_DM

<!--Device-DeviceManager-getDeviceInfo(networkId: string, callback: AsyncCallback<DeviceInfo>): void--><!--Device-DeviceManager-getDeviceInfo(networkId: string, callback: AsyncCallback<DeviceInfo>): void-End-->

**系统能力：** SystemCapability.DistributedHardware.DeviceManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| networkId | string | 是 | 设备的网络标识。长度范围1~255字符。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;DeviceInfo&gt; | 是 | 获取指定设备信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter type;3. Parameter verification failed;4. The size of specified networkId is greater than 255. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |

**示例：**

示例中的初始化请参见[deviceManager.createDeviceManager](#devicemanagercreatedevicemanager)。

```TypeScript
import deviceManager from '@ohos.distributedHardware.deviceManager';
import { BusinessError } from '@ohos.base';

try {
  // 设备网络标识，可以从可信设备列表中获取
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

通过指定设备的网络标识获取该设备的信息。使用Promise异步回调。

**起始版本：** 10

**废弃版本：** 11

**替代接口：** [getDeviceName](arkts-distributedservice-distributeddevicemanager-devicemanager-i.md#getdevicename-1)

**需要权限：** ohos.permission.ACCESS_SERVICE_DM

<!--Device-DeviceManager-getDeviceInfo(networkId: string): Promise<DeviceInfo>--><!--Device-DeviceManager-getDeviceInfo(networkId: string): Promise<DeviceInfo>-End-->

**系统能力：** SystemCapability.DistributedHardware.DeviceManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| networkId | string | 是 | 设备的网络标识。长度范围1~255字符。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;DeviceInfo&gt; | Promise实例，用于获取异步返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter type;3. Parameter verification failed;4. The size of specified networkId is greater than 255. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |

**示例：**

示例中的初始化请参见[deviceManager.createDeviceManager](#devicemanagercreatedevicemanager)。

```TypeScript
import deviceManager from '@ohos.distributedHardware.deviceManager';
import { BusinessError } from '@ohos.base';

// 设备网络标识，可以从可信设备列表中获取
let networkId = "xxxxxxx";
dmInstance.getDeviceInfo(networkId).then((data: deviceManager.DeviceInfo) => {
  console.info('get device info: ' + JSON.stringify(data));
}).catch((err: BusinessError) => {
  console.error("getDeviceInfo errCode:" + err.code + ",errMessage:" + err.message);
});

```

<a id="getlocaldeviceinfo"></a>
## getLocalDeviceInfo

```TypeScript
getLocalDeviceInfo(callback: AsyncCallback<DeviceInfo>): void
```

获取本地设备信息。使用callback异步回调。

**起始版本：** 8

**废弃版本：** 11

**替代接口：** [getLocalDeviceNetworkId](arkts-distributedservice-distributeddevicemanager-devicemanager-i.md#getlocaldevicenetworkid-1)

**需要权限：** ohos.permission.ACCESS_SERVICE_DM

<!--Device-DeviceManager-getLocalDeviceInfo(callback: AsyncCallback<DeviceInfo>): void--><!--Device-DeviceManager-getLocalDeviceInfo(callback: AsyncCallback<DeviceInfo>): void-End-->

**系统能力：** SystemCapability.DistributedHardware.DeviceManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;DeviceInfo&gt; | 是 | 获取本地设备信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter type;3. Parameter verification failed. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |

**示例：**

示例中的初始化请参见[deviceManager.createDeviceManager](#devicemanagercreatedevicemanager)。

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

获取本地设备信息。使用Promise异步回调。

**起始版本：** 8

**废弃版本：** 11

**替代接口：** [getLocalDeviceNetworkId](arkts-distributedservice-distributeddevicemanager-devicemanager-i.md#getlocaldevicenetworkid-1)

**需要权限：** ohos.permission.ACCESS_SERVICE_DM

<!--Device-DeviceManager-getLocalDeviceInfo(): Promise<DeviceInfo>--><!--Device-DeviceManager-getLocalDeviceInfo(): Promise<DeviceInfo>-End-->

**系统能力：** SystemCapability.DistributedHardware.DeviceManager

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;DeviceInfo&gt; | Promise实例，用于获取异步返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |

**示例：**

示例中的初始化请参见[deviceManager.createDeviceManager](#devicemanagercreatedevicemanager)。

```TypeScript
import deviceManager from '@ohos.distributedHardware.deviceManager';
import { BusinessError } from '@ohos.base';

dmInstance.getLocalDeviceInfo().then((data: deviceManager.DeviceInfo) => {
  console.info('get local device info: ' + JSON.stringify(data));
}).catch((err: BusinessError) => {
  console.error("getLocalDeviceInfo errCode:" + err.code + ",errMessage:" + err.message);
});

```

<a id="getlocaldeviceinfosync"></a>
## getLocalDeviceInfoSync

```TypeScript
getLocalDeviceInfoSync(): DeviceInfo
```

同步获取本地设备信息。

**起始版本：** 8

**废弃版本：** 11

**替代接口：** [getLocalDeviceNetworkId](arkts-distributedservice-distributeddevicemanager-devicemanager-i.md#getlocaldevicenetworkid-1)

**需要权限：** ohos.permission.ACCESS_SERVICE_DM

<!--Device-DeviceManager-getLocalDeviceInfoSync(): DeviceInfo--><!--Device-DeviceManager-getLocalDeviceInfoSync(): DeviceInfo-End-->

**系统能力：** SystemCapability.DistributedHardware.DeviceManager

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [DeviceInfo](../../apis-avsession-kit/arkts-apis/arkts-avsession-avsession-deviceinfo-i-sys.md) | 返回本地设备列表。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [11600101](../../apis-distributedservice-kit/errorcode-device-manager.md#11600101-服务调用异常) | Failed to execute the function. |

**示例：**

示例中的初始化请参见[deviceManager.createDeviceManager](#devicemanagercreatedevicemanager)。

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

<a id="gettrusteddevicelist"></a>
## getTrustedDeviceList

```TypeScript
getTrustedDeviceList(callback: AsyncCallback<Array<DeviceInfo>>): void
```

获取所有可信设备列表。使用callback异步回调。

**起始版本：** 8

**废弃版本：** 11

**替代接口：** [getAvailableDeviceList(callback:](arkts-distributedservice-distributeddevicemanager-devicemanager-i.md#getavailabledevicelist-1)

**需要权限：** ohos.permission.ACCESS_SERVICE_DM

<!--Device-DeviceManager-getTrustedDeviceList(callback: AsyncCallback<Array<DeviceInfo>>): void--><!--Device-DeviceManager-getTrustedDeviceList(callback: AsyncCallback<Array<DeviceInfo>>): void-End-->

**系统能力：** SystemCapability.DistributedHardware.DeviceManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;Array&lt;DeviceInfo&gt;&gt; | 是 | 获取所有可信设备列表的回调，返回设备信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter type;3. Parameter verification failed. |

**示例：**

示例中的初始化请参见[deviceManager.createDeviceManager](#devicemanagercreatedevicemanager)。

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

获取所有可信设备列表。使用Promise异步回调。

**起始版本：** 8

**废弃版本：** 11

**替代接口：** [getAvailableDeviceList()](arkts-distributedservice-distributeddevicemanager-devicemanager-i.md#getavailabledevicelist-1)

**需要权限：** ohos.permission.ACCESS_SERVICE_DM

<!--Device-DeviceManager-getTrustedDeviceList(): Promise<Array<DeviceInfo>>--><!--Device-DeviceManager-getTrustedDeviceList(): Promise<Array<DeviceInfo>>-End-->

**系统能力：** SystemCapability.DistributedHardware.DeviceManager

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;DeviceInfo&gt;&gt; | Promise实例，用于获取异步返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |

**示例：**

示例中的初始化请参见[deviceManager.createDeviceManager](#devicemanagercreatedevicemanager)。

```TypeScript
import deviceManager from '@ohos.distributedHardware.deviceManager';
import { BusinessError } from '@ohos.base';

dmInstance.getTrustedDeviceList().then((data: Array<deviceManager.DeviceInfo>) => {
  console.info('get trusted device info: ' + JSON.stringify(data));
  }).catch((err: BusinessError) => {
    console.error("getTrustedDeviceList errCode:" + err.code + ",errMessage:" + err.message);
});

```

<a id="gettrusteddevicelistsync"></a>
## getTrustedDeviceListSync

```TypeScript
getTrustedDeviceListSync(): Array<DeviceInfo>
```

同步获取所有可信设备列表。

**起始版本：** 7

**废弃版本：** 11

**替代接口：** [getAvailableDeviceListSync](arkts-distributedservice-distributeddevicemanager-devicemanager-i.md#getavailabledevicelistsync-1)

**需要权限：** ohos.permission.ACCESS_SERVICE_DM

<!--Device-DeviceManager-getTrustedDeviceListSync(): Array<DeviceInfo>--><!--Device-DeviceManager-getTrustedDeviceListSync(): Array<DeviceInfo>-End-->

**系统能力：** SystemCapability.DistributedHardware.DeviceManager

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;DeviceInfo&gt; | 返回可信设备列表。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [11600101](../../apis-distributedservice-kit/errorcode-device-manager.md#11600101-服务调用异常) | Failed to execute the function. |

**示例：**

示例中的初始化请参见[deviceManager.createDeviceManager](#devicemanagercreatedevicemanager)。

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

打开软总线系统端的心跳模式，让周围处于下线状态的可信设备快速上线，同时刷新已上线的可信设备列表。

**起始版本：** 10

**废弃版本：** 11

**需要权限：** ohos.permission.ACCESS_SERVICE_DM

<!--Device-DeviceManager-getTrustedDeviceListSync(isRefresh: boolean): Array<DeviceInfo>--><!--Device-DeviceManager-getTrustedDeviceListSync(isRefresh: boolean): Array<DeviceInfo>-End-->

**系统能力：** SystemCapability.DistributedHardware.DeviceManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| isRefresh | boolean | 是 | 是否打开心跳模式，刷新可信列表，true表示打开心跳模式，false表示关闭心跳模式。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;DeviceInfo&gt; | 返回可信设备列表。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter type;3. Parameter verification failed. |
| [11600101](../../apis-distributedservice-kit/errorcode-device-manager.md#11600101-服务调用异常) | Failed to execute the function. |

**示例：**

示例中的初始化请参见[deviceManager.createDeviceManager](#devicemanagercreatedevicemanager)。

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

<a id="importcredential"></a>
## importCredential

```TypeScript
importCredential(credentialInfo: string, callback: AsyncCallback<{ resultInfo: string }>): void
```

导入凭据信息。

**起始版本：** 10

**废弃版本：** 11

**需要权限：** ohos.permission.ACCESS_SERVICE_DM

<!--Device-DeviceManager-importCredential(credentialInfo: string, callback: AsyncCallback<{ resultInfo: string }>): void--><!--Device-DeviceManager-importCredential(credentialInfo: string, callback: AsyncCallback<{ resultInfo: string }>): void-End-->

**系统能力：** SystemCapability.DistributedHardware.DeviceManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| credentialInfo | string | 是 | 导入凭据信息。长度范围1~64000字符。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;{ resultInfo: string }&gt; | 是 |  |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter type;3. Parameter verification failed;4. The size of specified credentialInfo is greater than 5999. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |

**示例：**

示例中的初始化请参见[deviceManager.createDeviceManager](#devicemanagercreatedevicemanager)。

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

<a id="off"></a>
## off('uiStateChange')

```TypeScript
off(type: 'uiStateChange', callback?: Callback<{ param: string }>): void
```

取消ui状态变更回调。

**起始版本：** 9

**废弃版本：** 11

**替代接口：** off(type:

**需要权限：** ohos.permission.ACCESS_SERVICE_DM

<!--Device-DeviceManager-off(type: 'uiStateChange', callback?: Callback<{ param: string }>): void--><!--Device-DeviceManager-off(type: 'uiStateChange', callback?: Callback<{ param: string }>): void-End-->

**系统能力：** SystemCapability.DistributedHardware.DeviceManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'uiStateChange' | 是 | 取消注册的设备管理器 ui 状态回调，固定为uiStateChange。 |
| callback | [Callback](../../apis-arkui/arkts-components/arkts-arkui-callback-i.md)&lt;{ param: string }&gt; | 否 |  |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter type;3. Parameter verification failed;4. The size of specified eventType is greater than 255. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |

**示例：**

示例中的初始化请参见[deviceManager.createDeviceManager](#devicemanagercreatedevicemanager)。

```TypeScript
import { BusinessError } from '@ohos.base';

try {
  dmInstance.off('uiStateChange');
} catch (err) {
  let e: BusinessError = err as BusinessError;
  console.error("uiStateChange errCode:" + e.code + ",errMessage:" + e.message);
}

```

<a id="off-1"></a>
## off('deviceStateChange')

```TypeScript
off(type: 'deviceStateChange', callback?: Callback<{ action: DeviceStateChangeAction, device: DeviceInfo }>): void
```

取消注册设备状态回调。

**起始版本：** 7

**废弃版本：** 11

**替代接口：** off(type:

**需要权限：** ohos.permission.ACCESS_SERVICE_DM

<!--Device-DeviceManager-off(type: 'deviceStateChange', callback?: Callback<{ action: DeviceStateChangeAction, device: DeviceInfo }>): void--><!--Device-DeviceManager-off(type: 'deviceStateChange', callback?: Callback<{ action: DeviceStateChangeAction, device: DeviceInfo }>): void-End-->

**系统能力：** SystemCapability.DistributedHardware.DeviceManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'deviceStateChange' | 是 | 根据应用程序的包名取消注册设备状态回调，固定为deviceStateChange。 |
| callback | [Callback](../../apis-arkui/arkts-components/arkts-arkui-callback-i.md)&lt;{ action: DeviceStateChangeAction, device: DeviceInfo }&gt; | 否 |  |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter type;3. Parameter verification failed;4. The size of specified eventType is greater than 255. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |

**示例：**

示例中的初始化请参见[deviceManager.createDeviceManager](#devicemanagercreatedevicemanager)。

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

<a id="off-2"></a>
## off('deviceFound')

```TypeScript
off(type: 'deviceFound', callback?: Callback<{ subscribeId: number, device: DeviceInfo }>): void
```

取消注册设备发现回调。

**起始版本：** 7

**废弃版本：** 11

**替代接口：** off(type:

**需要权限：** ohos.permission.ACCESS_SERVICE_DM

<!--Device-DeviceManager-off(type: 'deviceFound', callback?: Callback<{ subscribeId: number, device: DeviceInfo }>): void--><!--Device-DeviceManager-off(type: 'deviceFound', callback?: Callback<{ subscribeId: number, device: DeviceInfo }>): void-End-->

**系统能力：** SystemCapability.DistributedHardware.DeviceManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'deviceFound' | 是 | 取消注册设备发现回调，固定为deviceFound。 |
| callback | [Callback](../../apis-arkui/arkts-components/arkts-arkui-callback-i.md)&lt;{ subscribeId: number, device: DeviceInfo }&gt; | 否 |  |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter type;3. Parameter verification failed;4. The size of specified eventType is greater than 255. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |

**示例：**

示例中的初始化请参见[deviceManager.createDeviceManager](#devicemanagercreatedevicemanager)。

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

<a id="off-3"></a>
## off('discoverFail')

```TypeScript
off(type: 'discoverFail', callback?: Callback<{ subscribeId: number, reason: number }>): void
```

取消注册设备发现失败回调。

**起始版本：** 7

**废弃版本：** 11

**替代接口：** off(type:

**需要权限：** ohos.permission.ACCESS_SERVICE_DM

<!--Device-DeviceManager-off(type: 'discoverFail', callback?: Callback<{ subscribeId: number, reason: number }>): void--><!--Device-DeviceManager-off(type: 'discoverFail', callback?: Callback<{ subscribeId: number, reason: number }>): void-End-->

**系统能力：** SystemCapability.DistributedHardware.DeviceManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'discoverFail' | 是 | 取消注册设备发现失败回调，固定为discoverFail。 |
| callback | [Callback](../../apis-arkui/arkts-components/arkts-arkui-callback-i.md)&lt;{ subscribeId: number, reason: number }&gt; | 否 |  |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter type;3. Parameter verification failed;4. The size of specified eventType is greater than 255. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |

**示例：**

示例中的初始化请参见[deviceManager.createDeviceManager](#devicemanagercreatedevicemanager)。

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

<a id="off-4"></a>
## off('publishSuccess')

```TypeScript
off(type: 'publishSuccess', callback?: Callback<{ publishId: number }>): void
```

取消注册设备发布成功回调。

**起始版本：** 9

**废弃版本：** 11

**需要权限：** ohos.permission.ACCESS_SERVICE_DM

<!--Device-DeviceManager-off(type: 'publishSuccess', callback?: Callback<{ publishId: number }>): void--><!--Device-DeviceManager-off(type: 'publishSuccess', callback?: Callback<{ publishId: number }>): void-End-->

**系统能力：** SystemCapability.DistributedHardware.DeviceManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'publishSuccess' | 是 | 取消注册设备发布成功回调，固定为publishSuccess。 |
| callback | [Callback](../../apis-arkui/arkts-components/arkts-arkui-callback-i.md)&lt;{ publishId: number }&gt; | 否 |  |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter type;3. Parameter verification failed;4. The size of specified eventType is greater than 255. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |

**示例：**

示例中的初始化请参见[deviceManager.createDeviceManager](#devicemanagercreatedevicemanager)。

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

<a id="off-5"></a>
## off('publishFail')

```TypeScript
off(type: 'publishFail', callback?: Callback<{ publishId: number, reason: number }>): void
```

取消注册设备发布失败回调。

**起始版本：** 9

**废弃版本：** 11

**需要权限：** ohos.permission.ACCESS_SERVICE_DM

<!--Device-DeviceManager-off(type: 'publishFail', callback?: Callback<{ publishId: number, reason: number }>): void--><!--Device-DeviceManager-off(type: 'publishFail', callback?: Callback<{ publishId: number, reason: number }>): void-End-->

**系统能力：** SystemCapability.DistributedHardware.DeviceManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'publishFail' | 是 | 取消注册设备发布失败回调，固定为publishFail。 |
| callback | [Callback](../../apis-arkui/arkts-components/arkts-arkui-callback-i.md)&lt;{ publishId: number, reason: number }&gt; | 否 |  |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter type;3. Parameter verification failed;4. The size of specified eventType is greater than 255. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |

**示例：**

示例中的初始化请参见[deviceManager.createDeviceManager](#devicemanagercreatedevicemanager)。

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

<a id="off-6"></a>
## off('serviceDie')

```TypeScript
off(type: 'serviceDie', callback?: () => void): void
```

取消注册设备管理服务死亡监听。

**起始版本：** 7

**废弃版本：** 11

**替代接口：** off(type:

**需要权限：** ohos.permission.ACCESS_SERVICE_DM

<!--Device-DeviceManager-off(type: 'serviceDie', callback?: () => void): void--><!--Device-DeviceManager-off(type: 'serviceDie', callback?: () => void): void-End-->

**系统能力：** SystemCapability.DistributedHardware.DeviceManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'serviceDie' | 是 | 取消注册serviceDie回调，以便在devicemanager服务异常终止时通知应用程序，固定为serviceDie。 |
| callback | () =&gt; void | 否 | 取消注册serviceDie的回调方法。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter type;3. Parameter verification failed;4. The size of specified eventType is greater than 255. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |

**示例：**

示例中的初始化请参见[deviceManager.createDeviceManager](#devicemanagercreatedevicemanager)。

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

<a id="on"></a>
## on('uiStateChange')

```TypeScript
on(type: 'uiStateChange', callback: Callback<{ param: string }>): void
```

ui状态变更回调。

**起始版本：** 9

**废弃版本：** 11

**替代接口：** on(type:

**需要权限：** ohos.permission.ACCESS_SERVICE_DM

<!--Device-DeviceManager-on(type: 'uiStateChange', callback: Callback<{ param: string }>): void--><!--Device-DeviceManager-on(type: 'uiStateChange', callback: Callback<{ param: string }>): void-End-->

**系统能力：** SystemCapability.DistributedHardware.DeviceManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'uiStateChange' | 是 | 注册的设备管理器 ui 状态回调，以便在状态改变时通知应用，固定为uiStateChange。 |
| callback | [Callback](../../apis-arkui/arkts-components/arkts-arkui-callback-i.md)&lt;{ param: string }&gt; | 是 |  |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter type;3. Parameter verification failed;4. The size of specified eventType is greater than 255. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |

**示例：**

示例中的初始化请参见[deviceManager.createDeviceManager](#devicemanagercreatedevicemanager)。

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

<a id="on-1"></a>
## on('deviceStateChange')

```TypeScript
on(type: 'deviceStateChange', callback: Callback<{ action: DeviceStateChangeAction, device: DeviceInfo }>): void
```

注册设备状态回调。

**起始版本：** 7

**废弃版本：** 11

**替代接口：** on(type:

**需要权限：** ohos.permission.ACCESS_SERVICE_DM

<!--Device-DeviceManager-on(type: 'deviceStateChange', callback: Callback<{ action: DeviceStateChangeAction, device: DeviceInfo }>): void--><!--Device-DeviceManager-on(type: 'deviceStateChange', callback: Callback<{ action: DeviceStateChangeAction, device: DeviceInfo }>): void-End-->

**系统能力：** SystemCapability.DistributedHardware.DeviceManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'deviceStateChange' | 是 | 注册设备状态回调，固定为deviceStateChange。 |
| callback | [Callback](../../apis-arkui/arkts-components/arkts-arkui-callback-i.md)&lt;{ action: DeviceStateChangeAction, device: DeviceInfo }&gt; | 是 |  |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter type;3. Parameter verification failed;4. The size of specified eventType is greater than 255. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |

**示例：**

示例中的初始化请参见[deviceManager.createDeviceManager](#devicemanagercreatedevicemanager)。

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

<a id="on-2"></a>
## on('deviceFound')

```TypeScript
on(type: 'deviceFound', callback: Callback<{ subscribeId: number, device: DeviceInfo }>): void
```

注册发现设备回调监听。

**起始版本：** 7

**废弃版本：** 11

**替代接口：** on(type:

**需要权限：** ohos.permission.ACCESS_SERVICE_DM

<!--Device-DeviceManager-on(type: 'deviceFound', callback: Callback<{ subscribeId: number, device: DeviceInfo }>): void--><!--Device-DeviceManager-on(type: 'deviceFound', callback: Callback<{ subscribeId: number, device: DeviceInfo }>): void-End-->

**系统能力：** SystemCapability.DistributedHardware.DeviceManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'deviceFound' | 是 | 注册设备发现回调，以便在发现周边设备时通知应用程序，固定为deviceFound。 |
| callback | [Callback](../../apis-arkui/arkts-components/arkts-arkui-callback-i.md)&lt;{ subscribeId: number, device: DeviceInfo }&gt; | 是 |  |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter type;3. Parameter verification failed;4. The size of specified eventType is greater than 255. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |

**示例：**

示例中的初始化请参见[deviceManager.createDeviceManager](#devicemanagercreatedevicemanager)。

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

<a id="on-3"></a>
## on('discoverFail')

```TypeScript
on(type: 'discoverFail', callback: Callback<{ subscribeId: number, reason: number }>): void
```

注册设备发现失败回调监听。

**起始版本：** 7

**废弃版本：** 11

**替代接口：** on(type:

**需要权限：** ohos.permission.ACCESS_SERVICE_DM

<!--Device-DeviceManager-on(type: 'discoverFail', callback: Callback<{ subscribeId: number, reason: number }>): void--><!--Device-DeviceManager-on(type: 'discoverFail', callback: Callback<{ subscribeId: number, reason: number }>): void-End-->

**系统能力：** SystemCapability.DistributedHardware.DeviceManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'discoverFail' | 是 | 注册设备发现失败回调，以便在发现周边设备失败时通知应用程序，固定为discoverFail。 |
| callback | [Callback](../../apis-arkui/arkts-components/arkts-arkui-callback-i.md)&lt;{ subscribeId: number, reason: number }&gt; | 是 |  |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter type;3. Parameter verification failed;4. The size of specified eventType is greater than 255. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |

**示例：**

示例中的初始化请参见[deviceManager.createDeviceManager](#devicemanagercreatedevicemanager)。

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

<a id="on-4"></a>
## on('publishSuccess')

```TypeScript
on(type: 'publishSuccess', callback: Callback<{ publishId: number }>): void
```

注册发布设备发现回调监听。

**起始版本：** 9

**废弃版本：** 11

**需要权限：** ohos.permission.ACCESS_SERVICE_DM

<!--Device-DeviceManager-on(type: 'publishSuccess', callback: Callback<{ publishId: number }>): void--><!--Device-DeviceManager-on(type: 'publishSuccess', callback: Callback<{ publishId: number }>): void-End-->

**系统能力：** SystemCapability.DistributedHardware.DeviceManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'publishSuccess' | 是 | 注册发布设备成功回调，以便将发布成功时通知应用程序，固定为publishSuccess。 |
| callback | [Callback](../../apis-arkui/arkts-components/arkts-arkui-callback-i.md)&lt;{ publishId: number }&gt; | 是 |  |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter type;3. Parameter verification failed;4. The size of specified eventType is greater than 255. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |

**示例：**

示例中的初始化请参见[deviceManager.createDeviceManager](#devicemanagercreatedevicemanager)。

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

<a id="on-5"></a>
## on('publishFail')

```TypeScript
on(type: 'publishFail', callback: Callback<{ publishId: number, reason: number }>): void
```

注册设备发布失败回调监听。

**起始版本：** 9

**废弃版本：** 11

**需要权限：** ohos.permission.ACCESS_SERVICE_DM

<!--Device-DeviceManager-on(type: 'publishFail', callback: Callback<{ publishId: number, reason: number }>): void--><!--Device-DeviceManager-on(type: 'publishFail', callback: Callback<{ publishId: number, reason: number }>): void-End-->

**系统能力：** SystemCapability.DistributedHardware.DeviceManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'publishFail' | 是 | 注册设备发布失败回调，以便在发布设备失败时通知应用程序，固定为publishFail。 |
| callback | [Callback](../../apis-arkui/arkts-components/arkts-arkui-callback-i.md)&lt;{ publishId: number, reason: number }&gt; | 是 |  |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter type;3. Parameter verification failed;4. The size of specified eventType is greater than 255. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |

**示例：**

示例中的初始化请参见[deviceManager.createDeviceManager](#devicemanagercreatedevicemanager)。

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

<a id="on-6"></a>
## on('serviceDie')

```TypeScript
on(type: 'serviceDie', callback: () => void): void
```

注册设备管理服务死亡监听。

**起始版本：** 7

**废弃版本：** 11

**替代接口：** on(type:

**需要权限：** ohos.permission.ACCESS_SERVICE_DM

<!--Device-DeviceManager-on(type: 'serviceDie', callback: () => void): void--><!--Device-DeviceManager-on(type: 'serviceDie', callback: () => void): void-End-->

**系统能力：** SystemCapability.DistributedHardware.DeviceManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'serviceDie' | 是 | 注册serviceDie回调，以便在devicemanager服务异常终止时通知应用程序，固定为serviceDie。 |
| callback | () =&gt; void | 是 | 注册serviceDie的回调方法。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter type;3. Parameter verification failed;4. The size of specified eventType is greater than 255. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |

**示例：**

示例中的初始化请参见[deviceManager.createDeviceManager](#devicemanagercreatedevicemanager)。

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

<a id="publishdevicediscovery"></a>
## publishDeviceDiscovery

```TypeScript
publishDeviceDiscovery(publishInfo: PublishInfo): void
```

发布设备发现。发布状态持续两分钟，超过两分钟会停止发布。

**起始版本：** 9

**废弃版本：** 11

**需要权限：** ohos.permission.ACCESS_SERVICE_DM

<!--Device-DeviceManager-publishDeviceDiscovery(publishInfo: PublishInfo): void--><!--Device-DeviceManager-publishDeviceDiscovery(publishInfo: PublishInfo): void-End-->

**系统能力：** SystemCapability.DistributedHardware.DeviceManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| publishInfo | [PublishInfo](arkts-distributedservice-devicemanager-publishinfo-i-sys.md) | 是 | 发布设备发现信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter type;3. Parameter verification failed. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [11600105](../../apis-distributedservice-kit/errorcode-device-manager.md#11600105-发布业务不可用) | Publish unavailable. |
| [11600101](../../apis-distributedservice-kit/errorcode-device-manager.md#11600101-服务调用异常) | Failed to execute the function. |

**示例：**

示例中的初始化请参见[deviceManager.createDeviceManager](#devicemanagercreatedevicemanager)。

```TypeScript
import { BusinessError } from '@ohos.base';

interface PublishInfo {
  publishId: number;
  mode: number; // 主动模式
  freq: number; // 高频率
  ranging: boolean; // 支持发现时测距
};

// 生成发布标识，随机数确保每次调用发布接口的标识不一致
let publishId = Math.floor(Math.random() * 10000 + 1000);
let publishInfo: PublishInfo = {
  publishId: publishId,
  mode: 0xAA, // 主动模式
  freq: 2,    // 高频率
  ranging: true  // 支持发现时测距
};

try {
  dmInstance.publishDeviceDiscovery(publishInfo); // 当有发布结果时，通过回调通知给应用程序
} catch (err) {
  let e: BusinessError = err as BusinessError;
  console.error("publishDeviceDiscovery errCode:" + e.code + ",errMessage:" + e.message);
}

```

<a id="release"></a>
## release

```TypeScript
release(): void
```

设备管理实例不再使用后，通过该方法释放DeviceManager实例。

**起始版本：** 7

**废弃版本：** 11

**替代接口：** [releaseDeviceManager](arkts-distributedservice-distributeddevicemanager-releasedevicemanager-f.md#releasedevicemanager-1)

**需要权限：** ohos.permission.ACCESS_SERVICE_DM

<!--Device-DeviceManager-release(): void--><!--Device-DeviceManager-release(): void-End-->

**系统能力：** SystemCapability.DistributedHardware.DeviceManager

**系统接口：** 此接口为系统接口。

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [11600101](../../apis-distributedservice-kit/errorcode-device-manager.md#11600101-服务调用异常) | Failed to execute the function. |

**示例：**

示例中的初始化请参见[deviceManager.createDeviceManager](#devicemanagercreatedevicemanager)。

```TypeScript
import { BusinessError } from '@ohos.base';

try {
  dmInstance.release();
} catch (err) {
  let e: BusinessError = err as BusinessError;
  console.error("release errCode:" + e.code + ",errMessage:" + e.message);
}

```

<a id="requestcredentialregisterinfo"></a>
## requestCredentialRegisterInfo

```TypeScript
requestCredentialRegisterInfo(requestInfo: string, callback: AsyncCallback<{ registerInfo: string }>): void
```

获取凭据的注册信息。

**起始版本：** 10

**废弃版本：** 11

**需要权限：** ohos.permission.ACCESS_SERVICE_DM

<!--Device-DeviceManager-requestCredentialRegisterInfo(requestInfo: string, callback: AsyncCallback<{ registerInfo: string }>): void--><!--Device-DeviceManager-requestCredentialRegisterInfo(requestInfo: string, callback: AsyncCallback<{ registerInfo: string }>): void-End-->

**系统能力：** SystemCapability.DistributedHardware.DeviceManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| requestInfo | string | 是 | 请求凭据信息。最大长度255字符。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;{ registerInfo: string }&gt; | 是 |  |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter type;3. Parameter verification failed;4. The size of specified requestInfo is greater than 255. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |

**示例：**

示例中的初始化请参见[deviceManager.createDeviceManager](#devicemanagercreatedevicemanager)。

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

<a id="setuseroperation"></a>
## setUserOperation

```TypeScript
setUserOperation(operateAction: number, params: string): void
```

设置用户ui操作行为。

**起始版本：** 9

**废弃版本：** 11

**替代接口：** [replyUiAction](arkts-distributedservice-distributeddevicemanager-devicemanager-i-sys.md#replyuiaction-1)

**需要权限：** ohos.permission.ACCESS_SERVICE_DM

<!--Device-DeviceManager-setUserOperation(operateAction: number, params: string): void--><!--Device-DeviceManager-setUserOperation(operateAction: number, params: string): void-End-->

**系统能力：** SystemCapability.DistributedHardware.DeviceManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| operateAction | number | 是 | 用户操作动作。取值范围为0~5。 |
| params | string | 是 | 表示用户的输入参数。长度范围1~255字符。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter type;3. Parameter verification failed;4. The size of specified params is greater than 255. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |

**示例：**

示例中的初始化请参见[deviceManager.createDeviceManager](#devicemanagercreatedevicemanager)。

```TypeScript
import { BusinessError } from '@ohos.base';

try {
  /*
    operateAction = 0 - 允许授权
    operateAction = 1 - 取消授权
    operateAction = 2 - 授权框用户操作超时
    operateAction = 3 - 取消pin码框展示
    operateAction = 4 - 取消pin码输入框展示
    operateAction = 5 - pin码输入框确定操作
   */
  let operation = 0;
  dmInstance.setUserOperation(operation, "extra");
} catch (err) {
  let e: BusinessError = err as BusinessError;
  console.error("setUserOperation errCode:" + e.code + ",errMessage:" + e.message);
}

```

<a id="startdevicediscovery"></a>
## startDeviceDiscovery

```TypeScript
startDeviceDiscovery(subscribeInfo: SubscribeInfo): void
```

发现周边设备。发现状态持续两分钟，超过两分钟，会停止发现，最大发现数量99个。

**起始版本：** 8

**废弃版本：** 11

**替代接口：** [startDiscovering(discoverParam:](arkts-distributedservice-distributeddevicemanager-devicemanager-i.md#startdiscovering-1)

**需要权限：** ohos.permission.ACCESS_SERVICE_DM

<!--Device-DeviceManager-startDeviceDiscovery(subscribeInfo: SubscribeInfo): void--><!--Device-DeviceManager-startDeviceDiscovery(subscribeInfo: SubscribeInfo): void-End-->

**系统能力：** SystemCapability.DistributedHardware.DeviceManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| subscribeInfo | [SubscribeInfo](arkts-distributedservice-devicemanager-subscribeinfo-i-sys.md) | 是 | 发现信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter type;3. Parameter verification failed;4. The size of specified param is greater than 255. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [11600104](../../apis-distributedservice-kit/errorcode-device-manager.md#11600104-发现业务不可用) | Discovery unavailable. |
| [11600101](../../apis-distributedservice-kit/errorcode-device-manager.md#11600101-服务调用异常) | Failed to execute the function. |

**示例：**

示例中的初始化请参见[deviceManager.createDeviceManager](#devicemanagercreatedevicemanager)。

```TypeScript
import { BusinessError } from '@ohos.base';

interface SubscribeInfo {
  subscribeId: number;
  mode: number;   // 主动模式
  medium: number; // 自动发现类型，同时支持多种发现类型
  freq: number;   // 高频率
  isSameAccount: boolean;
  isWakeRemote: boolean;
  capability: number;
}

// 生成发现标识，随机数确保每次调用发现接口的标识不一致
let subscribeId = Math.floor(Math.random() * 10000 + 1000);
let subscribeInfo: SubscribeInfo = {
  subscribeId: subscribeId,
  mode: 0xAA, // 主动模式
  medium: 0,  // 自动发现类型，同时支持多种发现类型
  freq: 2,    // 高频率
  isSameAccount: false,
  isWakeRemote: false,
  capability: 1
};
try {
  dmInstance.startDeviceDiscovery(subscribeInfo); // 当有设备发现时，通过deviceFound回调通知给应用程序
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

发现周边设备。发现状态持续两分钟，超过两分钟，会停止发现，最大发现数量99个。

**起始版本：** 9

**废弃版本：** 11

**替代接口：** [startDiscovering(discoverParam:](arkts-distributedservice-distributeddevicemanager-devicemanager-i.md#startdiscovering-1)

**需要权限：** ohos.permission.ACCESS_SERVICE_DM

<!--Device-DeviceManager-startDeviceDiscovery(subscribeInfo: SubscribeInfo, filterOptions?: string): void--><!--Device-DeviceManager-startDeviceDiscovery(subscribeInfo: SubscribeInfo, filterOptions?: string): void-End-->

**系统能力：** SystemCapability.DistributedHardware.DeviceManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| subscribeInfo | [SubscribeInfo](arkts-distributedservice-devicemanager-subscribeinfo-i-sys.md) | 是 | 发现信息。 |
| filterOptions | string | 否 | 发现设备过滤信息。可选，默认为undefined，发现未上线设备。长度范围1~255字符。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter type;3. Parameter verification failed;4. The size of specified param is greater than 255. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [11600104](../../apis-distributedservice-kit/errorcode-device-manager.md#11600104-发现业务不可用) | Discovery unavailable. |
| [11600101](../../apis-distributedservice-kit/errorcode-device-manager.md#11600101-服务调用异常) | Failed to execute the function. |

**示例：**

示例中的初始化请参见[deviceManager.createDeviceManager](#devicemanagercreatedevicemanager)。

```TypeScript
import { BusinessError } from '@ohos.base';

interface Filters {
  type: string;
  value: number;
}

interface FilterOptions {
  filter_op: string; // 可选, 默认"OR"
  filters: Filters[];
}

interface SubscribeInfo {
  subscribeId: number;
  mode: number;   // 主动模式
  medium: number; // 自动发现类型，同时支持多种发现类型
  freq: number;   // 高频率
  isSameAccount: boolean;
  isWakeRemote: boolean;
  capability: number;
}

// 生成发现标识，随机数确保每次调用发现接口的标识不一致
let subscribeId = Math.floor(Math.random() * 10000 + 1000);
let subscribeInfo: SubscribeInfo = {
  subscribeId: subscribeId,
  mode: 0xAA, // 主动模式
  medium: 0,  // 自动发现类型，同时支持多种发现类型
  freq: 2,    // 高频率
  isSameAccount: false,
  isWakeRemote: false,
  capability: 1
};

let filters: Filters[] = [
  {
      type: "range",
      value: 50 // 需过滤发现设备的距离，单位(cm)
  }
];

let filterOptions: FilterOptions = {
  filter_op: "OR", // 可选, 默认"OR"
  filters: filters
};
try {
  dmInstance.startDeviceDiscovery(subscribeInfo, JSON.stringify(filterOptions)); // 当有设备发现时，通过deviceFound回调通知给应用程序
} catch (err) {
  let e: BusinessError = err as BusinessError;
  console.error("startDeviceDiscovery errCode:" + e.code + ",errMessage:" + e.message);
}

```

<a id="stopdevicediscovery"></a>
## stopDeviceDiscovery

```TypeScript
stopDeviceDiscovery(subscribeId: number): void
```

停止发现周边设备。

**起始版本：** 7

**废弃版本：** 11

**替代接口：** [stopDiscovering](arkts-distributedservice-distributeddevicemanager-devicemanager-i.md#stopdiscovering-1)

**需要权限：** ohos.permission.ACCESS_SERVICE_DM

<!--Device-DeviceManager-stopDeviceDiscovery(subscribeId: number): void--><!--Device-DeviceManager-stopDeviceDiscovery(subscribeId: number): void-End-->

**系统能力：** SystemCapability.DistributedHardware.DeviceManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| subscribeId | number | 是 | 发现标识。取值范围为1~65535。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter type;3. Parameter verification failed;4. The size of specified param is greater than 255. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [11600101](../../apis-distributedservice-kit/errorcode-device-manager.md#11600101-服务调用异常) | Failed to execute the function. |

**示例：**

示例中的初始化请参见[deviceManager.createDeviceManager](#devicemanagercreatedevicemanager)。

```TypeScript
import { BusinessError } from '@ohos.base';

try {
  // stopDeviceDiscovery和startDeviceDiscovery需配对使用，入参需要和startDeviceDiscovery接口传入的subscribeId值相等
  let subscribeId = 12345;
  dmInstance.stopDeviceDiscovery(subscribeId);
} catch (err) {
  let e: BusinessError = err as BusinessError;
  console.error("stopDeviceDiscovery errCode:" + e.code + ",errMessage:" + e.message);
}

```

<a id="unauthenticatedevice"></a>
## unAuthenticateDevice

```TypeScript
unAuthenticateDevice(deviceInfo: DeviceInfo): void
```

解除认证设备。

**起始版本：** 8

**废弃版本：** 11

**替代接口：** [unbindTarget](arkts-distributedservice-distributeddevicemanager-devicemanager-i.md#unbindtarget-1)

**需要权限：** ohos.permission.ACCESS_SERVICE_DM

<!--Device-DeviceManager-unAuthenticateDevice(deviceInfo: DeviceInfo): void--><!--Device-DeviceManager-unAuthenticateDevice(deviceInfo: DeviceInfo): void-End-->

**系统能力：** SystemCapability.DistributedHardware.DeviceManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| deviceInfo | [DeviceInfo](../../apis-avsession-kit/arkts-apis/arkts-avsession-avsession-deviceinfo-i-sys.md) | 是 | 设备信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter type;3. Parameter verification failed. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [11600101](../../apis-distributedservice-kit/errorcode-device-manager.md#11600101-服务调用异常) | Failed to execute the function. |

**示例：**

示例中的初始化请参见[deviceManager.createDeviceManager](#devicemanagercreatedevicemanager)。

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

<a id="unpublishdevicediscovery"></a>
## unPublishDeviceDiscovery

```TypeScript
unPublishDeviceDiscovery(publishId: number): void
```

停止发布设备发现。

**起始版本：** 9

**废弃版本：** 11

**需要权限：** ohos.permission.ACCESS_SERVICE_DM

<!--Device-DeviceManager-unPublishDeviceDiscovery(publishId: number): void--><!--Device-DeviceManager-unPublishDeviceDiscovery(publishId: number): void-End-->

**系统能力：** SystemCapability.DistributedHardware.DeviceManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| publishId | number | 是 | 发布标识。 取值范围为1~2147483647。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter type;3. Parameter verification failed. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [11600101](../../apis-distributedservice-kit/errorcode-device-manager.md#11600101-服务调用异常) | Failed to execute the function. |

**示例：**

示例中的初始化请参见[deviceManager.createDeviceManager](#devicemanagercreatedevicemanager)。

```TypeScript
import { BusinessError } from '@ohos.base';

try {
  // unPublishDeviceDiscovery和publishDeviceDiscovery配对使用，入参需要和publishDeviceDiscovery接口传入的publishId值相等
  let publishId = 12345;
  dmInstance.unPublishDeviceDiscovery(publishId);
} catch (err) {
  let e: BusinessError = err as BusinessError;
  console.error("unPublishDeviceDiscovery errCode:" + e.code + ",errMessage:" + e.message);
}

```

<a id="verifyauthinfo"></a>
## verifyAuthInfo

```TypeScript
verifyAuthInfo(authInfo: AuthInfo, callback: AsyncCallback<{ deviceId: string, level: number }>): void
```

验证认证信息。

**起始版本：** 7

**废弃版本：** 11

**需要权限：** ohos.permission.ACCESS_SERVICE_DM

<!--Device-DeviceManager-verifyAuthInfo(authInfo: AuthInfo, callback: AsyncCallback<{ deviceId: string, level: number }>): void--><!--Device-DeviceManager-verifyAuthInfo(authInfo: AuthInfo, callback: AsyncCallback<{ deviceId: string, level: number }>): void-End-->

**系统能力：** SystemCapability.DistributedHardware.DeviceManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| authInfo | [AuthInfo](arkts-distributedservice-devicemanager-authinfo-i-sys.md) | 是 | 认证信息。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;{ deviceId: string, level: number }&gt; | 是 |  |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter type;3. Parameter verification failed. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |

**示例：**

示例中的初始化请参见[deviceManager.createDeviceManager](#devicemanagercreatedevicemanager)。

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

