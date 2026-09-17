# MapMseProfile

该实例表示蓝牙消息访问协议中的MSE角色。

- 该类继承于[BaseProfile](arkts-connectivity-map-baseprofile-t.md)，因此可以使用其父类中的方法。  
- 使用该类的接口前，需通过[createMapMseProfile](arkts-connectivity-map-createmapmseprofile-f.md)接口构造该类的实例。  
- 和该实例角色相对应的是MCE角色。

**继承/实现关系：** MapMseProfile extends [BaseProfile](arkts-connectivity-map-baseprofile-t.md)

**起始版本：** 11

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## 导入模块

```TypeScript
import { map } from '@kit.ConnectivityKit';
```

## disconnect

```TypeScript
disconnect(deviceId: string): void
```

断开连接设备的map服务。适用于设备切换、连接异常恢复或用户主动断开蓝牙信息同步等场景。

**起始版本：** 11

**需要权限：** ohos.permission.ACCESS_BLUETOOTH

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| deviceId | string | 是 | 远端设备地址，例如："XX:XX:XX:XX:XX:XX"。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Non-system applications are not allowed to use system APIs. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Invalid parameter. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [2900001](../errorcode-bluetoothManager.md#2900001-蓝牙服务停止) | Service stopped. |
| [2900003](../errorcode-bluetoothManager.md#2900003-蓝牙开关关闭) | Bluetooth disabled. |
| [2900004](../errorcode-bluetoothManager.md#2900004-配置文件不支持) | Profile not supported. |
| [2900099](../errorcode-bluetoothManager.md#2900099-操作失败) | Operation failed. |

## getMessageAccessAuthorization

```TypeScript
getMessageAccessAuthorization(deviceId: string): Promise<AccessAuthorization>
```

获取信息的访问权限。使用Promise异步回调。适用于在蓝牙消息同步前查询当前设备是否已获得信息读取授权的场景。

**起始版本：** 11

**需要权限：** ohos.permission.ACCESS_BLUETOOTH and ohos.permission.MANAGE_BLUETOOTH

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| deviceId | string | 是 | 表示远端设备地址，例如："XX:XX:XX:XX:XX:XX"。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[AccessAuthorization](arkts-connectivity-map-accessauthorization-t-sys.md)&gt; | 以Promise的形式返回结果。如果成功，err为undefined，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Non-system applications are not allowed to use system APIs. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Invalid parameter. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [2900001](../errorcode-bluetoothManager.md#2900001-蓝牙服务停止) | Service stopped. |
| [2900003](../errorcode-bluetoothManager.md#2900003-蓝牙开关关闭) | Bluetooth disabled. |
| [2900004](../errorcode-bluetoothManager.md#2900004-配置文件不支持) | Profile not supported. |
| [2900099](../errorcode-bluetoothManager.md#2900099-操作失败) | Operation failed. |

## setMessageAccessAuthorization

```TypeScript
setMessageAccessAuthorization(deviceId: string, authorization: AccessAuthorization): Promise<void>
```

设置信息的访问权限。使用Promise异步回调。适用于蓝牙消息同步前进行权限授予或撤销的场景，如用户在车载、可穿戴设备上管理蓝牙消息读取权限。

**起始版本：** 11

**需要权限：** ohos.permission.ACCESS_BLUETOOTH and ohos.permission.MANAGE_BLUETOOTH

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| deviceId | string | 是 | 表示远端设备地址，例如："XX:XX:XX:XX:XX:XX"。 |
| authorization | [AccessAuthorization](arkts-connectivity-map-accessauthorization-t-sys.md) | 是 | 表示对信息访问的授权状态，例如允许访问（ACCESS_ALLOWED）、拒绝访问（ACCESS_DENIED）等。具体枚举值及含义详见[AccessAuthorization](arkts-connectivity-constant-accessauthorization-e-sys.md)。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 以Promise的形式返回结果。如果成功，err为undefined，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Non-system applications are not allowed to use system APIs. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Invalid parameter. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [2900001](../errorcode-bluetoothManager.md#2900001-蓝牙服务停止) | Service stopped. |
| [2900003](../errorcode-bluetoothManager.md#2900003-蓝牙开关关闭) | Bluetooth disabled. |
| [2900004](../errorcode-bluetoothManager.md#2900004-配置文件不支持) | Profile not supported. |
| [2900099](../errorcode-bluetoothManager.md#2900099-操作失败) | Operation failed. |
