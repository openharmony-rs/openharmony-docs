# DeviceManager

设备管理实例，用于获取可信设备和本地设备的相关信息。在调用DeviceManager的方法前，需要先通过createDeviceManager构建一个DeviceManager实例dmInstance。

**起始版本：** 7

**废弃版本：** 11

**替代接口：** [DeviceManager](arkts-distributedservice-distributeddevicemanager-devicemanager-i.md)

**系统能力：** SystemCapability.DistributedHardware.DeviceManager

## 导入模块

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

认证设备。

**起始版本：** 7

**废弃版本：** 11

**替代接口：** [bindTarget](arkts-distributedservice-distributeddevicemanager-devicemanager-i.md#bindtarget)(deviceId: string, bindParam: { [key: string]: Object; }, callback: AsyncCallback&lt;{deviceId: string;}&gt;)

**需要权限：** ohos.permission.ACCESS_SERVICE_DM

**系统能力：** SystemCapability.DistributedHardware.DeviceManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| deviceInfo | [DeviceInfo](arkts-distributedservice-devicemanager-deviceinfo-i-sys.md) | 是 | 设备信息。 |
| authParam | [AuthParam](arkts-distributedservice-devicemanager-authparam-i-sys.md) | 是 | 认证参数。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;{ deviceId: string, pinToken?: number }&gt; | 是 | 认证结果回调。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter type; 3. Parameter verification failed. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |

**示例**

```TypeScript
示例中的初始化请参见deviceManager.createDeviceManager。
```

## deleteCredential

```TypeScript
deleteCredential(queryInfo: string, callback: AsyncCallback<{ resultInfo: string }>): void
```

删除凭据信息。

**起始版本：** 10

**废弃版本：** 11

**需要权限：** ohos.permission.ACCESS_SERVICE_DM

**系统能力：** SystemCapability.DistributedHardware.DeviceManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| queryInfo | string | 是 | 删除凭据信息。长度范围1~64000字符。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;{ resultInfo: string }&gt; | 是 | 删除凭据结果回调。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter type; 3. Parameter verification failed; 4. The size of specified queryInfo is greater than 5999. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |

**示例**

```TypeScript
示例中的初始化请参见deviceManager.createDeviceManager。
```

## getDeviceInfo

```TypeScript
getDeviceInfo(networkId: string, callback: AsyncCallback<DeviceInfo>): void
```

通过指定设备的网络标识获取该设备的信息。使用callback异步回调。

**起始版本：** 10

**废弃版本：** 11

**替代接口：** [getDeviceName](arkts-distributedservice-distributeddevicemanager-devicemanager-i.md#getdevicename)

**需要权限：** ohos.permission.ACCESS_SERVICE_DM

**系统能力：** SystemCapability.DistributedHardware.DeviceManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| networkId | string | 是 | 设备的网络标识。长度范围1~255字符。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[DeviceInfo](arkts-distributedservice-devicemanager-deviceinfo-i-sys.md)&gt; | 是 | 获取指定设备信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter type; 3. Parameter verification failed; 4. The size of specified networkId is greater than 255. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |

**示例**

```TypeScript
示例中的初始化请参见deviceManager.createDeviceManager。
```

## getDeviceInfo

```TypeScript
getDeviceInfo(networkId: string): Promise<DeviceInfo>
```

通过指定设备的网络标识获取该设备的信息。使用Promise异步回调。

**起始版本：** 10

**废弃版本：** 11

**替代接口：** [getDeviceName](arkts-distributedservice-distributeddevicemanager-devicemanager-i.md#getdevicename)

**需要权限：** ohos.permission.ACCESS_SERVICE_DM

**系统能力：** SystemCapability.DistributedHardware.DeviceManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| networkId | string | 是 | 设备的网络标识。长度范围1~255字符。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[DeviceInfo](arkts-distributedservice-devicemanager-deviceinfo-i-sys.md)&gt; | Promise实例，用于获取异步返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter type; 3. Parameter verification failed; 4. The size of specified networkId is greater than 255. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |

**示例**

参见 [getDeviceInfo](#getdeviceinfo)

## getLocalDeviceInfo

```TypeScript
getLocalDeviceInfo(callback: AsyncCallback<DeviceInfo>): void
```

获取本地设备信息。使用callback异步回调。

**起始版本：** 8

**废弃版本：** 11

**替代接口：** [getLocalDeviceNetworkId](arkts-distributedservice-distributeddevicemanager-devicemanager-i.md#getlocaldevicenetworkid)

**需要权限：** ohos.permission.ACCESS_SERVICE_DM

**系统能力：** SystemCapability.DistributedHardware.DeviceManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[DeviceInfo](arkts-distributedservice-devicemanager-deviceinfo-i-sys.md)&gt; | 是 | 获取本地设备信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter type; 3. Parameter verification failed. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |

**示例**

```TypeScript
示例中的初始化请参见deviceManager.createDeviceManager。
```

## getLocalDeviceInfo

```TypeScript
getLocalDeviceInfo(): Promise<DeviceInfo>
```

获取本地设备信息。使用Promise异步回调。

**起始版本：** 8

**废弃版本：** 11

**替代接口：** [getLocalDeviceNetworkId](arkts-distributedservice-distributeddevicemanager-devicemanager-i.md#getlocaldevicenetworkid)

**需要权限：** ohos.permission.ACCESS_SERVICE_DM

**系统能力：** SystemCapability.DistributedHardware.DeviceManager

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[DeviceInfo](arkts-distributedservice-devicemanager-deviceinfo-i-sys.md)&gt; | Promise实例，用于获取异步返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |

**示例**

参见 [getLocalDeviceInfo](#getlocaldeviceinfo)

## getLocalDeviceInfoSync

```TypeScript
getLocalDeviceInfoSync(): DeviceInfo
```

同步获取本地设备信息。

**起始版本：** 8

**废弃版本：** 11

**替代接口：** [getLocalDeviceNetworkId](arkts-distributedservice-distributeddevicemanager-devicemanager-i.md#getlocaldevicenetworkid)

**需要权限：** ohos.permission.ACCESS_SERVICE_DM

**系统能力：** SystemCapability.DistributedHardware.DeviceManager

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [DeviceInfo](arkts-distributedservice-devicemanager-deviceinfo-i-sys.md) | 返回本地设备列表。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [11600101](../errorcode-device-manager.md#11600101-服务调用异常) | Failed to execute the function. |

**示例**

```TypeScript
示例中的初始化请参见deviceManager.createDeviceManager。
```

## getTrustedDeviceList

```TypeScript
getTrustedDeviceList(callback: AsyncCallback<Array<DeviceInfo>>): void
```

获取所有可信设备列表。使用callback异步回调。

**起始版本：** 8

**废弃版本：** 11

**替代接口：** [getAvailableDeviceList](arkts-distributedservice-distributeddevicemanager-devicemanager-i.md#getavailabledevicelist)(callback: AsyncCallback&lt;Array&lt;DeviceBasicInfo&gt;&gt;)

**需要权限：** ohos.permission.ACCESS_SERVICE_DM

**系统能力：** SystemCapability.DistributedHardware.DeviceManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;Array&lt;[DeviceInfo](arkts-distributedservice-devicemanager-deviceinfo-i-sys.md)&gt;&gt; | 是 | 获取所有可信设备列表的回调，返回设备信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter type; 3. Parameter verification failed. |

**示例**

```TypeScript
示例中的初始化请参见deviceManager.createDeviceManager。
```

## getTrustedDeviceList

```TypeScript
getTrustedDeviceList(): Promise<Array<DeviceInfo>>
```

获取所有可信设备列表。使用Promise异步回调。

**起始版本：** 8

**废弃版本：** 11

**替代接口：** [getAvailableDeviceList](arkts-distributedservice-distributeddevicemanager-devicemanager-i.md#getavailabledevicelist)()

**需要权限：** ohos.permission.ACCESS_SERVICE_DM

**系统能力：** SystemCapability.DistributedHardware.DeviceManager

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;[DeviceInfo](arkts-distributedservice-devicemanager-deviceinfo-i-sys.md)&gt;&gt; | Promise实例，用于获取异步返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |

**示例**

参见 [getTrustedDeviceList](#gettrusteddevicelist)

## getTrustedDeviceListSync

```TypeScript
getTrustedDeviceListSync(): Array<DeviceInfo>
```

同步获取所有可信设备列表。

**起始版本：** 7

**废弃版本：** 11

**替代接口：** [getAvailableDeviceListSync](arkts-distributedservice-distributeddevicemanager-devicemanager-i.md#getavailabledevicelistsync)

**需要权限：** ohos.permission.ACCESS_SERVICE_DM

**系统能力：** SystemCapability.DistributedHardware.DeviceManager

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;[DeviceInfo](arkts-distributedservice-devicemanager-deviceinfo-i-sys.md)&gt; | 返回可信设备列表。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [11600101](../errorcode-device-manager.md#11600101-服务调用异常) | Failed to execute the function. |

**示例**

```TypeScript
示例中的初始化请参见deviceManager.createDeviceManager。
```

## getTrustedDeviceListSync

```TypeScript
getTrustedDeviceListSync(isRefresh: boolean): Array<DeviceInfo>
```

打开软总线系统端的心跳模式，让周围处于下线状态的可信设备快速上线，同时刷新已上线的可信设备列表。

**起始版本：** 10

**废弃版本：** 11

**需要权限：** ohos.permission.ACCESS_SERVICE_DM

**系统能力：** SystemCapability.DistributedHardware.DeviceManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| isRefresh | boolean | 是 | 是否打开心跳模式，刷新可信列表，true表示打开心跳模式，false表示关闭心跳模式。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;[DeviceInfo](arkts-distributedservice-devicemanager-deviceinfo-i-sys.md)&gt; | 返回可信设备列表。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter type; 3. Parameter verification failed. |
| [11600101](../errorcode-device-manager.md#11600101-服务调用异常) | Failed to execute the function. |

**示例**

参见 [getTrustedDeviceListSync](#gettrusteddevicelistsync)

## importCredential

```TypeScript
importCredential(credentialInfo: string, callback: AsyncCallback<{ resultInfo: string }>): void
```

导入凭据信息。

**起始版本：** 10

**废弃版本：** 11

**需要权限：** ohos.permission.ACCESS_SERVICE_DM

**系统能力：** SystemCapability.DistributedHardware.DeviceManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| credentialInfo | string | 是 | 导入凭据信息。长度范围1~64000字符。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;{ resultInfo: string }&gt; | 是 | 导入凭据结果回调。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter type; 3. Parameter verification failed; 4. The size of specified credentialInfo is greater than 5999. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |

**示例**

```TypeScript
示例中的初始化请参见deviceManager.createDeviceManager。
```

## off('uiStateChange')

```TypeScript
off(type: 'uiStateChange', callback?: Callback<{ param: string }>): void
```

取消ui状态变更回调。

**起始版本：** 9

**废弃版本：** 11

**替代接口：** off(type: 'replyResult', callback: Callback&lt;{ param: string; }&gt;)

**需要权限：** ohos.permission.ACCESS_SERVICE_DM

**系统能力：** SystemCapability.DistributedHardware.DeviceManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'uiStateChange' | 是 | 取消注册的设备管理器 ui 状态回调，固定为uiStateChange。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;{ param: string }&gt; | 否 | 指示要取消注册的设备管理器 ui 状态，返回UI状态。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter type; 3. Parameter verification failed; 4. The size of specified eventType is greater than 255. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |

## off('deviceStateChange')

```TypeScript
off(type: 'deviceStateChange', callback?: Callback<{ action: DeviceStateChangeAction, device: DeviceInfo }>): void
```

取消注册设备状态回调。

**起始版本：** 7

**废弃版本：** 11

**替代接口：** [off](arkts-distributedservice-distributeddevicemanager-devicemanager-i.md#offdevicestatechange)(type: 'deviceStateChange', callback?: Callback&lt;{ action: DeviceStateChange; device: DeviceBasicInfo; }&gt;)

**需要权限：** ohos.permission.ACCESS_SERVICE_DM

**系统能力：** SystemCapability.DistributedHardware.DeviceManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'deviceStateChange' | 是 | 根据应用程序的包名取消注册设备状态回调，固定为deviceStateChange。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;{ action: DeviceStateChangeAction, device: DeviceInfo }&gt; | 否 | 指示要取消注册的设备状态回调，返回设备状态和设备信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter type; 3. Parameter verification failed; 4. The size of specified eventType is greater than 255. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |

## off('deviceFound')

```TypeScript
off(type: 'deviceFound', callback?: Callback<{ subscribeId: number, device: DeviceInfo }>): void
```

取消注册设备发现回调。

**起始版本：** 7

**废弃版本：** 11

**替代接口：** off(type: 'discoverSuccess', callback: Callback&lt;{ device: DeviceBasicInfo; }&gt;)

**需要权限：** ohos.permission.ACCESS_SERVICE_DM

**系统能力：** SystemCapability.DistributedHardware.DeviceManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'deviceFound' | 是 | 取消注册设备发现回调，固定为deviceFound。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;{ subscribeId: number, device: DeviceInfo }&gt; | 否 | 指示要取消注册的设备发现回调，返回设备状态和设备信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter type; 3. Parameter verification failed; 4. The size of specified eventType is greater than 255. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |

## off('discoverFail')

```TypeScript
off(type: 'discoverFail', callback?: Callback<{ subscribeId: number, reason: number }>): void
```

取消注册设备发现失败回调。

**起始版本：** 7

**废弃版本：** 11

**替代接口：** off(type: 'discoverFailure', callback: Callback&lt;{ reason: number; }&gt;)

**需要权限：** ohos.permission.ACCESS_SERVICE_DM

**系统能力：** SystemCapability.DistributedHardware.DeviceManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'discoverFail' | 是 | 取消注册设备发现失败回调，固定为discoverFail。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;{ subscribeId: number, reason: number }&gt; | 否 | 指示要取消注册的设备发现失败回调。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter type; 3. Parameter verification failed; 4. The size of specified eventType is greater than 255. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |

## off('publishSuccess')

```TypeScript
off(type: 'publishSuccess', callback?: Callback<{ publishId: number }>): void
```

取消注册设备发布成功回调。

**起始版本：** 9

**废弃版本：** 11

**需要权限：** ohos.permission.ACCESS_SERVICE_DM

**系统能力：** SystemCapability.DistributedHardware.DeviceManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'publishSuccess' | 是 | 取消注册设备发布成功回调，固定为publishSuccess。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;{ publishId: number }&gt; | 否 | 指示要取消注册的设备发布成功回调。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter type; 3. Parameter verification failed; 4. The size of specified eventType is greater than 255. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |

## off('publishFail')

```TypeScript
off(type: 'publishFail', callback?: Callback<{ publishId: number, reason: number }>): void
```

取消注册设备发布失败回调。

**起始版本：** 9

**废弃版本：** 11

**需要权限：** ohos.permission.ACCESS_SERVICE_DM

**系统能力：** SystemCapability.DistributedHardware.DeviceManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'publishFail' | 是 | 取消注册设备发布失败回调，固定为publishFail。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;{ publishId: number, reason: number }&gt; | 否 | 指示要取消注册设备发布失败回调。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter type; 3. Parameter verification failed; 4. The size of specified eventType is greater than 255. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |

## off('serviceDie')

```TypeScript
off(type: 'serviceDie', callback?: () => void): void
```

取消注册设备管理服务死亡监听。

**起始版本：** 7

**废弃版本：** 11

**替代接口：** [off](arkts-distributedservice-distributeddevicemanager-devicemanager-i.md#offservicedie)(type: 'serviceDie', callback?: Callback&lt;{}&gt;)

**需要权限：** ohos.permission.ACCESS_SERVICE_DM

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
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter type; 3. Parameter verification failed; 4. The size of specified eventType is greater than 255. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |

## on('uiStateChange')

```TypeScript
on(type: 'uiStateChange', callback: Callback<{ param: string }>): void
```

ui状态变更回调。

**起始版本：** 9

**废弃版本：** 11

**替代接口：** [on](arkts-distributedservice-distributeddevicemanager-devicemanager-i-sys.md#onreplyresult)(type: 'replyResult', callback: Callback&lt;{ param: string; }&gt;)

**需要权限：** ohos.permission.ACCESS_SERVICE_DM

**系统能力：** SystemCapability.DistributedHardware.DeviceManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'uiStateChange' | 是 | 注册的设备管理器 ui 状态回调，以便在状态改变时通知应用，固定为uiStateChange。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;{ param: string }&gt; | 是 | 指示要注册的设备管理器 ui 状态回调，返回ui状态。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter type; 3. Parameter verification failed; 4. The size of specified eventType is greater than 255. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |

## on('deviceStateChange')

```TypeScript
on(type: 'deviceStateChange', callback: Callback<{ action: DeviceStateChangeAction, device: DeviceInfo }>): void
```

注册设备状态回调。

**起始版本：** 7

**废弃版本：** 11

**替代接口：** [on](arkts-distributedservice-distributeddevicemanager-devicemanager-i.md#ondevicestatechange)(type: 'deviceStateChange', callback: Callback&lt;{ action: DeviceStateChange; device: DeviceBasicInfo; }&gt;)

**需要权限：** ohos.permission.ACCESS_SERVICE_DM

**系统能力：** SystemCapability.DistributedHardware.DeviceManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'deviceStateChange' | 是 | 注册设备状态回调，固定为deviceStateChange。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;{ action: DeviceStateChangeAction, device: DeviceInfo }&gt; | 是 | 指示要注册的设备状态回调，返回设备状态和设备信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter type; 3. Parameter verification failed; 4. The size of specified eventType is greater than 255. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |

## on('deviceFound')

```TypeScript
on(type: 'deviceFound', callback: Callback<{ subscribeId: number, device: DeviceInfo }>): void
```

注册发现设备回调监听。

**起始版本：** 7

**废弃版本：** 11

**替代接口：** [on](arkts-distributedservice-distributeddevicemanager-devicemanager-i.md#ondiscoversuccess)(type: 'discoverSuccess', callback: Callback&lt;{ device: DeviceBasicInfo; }&gt;)

**需要权限：** ohos.permission.ACCESS_SERVICE_DM

**系统能力：** SystemCapability.DistributedHardware.DeviceManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'deviceFound' | 是 | 注册设备发现回调，以便在发现周边设备时通知应用程序，固定为deviceFound。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;{ subscribeId: number, device: DeviceInfo }&gt; | 是 | 注册设备发现的回调方法。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter type; 3. Parameter verification failed; 4. The size of specified eventType is greater than 255. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |

## on('discoverFail')

```TypeScript
on(type: 'discoverFail', callback: Callback<{ subscribeId: number, reason: number }>): void
```

注册设备发现失败回调监听。

**起始版本：** 7

**废弃版本：** 11

**替代接口：** [on](arkts-distributedservice-distributeddevicemanager-devicemanager-i.md#ondiscoverfailure)(type: 'discoverFailure', callback: Callback&lt;{ reason: number; }&gt;)

**需要权限：** ohos.permission.ACCESS_SERVICE_DM

**系统能力：** SystemCapability.DistributedHardware.DeviceManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'discoverFail' | 是 | 注册设备发现失败回调，以便在发现周边设备失败时通知应用程序，固定为discoverFail。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;{ subscribeId: number, reason: number }&gt; | 是 | 注册设备发现失败的回调方法。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter type; 3. Parameter verification failed; 4. The size of specified eventType is greater than 255. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |

## on('publishSuccess')

```TypeScript
on(type: 'publishSuccess', callback: Callback<{ publishId: number }>): void
```

注册发布设备发现回调监听。

**起始版本：** 9

**废弃版本：** 11

**需要权限：** ohos.permission.ACCESS_SERVICE_DM

**系统能力：** SystemCapability.DistributedHardware.DeviceManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'publishSuccess' | 是 | 注册发布设备成功回调，以便将发布成功时通知应用程序，固定为publishSuccess。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;{ publishId: number }&gt; | 是 | 注册设备发布成功的回调方法。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter type; 3. Parameter verification failed; 4. The size of specified eventType is greater than 255. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |

## on('publishFail')

```TypeScript
on(type: 'publishFail', callback: Callback<{ publishId: number, reason: number }>): void
```

注册设备发布失败回调监听。

**起始版本：** 9

**废弃版本：** 11

**需要权限：** ohos.permission.ACCESS_SERVICE_DM

**系统能力：** SystemCapability.DistributedHardware.DeviceManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'publishFail' | 是 | 注册设备发布失败回调，以便在发布设备失败时通知应用程序，固定为publishFail。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;{ publishId: number, reason: number }&gt; | 是 | 注册设备发布失败的回调方法。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter type; 3. Parameter verification failed; 4. The size of specified eventType is greater than 255. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |

## on('serviceDie')

```TypeScript
on(type: 'serviceDie', callback: () => void): void
```

注册设备管理服务死亡监听。

**起始版本：** 7

**废弃版本：** 11

**替代接口：** on(type: 'serviceDie', callback?: Callback&lt;{}&gt;)

**需要权限：** ohos.permission.ACCESS_SERVICE_DM

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
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter type; 3. Parameter verification failed; 4. The size of specified eventType is greater than 255. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |

## publishDeviceDiscovery

```TypeScript
publishDeviceDiscovery(publishInfo: PublishInfo): void
```

发布设备发现。发布状态持续两分钟，超过两分钟会停止发布。

**起始版本：** 9

**废弃版本：** 11

**需要权限：** ohos.permission.ACCESS_SERVICE_DM

**系统能力：** SystemCapability.DistributedHardware.DeviceManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| publishInfo | [PublishInfo](arkts-distributedservice-devicemanager-publishinfo-i-sys.md) | 是 | 发布设备发现信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter type; 3. Parameter verification failed. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [11600105](../errorcode-device-manager.md#11600105-发布业务不可用) | Publish unavailable. |
| [11600101](../errorcode-device-manager.md#11600101-服务调用异常) | Failed to execute the function. |

**示例**

```TypeScript
示例中的初始化请参见deviceManager.createDeviceManager。
```

## release

```TypeScript
release(): void
```

设备管理实例不再使用后，通过该方法释放DeviceManager实例。

**起始版本：** 7

**废弃版本：** 11

**替代接口：** [releaseDeviceManager](arkts-distributedservice-distributeddevicemanager-releasedevicemanager-f.md)

**需要权限：** ohos.permission.ACCESS_SERVICE_DM

**系统能力：** SystemCapability.DistributedHardware.DeviceManager

**系统接口：** 此接口为系统接口。

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [11600101](../errorcode-device-manager.md#11600101-服务调用异常) | Failed to execute the function. |

**示例**

```TypeScript
示例中的初始化请参见deviceManager.createDeviceManager。
```

## requestCredentialRegisterInfo

```TypeScript
requestCredentialRegisterInfo(requestInfo: string, callback: AsyncCallback<{ registerInfo: string }>): void
```

获取凭据的注册信息。

**起始版本：** 10

**废弃版本：** 11

**需要权限：** ohos.permission.ACCESS_SERVICE_DM

**系统能力：** SystemCapability.DistributedHardware.DeviceManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| requestInfo | string | 是 | 请求凭据信息。最大长度255字符。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;{ registerInfo: string }&gt; | 是 | 凭据的注册信息回调。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter type; 3. Parameter verification failed; 4. The size of specified requestInfo is greater than 255. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |

**示例**

```TypeScript
示例中的初始化请参见deviceManager.createDeviceManager。
```

## setUserOperation

```TypeScript
setUserOperation(operateAction: number, params: string): void
```

设置用户ui操作行为。

**起始版本：** 9

**废弃版本：** 11

**替代接口：** [replyUiAction](arkts-distributedservice-distributeddevicemanager-devicemanager-i-sys.md#replyuiaction)

**需要权限：** ohos.permission.ACCESS_SERVICE_DM

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
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter type; 3. Parameter verification failed; 4. The size of specified params is greater than 255. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |

**示例**

```TypeScript
示例中的初始化请参见deviceManager.createDeviceManager。
```

## startDeviceDiscovery

```TypeScript
startDeviceDiscovery(subscribeInfo: SubscribeInfo): void
```

发现周边设备。发现状态持续两分钟，超过两分钟，会停止发现，最大发现数量99个。

**起始版本：** 8

**废弃版本：** 11

**替代接口：** [startDiscovering](arkts-distributedservice-distributeddevicemanager-devicemanager-i.md#startdiscovering)(discoverParam: { [key: string]: Object; }, filterOptions?: { [key: string]: Object; })

**需要权限：** ohos.permission.ACCESS_SERVICE_DM

**系统能力：** SystemCapability.DistributedHardware.DeviceManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| subscribeInfo | [SubscribeInfo](arkts-distributedservice-devicemanager-subscribeinfo-i-sys.md) | 是 | 发现信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter type; 3. Parameter verification failed; 4. The size of specified param is greater than 255. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [11600104](../errorcode-device-manager.md#11600104-发现业务不可用) | Discovery unavailable. |
| [11600101](../errorcode-device-manager.md#11600101-服务调用异常) | Failed to execute the function. |

**示例**

```TypeScript
示例中的初始化请参见deviceManager.createDeviceManager。
```

## startDeviceDiscovery

```TypeScript
startDeviceDiscovery(subscribeInfo: SubscribeInfo, filterOptions?: string): void
```

发现周边设备。发现状态持续两分钟，超过两分钟，会停止发现，最大发现数量99个。

**起始版本：** 9

**废弃版本：** 11

**替代接口：** [startDiscovering](arkts-distributedservice-distributeddevicemanager-devicemanager-i.md#startdiscovering)(discoverParam: { [key: string]: Object; }, filterOptions?: { [key: string]: Object; })

**需要权限：** ohos.permission.ACCESS_SERVICE_DM

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
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter type; 3. Parameter verification failed; 4. The size of specified param is greater than 255. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [11600104](../errorcode-device-manager.md#11600104-发现业务不可用) | Discovery unavailable. |
| [11600101](../errorcode-device-manager.md#11600101-服务调用异常) | Failed to execute the function. |

**示例**

参见 [startDeviceDiscovery](#startdevicediscovery)

## stopDeviceDiscovery

```TypeScript
stopDeviceDiscovery(subscribeId: number): void
```

停止发现周边设备。

**起始版本：** 7

**废弃版本：** 11

**替代接口：** [stopDiscovering](arkts-distributedservice-distributeddevicemanager-devicemanager-i.md#stopdiscovering)

**需要权限：** ohos.permission.ACCESS_SERVICE_DM

**系统能力：** SystemCapability.DistributedHardware.DeviceManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| subscribeId | number | 是 | 发现标识。取值范围为1~65535。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter type; 3. Parameter verification failed; 4. The size of specified param is greater than 255. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [11600101](../errorcode-device-manager.md#11600101-服务调用异常) | Failed to execute the function. |

**示例**

```TypeScript
示例中的初始化请参见deviceManager.createDeviceManager。
```

## unAuthenticateDevice

```TypeScript
unAuthenticateDevice(deviceInfo: DeviceInfo): void
```

解除认证设备。

**起始版本：** 8

**废弃版本：** 11

**替代接口：** [unbindTarget](arkts-distributedservice-distributeddevicemanager-devicemanager-i.md#unbindtarget)

**需要权限：** ohos.permission.ACCESS_SERVICE_DM

**系统能力：** SystemCapability.DistributedHardware.DeviceManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| deviceInfo | [DeviceInfo](arkts-distributedservice-devicemanager-deviceinfo-i-sys.md) | 是 | 设备信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter type; 3. Parameter verification failed. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [11600101](../errorcode-device-manager.md#11600101-服务调用异常) | Failed to execute the function. |

**示例**

```TypeScript
示例中的初始化请参见deviceManager.createDeviceManager。
```

## unPublishDeviceDiscovery

```TypeScript
unPublishDeviceDiscovery(publishId: number): void
```

停止发布设备发现。

**起始版本：** 9

**废弃版本：** 11

**需要权限：** ohos.permission.ACCESS_SERVICE_DM

**系统能力：** SystemCapability.DistributedHardware.DeviceManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| publishId | number | 是 | 发布标识。 取值范围为1~2147483647。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter type; 3. Parameter verification failed. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [11600101](../errorcode-device-manager.md#11600101-服务调用异常) | Failed to execute the function. |

**示例**

```TypeScript
示例中的初始化请参见deviceManager.createDeviceManager。
```

## verifyAuthInfo

```TypeScript
verifyAuthInfo(authInfo: AuthInfo, callback: AsyncCallback<{ deviceId: string, level: number }>): void
```

验证认证信息。

**起始版本：** 7

**废弃版本：** 11

**需要权限：** ohos.permission.ACCESS_SERVICE_DM

**系统能力：** SystemCapability.DistributedHardware.DeviceManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| authInfo | [AuthInfo](arkts-distributedservice-devicemanager-authinfo-i-sys.md) | 是 | 认证信息。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;{ deviceId: string, level: number }&gt; | 是 | 验证结果回调。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter type; 3. Parameter verification failed. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |

**示例**

```TypeScript
示例中的初始化请参见deviceManager.createDeviceManager。
```
