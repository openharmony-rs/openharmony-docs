# PanProfile

表示蓝牙PAN通信的实例，提供查询本端PAN支持状态、网络共享状态等能力，适用于蓝牙个人局域网共享网络场景。

使用PanProfile方法之前需要创建该类的实例进行操作，通过[createPanProfile](arkts-connectivity-pan-createpanprofile-f.md)方法构造此实例。该类继承于[BaseProfile](arkts-connectivity-pan-baseprofile-t.md)，因此可以使用其父类中的方法。

**继承/实现关系：** PanProfile extends [BaseProfile](arkts-connectivity-pan-baseprofile-t.md)

**起始版本：** 10

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## 导入模块

```TypeScript
import { pan } from '@kit.ConnectivityKit';
```

## connect

```TypeScript
connect(deviceId: string): void
```

本端作为PANU（个人区域网用户）角色时使用，向指定设备发起PAN服务连接请求。需确保对端设备已启用网络共享（NAP）能力才能成功连接。适用于本端需要通过蓝牙PAN连接到远端NAP设备以获取网络访问的场景，例如设备间通过蓝牙共享网络连接。

可通过订阅on('connectionStateChange')事件来感知连接是否成功。当不需要连接时需调用[disconnect](#disconnect)断开连接。

**起始版本：** 26.0.0

**需要权限：** ohos.permission.ACCESS_BLUETOOTH

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| deviceId | string | 是 | 表示远端设备MAC地址。例如："XX:XX:XX:XX:XX:XX"。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Non-system applications are not allowed to use system APIs. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. Only can be called on phone, tablet, and 2in1 devices. Failed to call the API when the short-range chip is not inserted on 2in1 device. |
| [2900003](../errorcode-bluetoothManager.md#2900003-蓝牙开关关闭) | Bluetooth disabled. |
| [2900004](../errorcode-bluetoothManager.md#2900004-配置文件不支持) | Remote Device profile not supported. |
| [2900099](../errorcode-bluetoothManager.md#2900099-操作失败) | Operation failed. |

**示例**

```TypeScript
try {
    let panProfile: pan.PanProfile = pan.createPanProfile();
    panProfile.connect('XX:XX:XX:XX:XX:XX');
} catch (err) {
    console.error(`errCode: ${err.code}, errMessage: ${err.message}`);
}
```

## disconnect

```TypeScript
disconnect(deviceId: string): void
```

本端作为PANU（个人区域网用户）角色时使用，断开与当前连接设备的PAN服务，并释放相关的资源。适用于不再需要通过蓝牙PAN获取网络服务时主动断开连接的场景。

可通过订阅on('connectionStateChange')事件来感知断开是否成功。

**起始版本：** 10

**需要权限：** ohos.permission.ACCESS_BLUETOOTH

**模型约束：** 此接口仅可在Stage模型下使用。

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

**示例**

```TypeScript
try {
    let panProfile: pan.PanProfile = pan.createPanProfile();
    panProfile.disconnect('XX:XX:XX:XX:XX:XX');
} catch (err) {
    console.error(`errCode: ${err.code}, errMessage: ${err.message}`);
```

## setTethering

```TypeScript
setTethering(enable: boolean): void
```

本端作为NAP（网络接入点）角色时使用，用于设置网络共享状态。

当本端未启用网络共享能力时，作为PANU角色的对端设备无法连接本端的PAN服务。调用该接口前，建议先调用[isTetheringOn](arkts-connectivity-pan-panprofile-i.md#istetheringon)判断当前的网络共享状态。开启网络共享状态后，可以通过订阅on('connectionStateChange')事件来感知作为PANU角色的对端设备的连接。

**起始版本：** 10

**需要权限：** ohos.permission.ACCESS_BLUETOOTH and ohos.permission.MANAGE_BLUETOOTH

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enable | boolean | 是 | 是否启用网络共享。true表示启用网络共享，false表示不启用网络共享。 |

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

**示例**

```TypeScript
try {
    let panProfile: pan.PanProfile = pan.createPanProfile();
    panProfile.setTethering(false);
} catch (err) {
    console.error(`errCode: ${err.code}, errMessage: ${err.message}`);
```
