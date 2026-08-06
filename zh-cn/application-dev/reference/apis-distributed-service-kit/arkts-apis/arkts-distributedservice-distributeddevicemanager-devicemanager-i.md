# DeviceManager

设备管理实例，用于获取可信设备和本地设备的相关信息。在调用DeviceManager的方法前，需要先通过createDeviceManager构建一个DeviceManager实例dmInstance。

**起始版本：** 10

**ArkTS模式：** ArkTS-Dyn起始版本为10；ArkTS-Sta起始版本为23。

<!--Device-distributedDeviceManager-interface DeviceManager--><!--Device-distributedDeviceManager-interface DeviceManager-End-->

**系统能力：** SystemCapability.DistributedHardware.DeviceManager

## bindTarget

```TypeScript
bindTarget(deviceId: string, bindParam: { [key: string]: Object; }, callback: AsyncCallback<{deviceId: string;}>): void
```

认证设备。使用callback异步回调。

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**需要权限：** ohos.permission.DISTRIBUTED_DATASYNC

<!--Device-DeviceManager-bindTarget(deviceId: string, bindParam: { [key: string]: Object; }, callback: AsyncCallback<{deviceId: string;}>): void--><!--Device-DeviceManager-bindTarget(deviceId: string, bindParam: { [key: string]: Object; }, callback: AsyncCallback<{deviceId: string;}>): void-End-->

**系统能力：** SystemCapability.DistributedHardware.DeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| deviceId | string | 是 | 设备标识。长度范围1~255字符。 |
| bindParam | { [key: string]: Object; } | 是 | 认证参数。由开发者自行决定传入的键值对。默认会携带以下key值：\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_bindType 此值是绑定的类型，必填。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_1\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_-1：PIN码。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_2\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_targetPkgName 绑定目标的包名。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_3\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_appName 尝试绑定目标的应用程序名称。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_4\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_appOperation 应用程序要绑定目标的原因。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_5\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_customDescription 操作的详细说明。 |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;{deviceId: string;}&gt; | 是 |  |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter type;3. Parameter verification failed;4. The size of specified deviceId is greater than 255. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [11600101](../../apis-distributedservice-kit/errorcode-device-manager.md#11600101-服务调用异常) | Failed to execute the function. |
| [11600103](../../apis-distributedservice-kit/errorcode-device-manager.md#11600103-认证业务不可用) | Authentication unavailable. |

**示例：**

```TypeScript
import { distributedDeviceManager } from '@kit.DistributedServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

class BindResultData {
  deviceId: string = '';
}
// 设备标识，可通过startDiscovering发现设备后从discoverSuccess回调获取DeviceBasicInfo.deviceId，或通过getAvailableDeviceListSync/getAvailableDeviceList获取可信设备的DeviceBasicInfo.deviceId
let deviceId = 'XXXXXXXX';
// 认证参数
let bindParam: Record<string, string | number> = {
  'bindType': 1, // 绑定类型： 1 - PIN码认证
  'targetPkgName': 'xxxx',
  'appName': 'xxxx',
  'appOperation': 'xxxx',
  'customDescription': 'xxxx'
};

try {
  // 创建设备管理实例
  let dmInstance = distributedDeviceManager.createDeviceManager('ohos.samples.jsHelloWorld');
  // 认证设备
  dmInstance.bindTarget(deviceId, bindParam, (err: BusinessError, data: BindResultData) => {
    if (err) {
      console.error(`Failed to bind target. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info('bindTarget result:' + JSON.stringify(data));
  });
} catch (err) {
  let error: BusinessError = err as BusinessError;
  console.error(`Failed to bind target. Code: ${error.code}, message: ${error.message}`);
}
```

## bindTarget

```TypeScript
bindTarget(deviceId: string, bindParam: Record<string, int | string>, callback: AsyncCallback<BindTargetResult>): void
```

认证设备。使用callback异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**需要权限：** ohos.permission.DISTRIBUTED_DATASYNC

<!--Device-DeviceManager-bindTarget(deviceId: string, bindParam: Record<string, int | string>, callback: AsyncCallback<BindTargetResult>): void--><!--Device-DeviceManager-bindTarget(deviceId: string, bindParam: Record<string, int | string>, callback: AsyncCallback<BindTargetResult>): void-End-->

**系统能力：** SystemCapability.DistributedHardware.DeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| deviceId | string | 是 | 设备标识。长度范围1~255字符。 |
| bindParam | Record&lt;string, int \| string&gt; | 是 | 认证参数。由开发者自行决定传入的键值对。默认会携带以下key值：\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_bindType 此值是绑定的类型，必填。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_1\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_-1：PIN码。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_2\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_targetPkgName 绑定目标的包名。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_3\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_appName 尝试绑定目标的应用程序名称。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_4\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_appOperation 应用程序要绑定目标的原因。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_5\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_customDescription 操作的详细说明。 |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;BindTargetResult&gt; | 是 | 认证结果回调。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [11600101](../../apis-distributedservice-kit/errorcode-device-manager.md#11600101-服务调用异常) | Failed to execute the function. |
| [11600103](../../apis-distributedservice-kit/errorcode-device-manager.md#11600103-认证业务不可用) | Authentication unavailable. |

## getAvailableDeviceList

```TypeScript
getAvailableDeviceList(callback: AsyncCallback<Array<DeviceBasicInfo>>): void
```

获取所有可信设备列表。使用callback异步回调。

**起始版本：** 10

**ArkTS模式：** ArkTS-Dyn起始版本为10；ArkTS-Sta起始版本为23。

**需要权限：** ohos.permission.DISTRIBUTED_DATASYNC

<!--Device-DeviceManager-getAvailableDeviceList(callback: AsyncCallback<Array<DeviceBasicInfo>>): void--><!--Device-DeviceManager-getAvailableDeviceList(callback: AsyncCallback<Array<DeviceBasicInfo>>): void-End-->

**系统能力：** SystemCapability.DistributedHardware.DeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;Array&lt;DeviceBasicInfo&gt;&gt; | 是 | 获取所有可信设备列表的回调，返回设备信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [11600101](../../apis-distributedservice-kit/errorcode-device-manager.md#11600101-服务调用异常) | Failed to execute the function. |

**示例：**

```TypeScript
import { distributedDeviceManager } from '@kit.DistributedServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  // 创建设备管理实例
  let dmInstance = distributedDeviceManager.createDeviceManager('ohos.samples.jsHelloWorld');
  // 获取所有在线可信设备
  dmInstance.getAvailableDeviceList((err: BusinessError, data: Array<distributedDeviceManager.DeviceBasicInfo>) => {
    if (err) {
      console.error(`Failed to get available device list. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info('get available device info: ' + JSON.stringify(data));
  });
} catch (err) {
  let error: BusinessError = err as BusinessError;
  console.error(`Failed to get available device list. Code: ${error.code}, message: ${error.message}`);
}
```

## getAvailableDeviceList

```TypeScript
getAvailableDeviceList(): Promise<Array<DeviceBasicInfo>>
```

获取所有可信设备列表。使用Promise异步回调。

**起始版本：** 10

**ArkTS模式：** ArkTS-Dyn起始版本为10；ArkTS-Sta起始版本为23。

**需要权限：** ohos.permission.DISTRIBUTED_DATASYNC

<!--Device-DeviceManager-getAvailableDeviceList(): Promise<Array<DeviceBasicInfo>>--><!--Device-DeviceManager-getAvailableDeviceList(): Promise<Array<DeviceBasicInfo>>-End-->

**系统能力：** SystemCapability.DistributedHardware.DeviceManager

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;DeviceBasicInfo&gt;&gt; | Promise实例，用于获取异步返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [11600101](../../apis-distributedservice-kit/errorcode-device-manager.md#11600101-服务调用异常) | Failed to execute the function. |

**示例：**

```TypeScript
import { distributedDeviceManager } from '@kit.DistributedServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  // 创建设备管理实例
  let dmInstance = distributedDeviceManager.createDeviceManager('ohos.samples.jsHelloWorld');
  // 获取所有在线可信设备
  dmInstance.getAvailableDeviceList().then((data: Array<distributedDeviceManager.DeviceBasicInfo>) => {
    console.info('get available device info: ' + JSON.stringify(data));
  }).catch((err: BusinessError) => {
    console.error(`Failed to get available device list. Code: ${err.code}, message: ${err.message}`);
  });
} catch (err) {
  let error: BusinessError = err as BusinessError;
  console.error(`Failed to get available device list. Code: ${error.code}, message: ${error.message}`);
}
```

## getAvailableDeviceListSync

```TypeScript
getAvailableDeviceListSync(): Array<DeviceBasicInfo>
```

同步获取所有可信设备列表。

**起始版本：** 10

**ArkTS模式：** ArkTS-Dyn起始版本为10；ArkTS-Sta起始版本为23。

**需要权限：** ohos.permission.DISTRIBUTED_DATASYNC

<!--Device-DeviceManager-getAvailableDeviceListSync(): Array<DeviceBasicInfo>--><!--Device-DeviceManager-getAvailableDeviceListSync(): Array<DeviceBasicInfo>-End-->

**系统能力：** SystemCapability.DistributedHardware.DeviceManager

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;DeviceBasicInfo&gt; | 返回可信设备列表。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [11600101](../../apis-distributedservice-kit/errorcode-device-manager.md#11600101-服务调用异常) | Failed to execute the function. |

**示例：**

```TypeScript
import { distributedDeviceManager } from '@kit.DistributedServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  // 创建设备管理实例
  let dmInstance = distributedDeviceManager.createDeviceManager('ohos.samples.jsHelloWorld');
  // 同步获取所有在线可信设备
  let deviceInfoList: Array<distributedDeviceManager.DeviceBasicInfo> = dmInstance.getAvailableDeviceListSync();
} catch (err) {
  let error: BusinessError = err as BusinessError;
  console.error(`Failed to get available device list sync. Code: ${error.code}, message: ${error.message}`);
}
```

## getDeviceName

```TypeScript
getDeviceName(networkId: string): string
```

通过指定设备的网络标识获取该设备名称。

**起始版本：** 10

**ArkTS模式：** ArkTS-Dyn起始版本为10；ArkTS-Sta起始版本为23。

**需要权限：** ohos.permission.DISTRIBUTED_DATASYNC

<!--Device-DeviceManager-getDeviceName(networkId: string): string--><!--Device-DeviceManager-getDeviceName(networkId: string): string-End-->

**系统能力：** SystemCapability.DistributedHardware.DeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| networkId | string | 是 | 设备的网络标识。长度范围1~255字符。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 返回指定设备名称。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter type;3. Parameter verification failed;4. The size of specified networkId is greater than 255. |
| [11600101](../../apis-distributedservice-kit/errorcode-device-manager.md#11600101-服务调用异常) | Failed to execute the function. |

**示例：**

```TypeScript
import { distributedDeviceManager } from '@kit.DistributedServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  // 设备网络标识，可通过getAvailableDeviceListSync或getAvailableDeviceList接口获取可信设备列表中的DeviceBasicInfo.networkId
  let networkId = 'xxxxxxx';
  // 创建设备管理实例
  let dmInstance = distributedDeviceManager.createDeviceManager('ohos.samples.jsHelloWorld');
  // 通过设备网络标识获取设备名称
  let deviceName: string = dmInstance.getDeviceName(networkId);
  console.info('device name: ' + JSON.stringify(deviceName));
} catch (err) {
  let error: BusinessError = err as BusinessError;
  console.error(`Failed to get device name. Code: ${error.code}, message: ${error.message}`);
}
```

## getDeviceType

ArkTS-Dyn:
```TypeScript
getDeviceType(networkId: string): number
```

ArkTS-Sta:
```TypeScript
getDeviceType(networkId: string): int
```

通过指定设备的网络标识获取该设备类型。

**起始版本：** 10

**ArkTS模式：** ArkTS-Dyn起始版本为10；ArkTS-Sta起始版本为23。

**需要权限：** ohos.permission.DISTRIBUTED_DATASYNC

<!--Device-DeviceManager-getDeviceType(networkId: string): int--><!--Device-DeviceManager-getDeviceType(networkId: string): int-End-->

**系统能力：** SystemCapability.DistributedHardware.DeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| networkId | string | 是 | 设备的网络标识。长度范围1~255字符。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：int | \_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_MD\_\_\_ESCAPED\_UNDERSCORE\_\_\_COMMENT\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_返回指定设备类型。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_MD\_\_\_ESCAPED\_UNDERSCORE\_\_\_COMMENT\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_1\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_ |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter type;3. Parameter verification failed;4. The size of specified networkId is greater than 255. |
| [11600101](../../apis-distributedservice-kit/errorcode-device-manager.md#11600101-服务调用异常) | Failed to execute the function. |

**示例：**

```TypeScript
import { distributedDeviceManager } from '@kit.DistributedServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  // 设备网络标识，可通过getAvailableDeviceListSync或getAvailableDeviceList接口获取可信设备列表中的DeviceBasicInfo.networkId
  let networkId = 'xxxxxxx';
  // 创建设备管理实例
  let dmInstance = distributedDeviceManager.createDeviceManager('ohos.samples.jsHelloWorld');
  // 通过设备网络标识获取设备类型
  let deviceType: number = dmInstance.getDeviceType(networkId);
  console.info('device type: ' + JSON.stringify(deviceType));
} catch (err) {
  let error: BusinessError = err as BusinessError;
  console.error(`Failed to get device type. Code: ${error.code}, message: ${error.message}`);
}
```

## getLocalDeviceId

```TypeScript
getLocalDeviceId(): string
```

获取本地设备id，实际值为udid-hash与appid和盐值基于sha256方式进行混淆后的值。

**起始版本：** 10

**ArkTS模式：** ArkTS-Dyn起始版本为10；ArkTS-Sta起始版本为23。

**需要权限：** ohos.permission.DISTRIBUTED_DATASYNC

<!--Device-DeviceManager-getLocalDeviceId(): string--><!--Device-DeviceManager-getLocalDeviceId(): string-End-->

**系统能力：** SystemCapability.DistributedHardware.DeviceManager

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 返回本地设备id。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [11600101](../../apis-distributedservice-kit/errorcode-device-manager.md#11600101-服务调用异常) | Failed to execute the function. |

**示例：**

```TypeScript
import { distributedDeviceManager } from '@kit.DistributedServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  // 创建设备管理实例
  let dmInstance = distributedDeviceManager.createDeviceManager('ohos.samples.jsHelloWorld');
  // 获取本地设备标识
  let deviceId: string = dmInstance.getLocalDeviceId();
  console.info('local device id: ' + JSON.stringify(deviceId));
} catch (err) {
  let error: BusinessError = err as BusinessError;
  console.error(`Failed to get local device id. Code: ${error.code}, message: ${error.message}`);
}
```

## getLocalDeviceName

```TypeScript
getLocalDeviceName(): string
```

获取本地设备名称。

**起始版本：** 10

**ArkTS模式：** ArkTS-Dyn起始版本为10；ArkTS-Sta起始版本为23。

**需要权限：** ohos.permission.DISTRIBUTED_DATASYNC

<!--Device-DeviceManager-getLocalDeviceName(): string--><!--Device-DeviceManager-getLocalDeviceName(): string-End-->

**系统能力：** SystemCapability.DistributedHardware.DeviceManager

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 返回本地设备名称。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [11600101](../../apis-distributedservice-kit/errorcode-device-manager.md#11600101-服务调用异常) | Failed to execute the function. |

**示例：**

```TypeScript
import { distributedDeviceManager } from '@kit.DistributedServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  // 创建设备管理实例
  let dmInstance = distributedDeviceManager.createDeviceManager('ohos.samples.jsHelloWorld');
  // 获取本地设备名称
  let deviceName: string = dmInstance.getLocalDeviceName();
  console.info('local device name: ' + JSON.stringify(deviceName));
} catch (err) {
  let error: BusinessError = err as BusinessError;
  console.error(`Failed to get local device name. Code: ${error.code}, message: ${error.message}`);
}
```

## getLocalDeviceNetworkId

```TypeScript
getLocalDeviceNetworkId(): string
```

获取本地设备网络标识。

**起始版本：** 10

**ArkTS模式：** ArkTS-Dyn起始版本为10；ArkTS-Sta起始版本为23。

**需要权限：** ohos.permission.DISTRIBUTED_DATASYNC

<!--Device-DeviceManager-getLocalDeviceNetworkId(): string--><!--Device-DeviceManager-getLocalDeviceNetworkId(): string-End-->

**系统能力：** SystemCapability.DistributedHardware.DeviceManager

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 返回本地设备网络标识。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [11600101](../../apis-distributedservice-kit/errorcode-device-manager.md#11600101-服务调用异常) | Failed to execute the function. |

**示例：**

```TypeScript
import { distributedDeviceManager } from '@kit.DistributedServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  // 创建设备管理实例
  let dmInstance = distributedDeviceManager.createDeviceManager('ohos.samples.jsHelloWorld');
  // 获取本地设备网络标识
  let deviceNetworkId: string = dmInstance.getLocalDeviceNetworkId();
  console.info('local device networkId: ' + JSON.stringify(deviceNetworkId));
} catch (err) {
  let error: BusinessError = err as BusinessError;
  console.error(`Failed to get local device network id. Code: ${error.code}, message: ${error.message}`);
}
```

## getLocalDeviceType

ArkTS-Dyn:
```TypeScript
getLocalDeviceType(): number
```

ArkTS-Sta:
```TypeScript
getLocalDeviceType(): int
```

获取本地设备类型。

**起始版本：** 10

**ArkTS模式：** ArkTS-Dyn起始版本为10；ArkTS-Sta起始版本为23。

**需要权限：** ohos.permission.DISTRIBUTED_DATASYNC

<!--Device-DeviceManager-getLocalDeviceType(): int--><!--Device-DeviceManager-getLocalDeviceType(): int-End-->

**系统能力：** SystemCapability.DistributedHardware.DeviceManager

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：int | \_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_MD\_\_\_ESCAPED\_UNDERSCORE\_\_\_COMMENT\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_返回本地设备类型。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_MD\_\_\_ESCAPED\_UNDERSCORE\_\_\_COMMENT\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_1\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_ |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [11600101](../../apis-distributedservice-kit/errorcode-device-manager.md#11600101-服务调用异常) | Failed to execute the function. |

**示例：**

ArkTS-Dyn示例：

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let dmInstance = distributedDeviceManager.createDeviceManager('ohos.samples.jsHelloWorld');
  let deviceType: number = dmInstance.getLocalDeviceType();
  console.info('local device type: ' + deviceType);
} catch (err) {
  let e: BusinessError = err as BusinessError;
  console.error(`getLocalDeviceType errCode: ${e.code}, errMessage: ${e.message}`);
}
```

ArkTS-Sta示例：

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let dmInstance = distributedDeviceManager.createDeviceManager('ohos.samples.jsHelloWorld');
  let deviceType: int = dmInstance.getLocalDeviceType();
  console.info('local device type: ' + deviceType);
} catch (err) {
  let e: BusinessError = err as BusinessError;
  console.error(`getLocalDeviceType errCode: ${e.code}, errMessage: ${e.message}`);
}
```

## off('deviceStateChange')

```TypeScript
off(type: 'deviceStateChange', callback?: Callback<{ action: DeviceStateChange; device: DeviceBasicInfo; }>): void
```

取消注册设备状态回调。使用callback异步回调。

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**需要权限：** ohos.permission.DISTRIBUTED_DATASYNC

<!--Device-DeviceManager-off(type: 'deviceStateChange', callback?: Callback<{ action: DeviceStateChange; device: DeviceBasicInfo; }>): void--><!--Device-DeviceManager-off(type: 'deviceStateChange', callback?: Callback<{ action: DeviceStateChange; device: DeviceBasicInfo; }>): void-End-->

**系统能力：** SystemCapability.DistributedHardware.DeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'deviceStateChange' | 是 | 根据应用程序的包名取消注册设备状态回调，固定为deviceStateChange。 |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;{ action: DeviceStateChange; device: DeviceBasicInfo; }&gt; | 否 |  |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter type;3. Parameter verification failed;4. The size of specified type is greater than 255. |

**示例：**

```TypeScript
import { distributedDeviceManager } from '@kit.DistributedServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

class DeviceStateChangeData {
  action: distributedDeviceManager.DeviceStateChange = 0;
  device: distributedDeviceManager.DeviceBasicInfo = {
    deviceId: '',
    deviceName: '',
    deviceType: '',
    networkId: ''
  };
}

try {
  // 创建设备管理实例
  let dmInstance = distributedDeviceManager.createDeviceManager('ohos.samples.jsHelloWorld');
  // 取消注册设备状态变化回调
  dmInstance.off('deviceStateChange', (data: DeviceStateChangeData) => {
    console.info('deviceStateChange' + JSON.stringify(data));
  });
} catch (err) {
  let error: BusinessError = err as BusinessError;
  console.error(`Failed to unregister device state change. Code: ${error.code}, message: ${error.message}`);
}
```

## off('discoverSuccess')

```TypeScript
off(type: 'discoverSuccess', callback?: Callback<{ device: DeviceBasicInfo; }>): void
```

取消注册设备发现成功回调。使用callback异步回调。

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**需要权限：** ohos.permission.DISTRIBUTED_DATASYNC

<!--Device-DeviceManager-off(type: 'discoverSuccess', callback?: Callback<{ device: DeviceBasicInfo; }>): void--><!--Device-DeviceManager-off(type: 'discoverSuccess', callback?: Callback<{ device: DeviceBasicInfo; }>): void-End-->

**系统能力：** SystemCapability.DistributedHardware.DeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'discoverSuccess' | 是 | 取消注册设备发现回调，固定为discoverSuccess。 |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;{ device: DeviceBasicInfo; }&gt; | 否 |  |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter type;3. Parameter verification failed;4. The size of specified type is greater than 255. |

**示例：**

```TypeScript
import { distributedDeviceManager } from '@kit.DistributedServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

class DiscoverSuccessData {
  device: distributedDeviceManager.DeviceBasicInfo = {
    deviceId: '',
    deviceName: '',
    deviceType: '',
    networkId: ''
  };
}

try {
  // 创建设备管理实例
  let dmInstance = distributedDeviceManager.createDeviceManager('ohos.samples.jsHelloWorld');
  // 取消注册设备发现成功回调
  dmInstance.off('discoverSuccess', (data: DiscoverSuccessData) => {
    console.info('discoverSuccess' + JSON.stringify(data));
  });
} catch (err) {
  let error: BusinessError = err as BusinessError;
  console.error(`Failed to unregister discover success callback. Code: ${error.code}, message: ${error.message}`);
}
```

## off('deviceNameChange')

```TypeScript
off(type: 'deviceNameChange', callback?: Callback<{ deviceName: string; }>): void
```

取消注册设备名称变更回调监听。使用callback异步回调。

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**需要权限：** ohos.permission.DISTRIBUTED_DATASYNC

<!--Device-DeviceManager-off(type: 'deviceNameChange', callback?: Callback<{ deviceName: string; }>): void--><!--Device-DeviceManager-off(type: 'deviceNameChange', callback?: Callback<{ deviceName: string; }>): void-End-->

**系统能力：** SystemCapability.DistributedHardware.DeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'deviceNameChange' | 是 | 取消注册设备名称改变回调，固定为deviceNameChange。 |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;{ deviceName: string; }&gt; | 否 |  |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter type;3. Parameter verification failed;4. The size of specified type is greater than 255. |

**示例：**

```TypeScript
import { distributedDeviceManager } from '@kit.DistributedServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

class DeviceNameChangeData {
  deviceName: string = '';
}

try {
  // 创建设备管理实例
  let dmInstance = distributedDeviceManager.createDeviceManager('ohos.samples.jsHelloWorld');
  // 取消注册设备名称变更回调
  dmInstance.off('deviceNameChange', (data: DeviceNameChangeData) => {
    console.info('deviceNameChange' + JSON.stringify(data));
  });
} catch (err) {
  let error: BusinessError = err as BusinessError;
  console.error(`Failed to unregister device name change callback. Code: ${error.code}, message: ${error.message}`);
}
```

## off('discoverFailure')

```TypeScript
off(type: 'discoverFailure', callback?: Callback<{ reason: int; }>): void
```

取消注册设备发现失败回调。使用callback异步回调。

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**需要权限：** ohos.permission.DISTRIBUTED_DATASYNC

<!--Device-DeviceManager-off(type: 'discoverFailure', callback?: Callback<{ reason: int; }>): void--><!--Device-DeviceManager-off(type: 'discoverFailure', callback?: Callback<{ reason: int; }>): void-End-->

**系统能力：** SystemCapability.DistributedHardware.DeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'discoverFailure' | 是 | 取消注册设备发现失败回调，固定为discoverFailure。 |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;{ reason: int; }&gt; | 否 |  |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter type;3. Parameter verification failed;4. The size of specified type is greater than 255. |

**示例：**

```TypeScript
import { distributedDeviceManager } from '@kit.DistributedServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

class DiscoverFailureData {
  reason: number = 0;
}

try {
  // 创建设备管理实例
  let dmInstance = distributedDeviceManager.createDeviceManager('ohos.samples.jsHelloWorld');
  // 取消注册设备发现失败回调
  dmInstance.off('discoverFailure', (data: DiscoverFailureData) => {
    console.info('discoverFailure' + JSON.stringify(data));
  });
} catch (err) {
  let error: BusinessError = err as BusinessError;
  console.error(`Failed to unregister discover failure callback. Code: ${error.code}, message: ${error.message}`);
}
```

## off('serviceDie')

```TypeScript
off(type: 'serviceDie', callback?: Callback<{}>): void
```

取消注册设备管理服务死亡回调。使用callback异步回调。

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**需要权限：** ohos.permission.DISTRIBUTED_DATASYNC

<!--Device-DeviceManager-off(type: 'serviceDie', callback?: Callback<{}>): void--><!--Device-DeviceManager-off(type: 'serviceDie', callback?: Callback<{}>): void-End-->

**系统能力：** SystemCapability.DistributedHardware.DeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'serviceDie' | 是 | 取消注册serviceDie回调，以便在devicemanager服务异常终止时通知应用程序，固定为serviceDie。 |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;{}&gt; | 否 |  |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter type;3. Parameter verification failed;4. The size of specified type is greater than 255. |

**示例：**

```TypeScript
import { distributedDeviceManager } from '@kit.DistributedServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  // 创建设备管理实例
  let dmInstance = distributedDeviceManager.createDeviceManager('ohos.samples.jsHelloWorld');
  // 取消注册设备管理服务死亡回调
  dmInstance.off('serviceDie', () => {
    console.info('serviceDie off');
  });
} catch (err) {
  let error: BusinessError = err as BusinessError;
  console.error(`Failed to unregister service die callback. Code: ${error.code}, message: ${error.message}`);
}
```

## offDeviceNameChange

```TypeScript
offDeviceNameChange(callback?: Callback<DeviceNameChangeResult>): void
```

取消注册设备名称变更回调监听。使用callback异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**需要权限：** ohos.permission.DISTRIBUTED_DATASYNC

<!--Device-DeviceManager-offDeviceNameChange(callback?: Callback<DeviceNameChangeResult>): void--><!--Device-DeviceManager-offDeviceNameChange(callback?: Callback<DeviceNameChangeResult>): void-End-->

**系统能力：** SystemCapability.DistributedHardware.DeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;DeviceNameChangeResult&gt; | 否 | 指示要取消注册设备名称改变的回调方法。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed.The application does not have the permission required to call the API. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let dmInstance = distributedDeviceManager.createDeviceManager('ohos.samples.jsHelloWorld');
  dmInstance.offDeviceNameChange((data: distributedDeviceManager.DeviceNameChangeResult) => {
    console.info('deviceNameChange' + JSON.stringify(data));
  });
} catch (err) {
  let e: BusinessError = err as BusinessError;
  console.error(`deviceNameChange errCode: ${e.code}, errMessage: ${e.message}`);
}
```

## offDeviceStateChange

```TypeScript
offDeviceStateChange(callback?: Callback<DeviceStateChangeResult>): void
```

取消注册设备状态回调。使用callback异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**需要权限：** ohos.permission.DISTRIBUTED_DATASYNC

<!--Device-DeviceManager-offDeviceStateChange(callback?: Callback<DeviceStateChangeResult>): void--><!--Device-DeviceManager-offDeviceStateChange(callback?: Callback<DeviceStateChangeResult>): void-End-->

**系统能力：** SystemCapability.DistributedHardware.DeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;DeviceStateChangeResult&gt; | 否 | 指示要取消注册的设备状态回调，返回设备状态和设备信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed.The application does not have the permission required to call the API. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let dmInstance = distributedDeviceManager.createDeviceManager('ohos.samples.jsHelloWorld');
  dmInstance.offDeviceStateChange((data: distributedDeviceManager.DeviceStateChangeResult) => {
    console.info('deviceStateChange' + JSON.stringify(data));
  });
} catch (err) {
  let e: BusinessError = err as BusinessError;
  console.error(`deviceStateChange errCode: ${e.code}, errMessage: ${e.message}`);
}
```

## offDiscoverFailure

```TypeScript
offDiscoverFailure(callback?: Callback<DiscoveryFailureResult>): void
```

取消注册设备发现失败回调。使用callback异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**需要权限：** ohos.permission.DISTRIBUTED_DATASYNC

<!--Device-DeviceManager-offDiscoverFailure(callback?: Callback<DiscoveryFailureResult>): void--><!--Device-DeviceManager-offDiscoverFailure(callback?: Callback<DiscoveryFailureResult>): void-End-->

**系统能力：** SystemCapability.DistributedHardware.DeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;DiscoveryFailureResult&gt; | 否 | 指示要取消注册的设备发现失败回调。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed.The application does not have the permission required to call the API. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let dmInstance = distributedDeviceManager.createDeviceManager('ohos.samples.jsHelloWorld');
  dmInstance.offDiscoverFailure((data: distributedDeviceManager.DiscoveryFailureResult) => {
    console.info('discoverFailure' + JSON.stringify(data));
  });
} catch (err) {
  let e: BusinessError = err as BusinessError;
  console.error(`discoverFailure errCode: ${e.code}, errMessage: ${e.message}`);
}
```

## offDiscoverSuccess

```TypeScript
offDiscoverSuccess(callback?: Callback<DiscoverySuccessResult>): void
```

取消注册设备发现成功回调。使用callback异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**需要权限：** ohos.permission.DISTRIBUTED_DATASYNC

<!--Device-DeviceManager-offDiscoverSuccess(callback?: Callback<DiscoverySuccessResult>): void--><!--Device-DeviceManager-offDiscoverSuccess(callback?: Callback<DiscoverySuccessResult>): void-End-->

**系统能力：** SystemCapability.DistributedHardware.DeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;DiscoverySuccessResult&gt; | 否 | 指示要取消注册的设备发现回调，返回设备状态和设备信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed.The application does not have the permission required to call the API. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let dmInstance = distributedDeviceManager.createDeviceManager('ohos.samples.jsHelloWorld');
  dmInstance.offDiscoverSuccess((data: distributedDeviceManager.DiscoverySuccessResult) => {
    console.info('discoverSuccess' + JSON.stringify(data));
  });
} catch (err) {
  let e: BusinessError = err as BusinessError;
  console.error(`discoverSuccess errCode: ${e.code}, errMessage: ${e.message}`);
}
```

## offServiceDie

```TypeScript
offServiceDie(callback?: Callback<ServiceDieData>): void
```

取消注册设备管理服务死亡回调。使用callback异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**需要权限：** ohos.permission.DISTRIBUTED_DATASYNC

<!--Device-DeviceManager-offServiceDie(callback?: Callback<ServiceDieData>): void--><!--Device-DeviceManager-offServiceDie(callback?: Callback<ServiceDieData>): void-End-->

**系统能力：** SystemCapability.DistributedHardware.DeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;ServiceDieData&gt; | 否 | 取消注册serviceDie的回调方法。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed.The application does not have the permission required to call the API. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let dmInstance = distributedDeviceManager.createDeviceManager('ohos.samples.jsHelloWorld');
  dmInstance.offServiceDie((data: distributedDeviceManager.ServiceDieData) => {
    console.info('serviceDie off');
  });
} catch (err) {
  let e: BusinessError = err as BusinessError;
  console.error(`serviceDie errCode: ${e.code}, errMessage: ${e.message}`);
}
```

## on('deviceStateChange')

```TypeScript
on(type: 'deviceStateChange', callback: Callback<{ action: DeviceStateChange; device: DeviceBasicInfo; }>): void
```

注册设备状态回调，以便在设备状态发生变化时根据应用捆绑包名通知应用。使用callback异步回调。

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**需要权限：** ohos.permission.DISTRIBUTED_DATASYNC

<!--Device-DeviceManager-on(type: 'deviceStateChange', callback: Callback<{ action: DeviceStateChange; device: DeviceBasicInfo; }>): void--><!--Device-DeviceManager-on(type: 'deviceStateChange', callback: Callback<{ action: DeviceStateChange; device: DeviceBasicInfo; }>): void-End-->

**系统能力：** SystemCapability.DistributedHardware.DeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'deviceStateChange' | 是 | 注册设备状态回调，固定为deviceStateChange。 |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;{ action: DeviceStateChange; device: DeviceBasicInfo; }&gt; | 是 |  |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter type;3. Parameter verification failed;4. The size of specified type is greater than 255. |

**示例：**

```TypeScript
import { distributedDeviceManager } from '@kit.DistributedServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

class DeviceStateChangeData {
  action: distributedDeviceManager.DeviceStateChange = 0;
  device: distributedDeviceManager.DeviceBasicInfo = {
    deviceId: '',
    deviceName: '',
    deviceType: '',
    networkId: ''
  };
}

try {
  // 创建设备管理实例
  let dmInstance = distributedDeviceManager.createDeviceManager('ohos.samples.jsHelloWorld');
  // 注册设备状态变化回调
  dmInstance.on('deviceStateChange', (data: DeviceStateChangeData) => {
    console.info('deviceStateChange on:' + JSON.stringify(data));
  });
} catch (err) {
  let error: BusinessError = err as BusinessError;
  console.error(`Failed to register device state change. Code: ${error.code}, message: ${error.message}`);
}
```

## on('discoverSuccess')

```TypeScript
on(type: 'discoverSuccess', callback: Callback<{ device: DeviceBasicInfo; }>): void
```

注册发现设备成功回调监听。使用callback异步回调。

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**需要权限：** ohos.permission.DISTRIBUTED_DATASYNC

<!--Device-DeviceManager-on(type: 'discoverSuccess', callback: Callback<{ device: DeviceBasicInfo; }>): void--><!--Device-DeviceManager-on(type: 'discoverSuccess', callback: Callback<{ device: DeviceBasicInfo; }>): void-End-->

**系统能力：** SystemCapability.DistributedHardware.DeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'discoverSuccess' | 是 | 注册设备发现回调，以便在发现周边设备时通知应用程序，固定为discoverSuccess。 |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;{ device: DeviceBasicInfo; }&gt; | 是 |  |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter type;3. Parameter verification failed;4. The size of specified type is greater than 255. |

**示例：**

```TypeScript
import { distributedDeviceManager } from '@kit.DistributedServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

class DiscoverSuccessData {
  device: distributedDeviceManager.DeviceBasicInfo = {
    deviceId: '',
    deviceName: '',
    deviceType: '',
    networkId: ''
  };
}

try {
  // 创建设备管理实例
  let dmInstance = distributedDeviceManager.createDeviceManager('ohos.samples.jsHelloWorld');
  // 注册设备发现成功回调
  dmInstance.on('discoverSuccess', (data: DiscoverSuccessData) => {
    console.info('discoverSuccess:' + JSON.stringify(data));
  });
} catch (err) {
  let error: BusinessError = err as BusinessError;
  console.error(`Failed to register discover success callback. Code: ${error.code}, message: ${error.message}`);
}
```

## on('deviceNameChange')

```TypeScript
on(type: 'deviceNameChange', callback: Callback<{ deviceName: string; }>): void
```

注册设备名称变更回调，以便在设备名称改变时通知应用程序。使用callback异步回调。

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**需要权限：** ohos.permission.DISTRIBUTED_DATASYNC

<!--Device-DeviceManager-on(type: 'deviceNameChange', callback: Callback<{ deviceName: string; }>): void--><!--Device-DeviceManager-on(type: 'deviceNameChange', callback: Callback<{ deviceName: string; }>): void-End-->

**系统能力：** SystemCapability.DistributedHardware.DeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'deviceNameChange' | 是 | 注册设备名称改变回调，以便在设备名称改变时通知应用程序，固定为deviceNameChange。 |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;{ deviceName: string; }&gt; | 是 |  |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter type;3. Parameter verification failed;4. The size of specified type is greater than 255. |

**示例：**

```TypeScript
import { distributedDeviceManager } from '@kit.DistributedServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

class DeviceNameChangeData {
  deviceName: string = '';
}

try {
  // 创建设备管理实例
  let dmInstance = distributedDeviceManager.createDeviceManager('ohos.samples.jsHelloWorld');
  // 注册设备名称变更回调
  dmInstance.on('deviceNameChange', (data: DeviceNameChangeData) => {
    console.info('deviceNameChange on:' + JSON.stringify(data));
  });
} catch (err) {
  let error: BusinessError = err as BusinessError;
  console.error(`Failed to register device name change callback. Code: ${error.code}, message: ${error.message}`);
}
```

## on('discoverFailure')

```TypeScript
on(type: 'discoverFailure', callback: Callback<{ reason: number; }>): void
```

注册设备发现失败回调监听。使用callback异步回调。

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**需要权限：** ohos.permission.DISTRIBUTED_DATASYNC

<!--Device-DeviceManager-on(type: 'discoverFailure', callback: Callback<{ reason: number; }>): void--><!--Device-DeviceManager-on(type: 'discoverFailure', callback: Callback<{ reason: number; }>): void-End-->

**系统能力：** SystemCapability.DistributedHardware.DeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'discoverFailure' | 是 | 注册设备发现失败回调，以便在发现周边设备失败时通知应用程序，固定为discoverFailure。 |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;{ reason: number; }&gt; | 是 |  |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter type;3. Parameter verification failed;4. The size of specified type is greater than 255. |

**示例：**

```TypeScript
import { distributedDeviceManager } from '@kit.DistributedServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

class DiscoverFailureData {
  reason: number = 0;
}

try {
  // 创建设备管理实例
  let dmInstance = distributedDeviceManager.createDeviceManager('ohos.samples.jsHelloWorld');
  // 注册设备发现失败回调
  dmInstance.on('discoverFailure', (data: DiscoverFailureData) => {
    console.info('discoverFailure on:' + JSON.stringify(data));
  });
} catch (err) {
  let error: BusinessError = err as BusinessError;
  console.error(`Failed to register discover failure callback. Code: ${error.code}, message: ${error.message}`);
}
```

## on('serviceDie')

```TypeScript
on(type: 'serviceDie', callback?: Callback<{}>): void
```

注册设备管理服务死亡回调，以便在服务死亡时通知应用程序。使用callback异步回调。

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**需要权限：** ohos.permission.DISTRIBUTED_DATASYNC

<!--Device-DeviceManager-on(type: 'serviceDie', callback?: Callback<{}>): void--><!--Device-DeviceManager-on(type: 'serviceDie', callback?: Callback<{}>): void-End-->

**系统能力：** SystemCapability.DistributedHardware.DeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'serviceDie' | 是 | 注册serviceDie回调，以便在devicemanager服务异常终止时通知应用程序，固定为serviceDie。 |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;{}&gt; | 否 |  |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter type;3. Parameter verification failed;4. The size of specified type is greater than 255. |

**示例：**

```TypeScript
import { distributedDeviceManager } from '@kit.DistributedServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  // 创建设备管理实例
  let dmInstance = distributedDeviceManager.createDeviceManager('ohos.samples.jsHelloWorld');
  // 注册设备管理服务死亡回调
  dmInstance.on('serviceDie', () => {
    console.info('serviceDie on');
  });
} catch (err) {
  let error: BusinessError = err as BusinessError;
  console.error(`Failed to register service die callback. Code: ${error.code}, message: ${error.message}`);
}
```

## onDeviceNameChange

```TypeScript
onDeviceNameChange(callback: Callback<DeviceNameChangeResult>): void
```

注册设备名称变更回调，以便在设备名称改变时通知应用程序。使用callback异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**需要权限：** ohos.permission.DISTRIBUTED_DATASYNC

<!--Device-DeviceManager-onDeviceNameChange(callback: Callback<DeviceNameChangeResult>): void--><!--Device-DeviceManager-onDeviceNameChange(callback: Callback<DeviceNameChangeResult>): void-End-->

**系统能力：** SystemCapability.DistributedHardware.DeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;DeviceNameChangeResult&gt; | 是 | 注册设备名称改变的回调方法。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed.The application does not have the permission required to call the API. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let dmInstance = distributedDeviceManager.createDeviceManager('ohos.samples.jsHelloWorld');
  dmInstance.onDeviceNameChange((data: distributedDeviceManager.DeviceNameChangeResult) => {
    console.info('deviceNameChange on:' + JSON.stringify(data));
  });
} catch (err) {
  let e: BusinessError = err as BusinessError;
  console.error(`deviceNameChange errCode: ${e.code}, errMessage: ${e.message}`);
}
```

## onDeviceStateChange

```TypeScript
onDeviceStateChange(callback: Callback<DeviceStateChangeResult>): void
```

注册设备状态回调，以便在设备状态发生变化时根据应用捆绑包名通知应用。使用callback异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**需要权限：** ohos.permission.DISTRIBUTED_DATASYNC

<!--Device-DeviceManager-onDeviceStateChange(callback: Callback<DeviceStateChangeResult>): void--><!--Device-DeviceManager-onDeviceStateChange(callback: Callback<DeviceStateChangeResult>): void-End-->

**系统能力：** SystemCapability.DistributedHardware.DeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;DeviceStateChangeResult&gt; | 是 | 指示要注册的设备状态回调，返回设备状态和设备信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let dmInstance = distributedDeviceManager.createDeviceManager('ohos.samples.jsHelloWorld');
  dmInstance.onDeviceStateChange((data: distributedDeviceManager.DeviceStateChangeResult) => {
    console.info('deviceStateChange on:' + JSON.stringify(data));
  });
} catch (err) {
  let e: BusinessError = err as BusinessError;
  console.error(`deviceStateChange errCode: ${e.code}, errMessage: ${e.message}`);
}
```

## onDiscoverFailure

```TypeScript
onDiscoverFailure(callback: Callback<DiscoveryFailureResult>): void
```

注册设备发现失败回调监听。使用callback异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**需要权限：** ohos.permission.DISTRIBUTED_DATASYNC

<!--Device-DeviceManager-onDiscoverFailure(callback: Callback<DiscoveryFailureResult>): void--><!--Device-DeviceManager-onDiscoverFailure(callback: Callback<DiscoveryFailureResult>): void-End-->

**系统能力：** SystemCapability.DistributedHardware.DeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;DiscoveryFailureResult&gt; | 是 | 注册设备发现失败的回调方法。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed.The application does not have the permission required to call the API. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let dmInstance = distributedDeviceManager.createDeviceManager('ohos.samples.jsHelloWorld');
  dmInstance.onDiscoverFailure((data: distributedDeviceManager.DiscoveryFailureResult) => {
    console.info('discoverFailure' + JSON.stringify(data));
  });
} catch (err) {
  let e: BusinessError = err as BusinessError;
  console.error(`discoverFailure errCode: ${e.code}, errMessage: ${e.message}`);
}
```

## onDiscoverSuccess

```TypeScript
onDiscoverSuccess(callback: Callback<DiscoverySuccessResult>): void
```

注册发现设备成功回调监听。使用callback异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**需要权限：** ohos.permission.DISTRIBUTED_DATASYNC

<!--Device-DeviceManager-onDiscoverSuccess(callback: Callback<DiscoverySuccessResult>): void--><!--Device-DeviceManager-onDiscoverSuccess(callback: Callback<DiscoverySuccessResult>): void-End-->

**系统能力：** SystemCapability.DistributedHardware.DeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;DiscoverySuccessResult&gt; | 是 | 注册设备发现的回调方法。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed.The application does not have the permission required to call the API. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let dmInstance = distributedDeviceManager.createDeviceManager('ohos.samples.jsHelloWorld');
  dmInstance.onDiscoverSuccess((data: distributedDeviceManager.DiscoverySuccessResult) => {
    console.info('discoverSuccess:' + JSON.stringify(data));
  });
} catch (err) {
  let e: BusinessError = err as BusinessError;
  console.error(`discoverSuccess errCode: ${e.code}, errMessage: ${e.message}`);
}
```

## onServiceDie

```TypeScript
onServiceDie(callback: Callback<ServiceDieData>): void
```

注册设备管理服务死亡回调，以便在服务死亡时通知应用程序。使用callback异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**需要权限：** ohos.permission.DISTRIBUTED_DATASYNC

<!--Device-DeviceManager-onServiceDie(callback: Callback<ServiceDieData>): void--><!--Device-DeviceManager-onServiceDie(callback: Callback<ServiceDieData>): void-End-->

**系统能力：** SystemCapability.DistributedHardware.DeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;ServiceDieData&gt; | 是 | 注册serviceDie的回调方法。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed.The application does not have the permission required to call the API. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let dmInstance = distributedDeviceManager.createDeviceManager('ohos.samples.jsHelloWorld');
  dmInstance.onServiceDie((data: distributedDeviceManager.ServiceDieData) => {
    console.info('serviceDie on');
  });
} catch (err) {
  let e: BusinessError = err as BusinessError;
  console.error(`serviceDie errCode: ${e.code}, errMessage: ${e.message}`);
}
```

## startDiscovering

```TypeScript
startDiscovering(discoverParam: { [key: string]: Object; }, filterOptions?: { [key: string]: Object; }): void
```

发现周边设备。发现状态持续两分钟，超过两分钟，会停止发现，最大发现数量99个。wifi场景要求同局域网。

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**需要权限：** ohos.permission.DISTRIBUTED_DATASYNC

<!--Device-DeviceManager-startDiscovering(discoverParam: { [key: string]: Object; }, filterOptions?: { [key: string]: Object; }): void--><!--Device-DeviceManager-startDiscovering(discoverParam: { [key: string]: Object; }, filterOptions?: { [key: string]: Object; }): void-End-->

**系统能力：** SystemCapability.DistributedHardware.DeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| discoverParam | { [key: string]: Object; } | 是 | 发现标识。 标识发现的目标类型。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_discoverTargetType: 发现目标默认为设备，值为1。 |
| filterOptions | { [key: string]: Object; } | 否 | 发现设备过滤信息。可选，默认为undefined，发现未上线设备。会携带以下key值：\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_availableStatus(0-1)：仅发现设备可信，值为0表示设备不可信。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_1\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_-0：设备离线，客户端需要通过调用bindTarget绑定设备。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_2\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_-1：设备已在线，客户端可以进行连接。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_3\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_discoverDistance(0-100)：发现距离本地一定距离内的设备，单位为cm。wifi场景不传该参数。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_4\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_authenticationStatus(0-1)：根据不同的认证状态发现设备：\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_5\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_-0：设备未认证。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_6\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_-1：设备已认证。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_7\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_authorizationType(0-2)：根据不同的授权类型发现设备：\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_8\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_-0：根据临时协商的会话密钥认证的设备。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_9\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_-1：基于同账号密钥进行身份验证的设备。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_10\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_-2：基于不同账号凭据密钥认证的设备。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter type;3. Parameter verification failed. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [11600104](../../apis-distributedservice-kit/errorcode-device-manager.md#11600104-发现业务不可用) | Discovery unavailable. |
| [11600101](../../apis-distributedservice-kit/errorcode-device-manager.md#11600101-服务调用异常) | Failed to execute the function. |

**示例：**

```TypeScript
import { distributedDeviceManager } from '@kit.DistributedServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

// 发现标识，discoverTargetType为1表示发现目标为设备
let discoverParam: Record<string, number> = {
  'discoverTargetType': 1
};
// 发现设备过滤信息，availableStatus为0表示发现离线设备
let filterOptions: Record<string, number> = {
  'availableStatus': 0
};

try {
  // 创建设备管理实例
  let dmInstance = distributedDeviceManager.createDeviceManager('ohos.samples.jsHelloWorld');
  dmInstance.startDiscovering(discoverParam, filterOptions); // 当有设备发现时，通过discoverSuccess回调通知给应用
} catch (err) {
  let error: BusinessError = err as BusinessError;
  console.error(`Failed to start discovering. Code: ${error.code}, message: ${error.message}`);
}
```

## startDiscovering

```TypeScript
startDiscovering(discoverParam: Record<string, int | string>, filterOptions?: Record<string, int | string>): void
```

发现周边设备。发现状态持续两分钟，超过两分钟，会停止发现，最大发现数量99个。wifi场景要求同局域网。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**需要权限：** ohos.permission.DISTRIBUTED_DATASYNC

<!--Device-DeviceManager-startDiscovering(discoverParam: Record<string, int | string>, filterOptions?: Record<string, int | string>): void--><!--Device-DeviceManager-startDiscovering(discoverParam: Record<string, int | string>, filterOptions?: Record<string, int | string>): void-End-->

**系统能力：** SystemCapability.DistributedHardware.DeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| discoverParam | Record&lt;string, int \| string&gt; | 是 | 发现标识。 标识发现的目标类型。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_discoverTargetType: 发现目标默认为设备，值为1。 |
| filterOptions | Record&lt;string, int \| string&gt; | 否 | 发现设备过滤信息。可选，默认为undefined，发现未上线设备。会携带以下key值：\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_availableStatus(0-1)：仅发现设备可信，值为0表示设备不可信。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_1\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_-0：设备离线，客户端需要通过调用bindTarget绑定设备。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_2\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_-1：设备已在线，客户端可以进行连接。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_3\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_discoverDistance(0-100)：发现距离本地一定距离内的设备，单位为cm。wifi场景不传该参数。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_4\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_authenticationStatus(0-1)：根据不同的认证状态发现设备：\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_5\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_-0：设备未认证。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_6\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_-1：设备已认证。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_7\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_authorizationType(0-2)：根据不同的授权类型发现设备：\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_8\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_-0：根据临时协商的会话密钥认证的设备。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_9\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_-1：基于同账号密钥进行身份验证的设备。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_10\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_-2：基于不同账号凭据密钥认证的设备。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [11600104](../../apis-distributedservice-kit/errorcode-device-manager.md#11600104-发现业务不可用) | Discovery unavailable. |
| [11600101](../../apis-distributedservice-kit/errorcode-device-manager.md#11600101-服务调用异常) | Failed to execute the function. |

## stopDiscovering

```TypeScript
stopDiscovering(): void
```

停止发现周边设备。

**起始版本：** 10

**ArkTS模式：** ArkTS-Dyn起始版本为10；ArkTS-Sta起始版本为23。

**需要权限：** ohos.permission.DISTRIBUTED_DATASYNC

<!--Device-DeviceManager-stopDiscovering(): void--><!--Device-DeviceManager-stopDiscovering(): void-End-->

**系统能力：** SystemCapability.DistributedHardware.DeviceManager

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [11600101](../../apis-distributedservice-kit/errorcode-device-manager.md#11600101-服务调用异常) | Failed to execute the function. |

**示例：**

```TypeScript
import { distributedDeviceManager } from '@kit.DistributedServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  // 创建设备管理实例
  let dmInstance = distributedDeviceManager.createDeviceManager('ohos.samples.jsHelloWorld');
  // 停止发现周边设备
  dmInstance.stopDiscovering();
} catch (err) {
  let error: BusinessError = err as BusinessError;
  console.error(`Failed to stop discovering. Code: ${error.code}, message: ${error.message}`);
}
```

## unbindTarget

```TypeScript
unbindTarget(deviceId: string): void
```

解除认证设备。

**起始版本：** 10

**ArkTS模式：** ArkTS-Dyn起始版本为10；ArkTS-Sta起始版本为23。

**需要权限：** ohos.permission.DISTRIBUTED_DATASYNC

<!--Device-DeviceManager-unbindTarget(deviceId: string): void--><!--Device-DeviceManager-unbindTarget(deviceId: string): void-End-->

**系统能力：** SystemCapability.DistributedHardware.DeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| deviceId | string | 是 | 设备标识。长度范围1~255字符。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter type;3. Parameter verification failed;4. The size of specified deviceId is greater than 255. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [11600101](../../apis-distributedservice-kit/errorcode-device-manager.md#11600101-服务调用异常) | Failed to execute the function. |

**示例：**

```TypeScript
import { distributedDeviceManager } from '@kit.DistributedServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  // 设备标识，可以从发现的结果（startDiscovering的discoverSuccess回调）或可信设备列表（getAvailableDeviceListSync/getAvailableDeviceList返回的DeviceBasicInfo）中获取
  let deviceId = 'XXXXXXXX';
  // 创建设备管理实例
  let dmInstance = distributedDeviceManager.createDeviceManager('ohos.samples.jsHelloWorld');
  // 解除认证设备
  dmInstance.unbindTarget(deviceId);
} catch (err) {
  let error: BusinessError = err as BusinessError;
  console.error(`Failed to unbind target. Code: ${error.code}, message: ${error.message}`);
}
```

