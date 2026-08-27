# DeviceManager

设备管理实例，是分布式设备管理方法的调用入口，提供设备发现、设备认证、状态监听和信息查询等能力。 在调用DeviceManager的方法前，需要先通过createDeviceManager构建一个DeviceManager实例dmInstance。

**起始版本：** 10

**系统能力：** SystemCapability.DistributedHardware.DeviceManager

## 导入模块

```TypeScript
import { distributedDeviceManager } from '@kit.DistributedServiceKit';
```

## bindTarget

```TypeScript
bindTarget(deviceId: string, bindParam: { [key: string]: Object; }, callback: AsyncCallback<{deviceId: string;}>): void
```

认证设备，将发现的不可信设备通过认证流程绑定为可信设备。认证过程中，系统会根据bindParam中指定的认证类型发起认证请求， 认证成功后设备将加入可信设备列表，可通过getAvailableDeviceListSync查询。当不再需要与目标设备进行分布式业务时， 可调用unbindTarget解除绑定。使用callback异步回调。

**起始版本：** 10

**需要权限：** ohos.permission.DISTRIBUTED_DATASYNC

**系统能力：** SystemCapability.DistributedHardware.DeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| deviceId | string | 是 | 设备标识，可从设备发现结果（startDiscovering的discoverSuccess回调返回的 DeviceBasicInfo）中获取。长度范围1~255字符，超出范围时返回错误码401。 |
| bindParam | { [key: string]: Object; } | 是 | 认证参数。由开发者自行决定传入的键值对。默认会携带以下key值： bindType 此值是绑定的类型，必填。    -1：PIN码。    targetPkgName 绑定目标的包名。 appName 尝试绑定目标的应用程序名称。 appOperation 应用程序要绑定目标的原因。 customDescription 操作的详细说明。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;{deviceId: string;}&gt; | 是 | 认证结果回调。当认证成功时， err为undefined，data为包含deviceId的对象；当认证失败时，err为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter type; 3. Parameter verification failed; 4. The size of specified deviceId is greater than 255. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [11600101](../errorcode-device-manager.md#11600101-服务调用异常) | Failed to execute the function. |
| [11600103](../errorcode-device-manager.md#11600103-认证业务不可用) | Authentication unavailable. |

**示例**

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

## getAvailableDeviceList

```TypeScript
getAvailableDeviceList(callback: AsyncCallback<Array<DeviceBasicInfo>>): void
```

获取所有在线可信设备。调用前需先通过createDeviceManager创建DeviceManager实例。使用callback异步回调。 与getAvailableDeviceListSync的区别在于：本方法为异步调用，通过callback返回结果；getAvailableDeviceListSync为同步调用， 直接返回结果。建议在不希望阻塞线程的场景使用本方法，在需要阻塞等待结果的场景使用getAvailableDeviceListSync。

**起始版本：** 10

**需要权限：** ohos.permission.DISTRIBUTED_DATASYNC

**系统能力：** SystemCapability.DistributedHardware.DeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;Array&lt;[DeviceBasicInfo](arkts-distributedservice-distributeddevicemanager-devicebasicinfo-i.md)&gt;&gt; | 是 | 回调函数。当获取可信设备列表成功时，err为undefined， data为获取到的可信设备列表；失败时，err为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [11600101](../errorcode-device-manager.md#11600101-服务调用异常) | Failed to execute the function. |

**示例**

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

获取所有在线可信设备。调用前需先通过createDeviceManager创建DeviceManager实例。使用Promise异步回调。 与getAvailableDeviceListSync的区别在于：本方法为异步调用，通过Promise返回结果；getAvailableDeviceListSync为同步调用， 直接返回结果。建议在不希望阻塞线程的场景使用本方法，在需要阻塞等待结果的场景使用getAvailableDeviceListSync。

**起始版本：** 10

**需要权限：** ohos.permission.DISTRIBUTED_DATASYNC

**系统能力：** SystemCapability.DistributedHardware.DeviceManager

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;[DeviceBasicInfo](arkts-distributedservice-distributeddevicemanager-devicebasicinfo-i.md)&gt;&gt; | Promise对象，resolve时返回分布式设备基本信息列表，reject时返回错误信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [11600101](../errorcode-device-manager.md#11600101-服务调用异常) | Failed to execute the function. |

**示例**

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

同步获取所有在线可信设备。调用前需先通过createDeviceManager创建DeviceManager实例。 与getAvailableDeviceList的区别在于：本方法为同步调用，直接返回结果；getAvailableDeviceList为异步调用，通过callback 或Promise返回结果。建议在需要阻塞等待结果的场景使用本方法，在不希望阻塞线程的场景使用getAvailableDeviceList。

**起始版本：** 10

**需要权限：** ohos.permission.DISTRIBUTED_DATASYNC

**系统能力：** SystemCapability.DistributedHardware.DeviceManager

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;[DeviceBasicInfo](arkts-distributedservice-distributeddevicemanager-devicebasicinfo-i.md)&gt; | 返回可信设备列表，包含设备标识、名称、类型和网络标识等信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [11600101](../errorcode-device-manager.md#11600101-服务调用异常) | Failed to execute the function. |

**示例**

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

**需要权限：** ohos.permission.DISTRIBUTED_DATASYNC

**系统能力：** SystemCapability.DistributedHardware.DeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| networkId | string | 是 | 设备的网络标识，可从可信设备列表（getAvailableDeviceListSync或 getAvailableDeviceList返回的DeviceBasicInfo）中获取。注意：若获取到的networkId为空字符串，不可用于本接口调用。 长度范围1~255字符，超出范围时返回错误码401。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 返回指定设备名称，可用于设备的展示与识别。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter type; 3. Parameter verification failed; 4. The size of specified networkId is greater than 255. |
| [11600101](../errorcode-device-manager.md#11600101-服务调用异常) | Failed to execute the function. |

**示例**

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

```TypeScript
getDeviceType(networkId: string): number
```

通过指定设备的网络标识获取该设备类型。

**起始版本：** 10

**需要权限：** ohos.permission.DISTRIBUTED_DATASYNC

**系统能力：** SystemCapability.DistributedHardware.DeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| networkId | string | 是 | 设备的网络标识，可从可信设备列表（getAvailableDeviceListSync或 getAvailableDeviceList返回的DeviceBasicInfo）中获取。注意：若获取到的networkId为空字符串，不可用于本接口调用。 长度范围1~255字符，超出范围时返回错误码401。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | <!--RP2-->返回指定设备类型。<!--RP2End--> |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter type; 3. Parameter verification failed; 4. The size of specified networkId is greater than 255. |
| [11600101](../errorcode-device-manager.md#11600101-服务调用异常) | Failed to execute the function. |

**示例**

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

**需要权限：** ohos.permission.DISTRIBUTED_DATASYNC

**系统能力：** SystemCapability.DistributedHardware.DeviceManager

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 返回本地设备ID，实际值为udid-hash与appid和盐值基于sha256方式进行混淆后的值。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [11600101](../errorcode-device-manager.md#11600101-服务调用异常) | Failed to execute the function. |

**示例**

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

**需要权限：** ohos.permission.DISTRIBUTED_DATASYNC

**系统能力：** SystemCapability.DistributedHardware.DeviceManager

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 返回本地设备名称，可用于设备的展示与识别。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [11600101](../errorcode-device-manager.md#11600101-服务调用异常) | Failed to execute the function. |

**示例**

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

**需要权限：** ohos.permission.DISTRIBUTED_DATASYNC

**系统能力：** SystemCapability.DistributedHardware.DeviceManager

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 返回本地设备网络标识，即设备在分布式网络中的唯一标识字符串。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [11600101](../errorcode-device-manager.md#11600101-服务调用异常) | Failed to execute the function. |

**示例**

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

```TypeScript
getLocalDeviceType(): number
```

获取本地设备类型。

**起始版本：** 10

**需要权限：** ohos.permission.DISTRIBUTED_DATASYNC

**系统能力：** SystemCapability.DistributedHardware.DeviceManager

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | <!--RP1-->返回本地设备类型。<!--RP1End--> |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [11600101](../errorcode-device-manager.md#11600101-服务调用异常) | Failed to execute the function. |

**示例**

```TypeScript
import { distributedDeviceManager } from '@kit.DistributedServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  // 创建设备管理实例
  let dmInstance = distributedDeviceManager.createDeviceManager('ohos.samples.jsHelloWorld');
  // 获取本地设备类型
  let deviceType: number = dmInstance.getLocalDeviceType();
  console.info('local device type: ' + JSON.stringify(deviceType));
} catch (err) {
  let error: BusinessError = err as BusinessError;
  console.error(`Failed to get local device type. Code: ${error.code}, message: ${error.message}`);
}
```

## off('deviceStateChange')

```TypeScript
off(type: 'deviceStateChange', callback?: Callback<{ action: DeviceStateChange; device: DeviceBasicInfo; }>): void
```

取消注册设备状态回调。使用callback异步回调。

**起始版本：** 10

**需要权限：** ohos.permission.DISTRIBUTED_DATASYNC

**系统能力：** SystemCapability.DistributedHardware.DeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'deviceStateChange' | 是 | 取消注册设备状态回调，固定为deviceStateChange。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;{ action: DeviceStateChange; device: DeviceBasicInfo; }&gt; | 否 |  |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter type; 3. Parameter verification failed; 4. The size of specified type is greater than 255. |

**示例**

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

**需要权限：** ohos.permission.DISTRIBUTED_DATASYNC

**系统能力：** SystemCapability.DistributedHardware.DeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'discoverSuccess' | 是 | 取消注册设备发现回调，固定为discoverSuccess。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;{ device: DeviceBasicInfo; }&gt; | 否 |  |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter type; 3. Parameter verification failed; 4. The size of specified type is greater than 255. |

**示例**

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

**需要权限：** ohos.permission.DISTRIBUTED_DATASYNC

**系统能力：** SystemCapability.DistributedHardware.DeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'deviceNameChange' | 是 | 取消注册设备名称改变回调，固定为deviceNameChange。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;{ deviceName: string; }&gt; | 否 |  |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter type; 3. Parameter verification failed; 4. The size of specified type is greater than 255. |

**示例**

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
off(type: 'discoverFailure', callback?: Callback<{ reason: number; }>): void
```

取消注册设备发现失败回调。使用callback异步回调。

**起始版本：** 10

**需要权限：** ohos.permission.DISTRIBUTED_DATASYNC

**系统能力：** SystemCapability.DistributedHardware.DeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'discoverFailure' | 是 | 取消注册设备发现失败回调，固定为discoverFailure。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;{ reason: number; }&gt; | 否 |  |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter type; 3. Parameter verification failed; 4. The size of specified type is greater than 255. |

**示例**

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

**需要权限：** ohos.permission.DISTRIBUTED_DATASYNC

**系统能力：** SystemCapability.DistributedHardware.DeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'serviceDie' | 是 | 取消注册serviceDie回调，固定为serviceDie。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;{}&gt; | 否 |  |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter type; 3. Parameter verification failed; 4. The size of specified type is greater than 255. |

**示例**

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

## on('deviceStateChange')

```TypeScript
on(type: 'deviceStateChange', callback: Callback<{ action: DeviceStateChange; device: DeviceBasicInfo; }>): void
```

注册设备状态回调，以便在设备状态发生变化时通知应用。使用callback异步回调。

**起始版本：** 10

**需要权限：** ohos.permission.DISTRIBUTED_DATASYNC

**系统能力：** SystemCapability.DistributedHardware.DeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'deviceStateChange' | 是 | 注册设备状态回调，固定为deviceStateChange。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;{ action: DeviceStateChange; device: DeviceBasicInfo; }&gt; | 是 |  |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter type; 3. Parameter verification failed; 4. The size of specified type is greater than 255. |

**示例**

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

注册发现设备成功回调。使用callback异步回调。此回调在调用startDiscovering发现到周边设备时触发， 返回发现的设备信息（DeviceBasicInfo）。需在调用startDiscovering之前注册此回调。

**起始版本：** 10

**需要权限：** ohos.permission.DISTRIBUTED_DATASYNC

**系统能力：** SystemCapability.DistributedHardware.DeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'discoverSuccess' | 是 | 注册设备发现回调，以便在发现周边设备时通知应用程序，固定为discoverSuccess。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;{ device: DeviceBasicInfo; }&gt; | 是 |  |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter type; 3. Parameter verification failed; 4. The size of specified type is greater than 255. |

**示例**

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

注册设备名称变更回调，以便在设备名称改变时通知应用。使用callback异步回调。

**起始版本：** 10

**需要权限：** ohos.permission.DISTRIBUTED_DATASYNC

**系统能力：** SystemCapability.DistributedHardware.DeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'deviceNameChange' | 是 | 注册设备名称改变回调，以便在设备名称改变时通知应用程序，固定为deviceNameChange。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;{ deviceName: string; }&gt; | 是 |  |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter type; 3. Parameter verification failed; 4. The size of specified type is greater than 255. |

**示例**

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

注册设备发现失败回调。使用callback异步回调。此回调在调用startDiscovering发现设备失败时触发， 返回失败原因。需在调用startDiscovering之前注册此回调。

**起始版本：** 10

**需要权限：** ohos.permission.DISTRIBUTED_DATASYNC

**系统能力：** SystemCapability.DistributedHardware.DeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'discoverFailure' | 是 | 注册设备发现失败回调，以便在发现周边设备失败时通知应用程序，固定为discoverFailure。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;{ reason: number; }&gt; | 是 |  |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter type; 3. Parameter verification failed; 4. The size of specified type is greater than 255. |

**示例**

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

注册设备管理服务死亡回调，以便在服务死亡时通知应用。使用callback异步回调。

**起始版本：** 10

**需要权限：** ohos.permission.DISTRIBUTED_DATASYNC

**系统能力：** SystemCapability.DistributedHardware.DeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'serviceDie' | 是 | 注册serviceDie回调，以便在devicemanager服务异常终止时通知应用程序，固定为serviceDie。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;{}&gt; | 否 |  |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter type; 3. Parameter verification failed; 4. The size of specified type is greater than 255. |

**示例**

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

## startDiscovering

```TypeScript
startDiscovering(discoverParam: { [key: string]: Object; }, filterOptions?: { [key: string]: Object; }): void
```

发现周边设备，用于在需要建立分布式连接前搜索可用设备。发现状态持续两分钟，超时后自动停止，最大发现数量为99个。使用WiFi进行 设备发现时，要求发现方与被发现方处于同一局域网内。调用本方法前，需先通过on('discoverSuccess')注册设备发现成功回调以接收 发现的设备信息，并通过on('discoverFailure')注册设备发现失败回调以接收失败通知。发现完成后可调用stopDiscovering停止发现。

**起始版本：** 10

**需要权限：** ohos.permission.DISTRIBUTED_DATASYNC

**系统能力：** SystemCapability.DistributedHardware.DeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| discoverParam | { [key: string]: Object; } | 是 | 发现标识。 标识发现的目标类型。 discoverTargetType: 发现目标默认为设备，值为1。 |
| filterOptions | { [key: string]: Object; } | 否 | 发现设备过滤信息。可选，默认为undefined，发现未上线设备。会携带以下key值： availableStatus(0-1)：仅发现设备可信，值为0表示设备不可信。    -0：设备离线，客户端需要通过调用bindTarget绑定设备。    -1：设备已在线，客户端可以进行连接。    discoverDistance(0-100)：发现距离本地一定距离内的设备，单位为cm。wifi场景不传该参数。 authenticationStatus(0-1)：根据不同的认证状态发现设备：    -0：设备未认证。    -1：设备已认证。    authorizationType(0-2)：根据不同的授权类型发现设备：    -0：根据临时协商的会话密钥认证的设备。    -1：基于同账号密钥进行身份验证的设备。    -2：基于不同账号凭据密钥认证的设备。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter type; 3. Parameter verification failed. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [11600104](../errorcode-device-manager.md#11600104-发现业务不可用) | Discovery unavailable. |
| [11600101](../errorcode-device-manager.md#11600101-服务调用异常) | Failed to execute the function. |

**示例**

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

## stopDiscovering

```TypeScript
stopDiscovering(): void
```

停止发现周边设备。与startDiscovering方法配合使用，用于在发现超时（两分钟）前手动停止设备发现。 需在调用startDiscovering之后调用。

**起始版本：** 10

**需要权限：** ohos.permission.DISTRIBUTED_DATASYNC

**系统能力：** SystemCapability.DistributedHardware.DeviceManager

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [11600101](../errorcode-device-manager.md#11600101-服务调用异常) | Failed to execute the function. |

**示例**

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

解除认证设备，用于在不再需要与目标设备进行分布式业务时，解除与该设备的认证关系。与bindTarget方法配合使用， 仅能解除已通过bindTarget认证绑定的可信设备。解除后设备将从可信设备列表中移除， 可通过getAvailableDeviceListSync或getAvailableDeviceList查询确认。

**起始版本：** 10

**需要权限：** ohos.permission.DISTRIBUTED_DATASYNC

**系统能力：** SystemCapability.DistributedHardware.DeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| deviceId | string | 是 | 设备标识，仅支持已通过bindTarget认证绑定的可信设备，可从可信设备列表 （getAvailableDeviceListSync或getAvailableDeviceList返回的DeviceBasicInfo）中获取。 长度范围1~255字符，超出范围时返回错误码401。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter type; 3. Parameter verification failed; 4. The size of specified deviceId is greater than 255. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [11600101](../errorcode-device-manager.md#11600101-服务调用异常) | Failed to execute the function. |

**示例**

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
