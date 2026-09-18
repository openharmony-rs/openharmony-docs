# HandsFreeHfProfile

该实例表示蓝牙通话音频中的HF角色‌。

- 该类继承于[BaseProfile](arkts-connectivity-hfp-baseprofile-t.md)，因此可以使用其父类中的方法。  
- 使用该类的接口前，需通过[createHfpHfProfile](arkts-connectivity-hfp-createhfphfprofile-f.md)接口构造该类的实例。  
- 和该实例角色相对应的是HFP AG角色。

**继承/实现关系：** HandsFreeHfProfile extends [BaseProfile](arkts-connectivity-hfp-baseprofile-t.md)

**起始版本：** 26.0.0

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## 导入模块

```TypeScript
import { hfp } from '@kit.ConnectivityKit';
```

## connect

```TypeScript
connect(deviceId: string): void
```

连接设备的HFP服务。例如，在蓝牙耳机或车载设备需要主动连接手机以进行免提通话时使用。

需要通过on('connectionStateChange')接口注册回调，感知设备的HFP Profile的连接状态变化。

**起始版本：** 26.0.0

**需要权限：** ohos.permission.ACCESS_BLUETOOTH

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| deviceId | string | 是 | 远端设备的MAC地址，例如："XX:XX:XX:XX:XX:XX"。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Non-system applications are not allowed to use system APIs. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [2900001](../errorcode-bluetoothManager.md#2900001-蓝牙服务停止) | Service stopped. |
| [2900003](../errorcode-bluetoothManager.md#2900003-蓝牙开关关闭) | Bluetooth disabled. |
| [2900004](../errorcode-bluetoothManager.md#2900004-配置文件不支持) | Profile not supported. |
| [2900099](../errorcode-bluetoothManager.md#2900099-操作失败) | Internal system error. For example, IPC error. |

**示例**

```TypeScript
try {
    let hf = hfp.createHfpHfProfile();
    hf.connect('XX:XX:XX:XX:XX:XX');
} catch (err) {
    console.error(`errCode: ${err.code}, errMessage: ${err.message}`);
}
```

## disconnect

```TypeScript
disconnect(deviceId: string): void
```

断开连接设备的HFP服务。

需要通过on('connectionStateChange')接口注册回调，感知设备的HFP Profile的连接状态变化。

**起始版本：** 26.0.0

**需要权限：** ohos.permission.ACCESS_BLUETOOTH

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| deviceId | string | 是 | 远端设备的MAC地址，例如："XX:XX:XX:XX:XX:XX"。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Non-system applications are not allowed to use system APIs. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [2900001](../errorcode-bluetoothManager.md#2900001-蓝牙服务停止) | Service stopped. |
| [2900003](../errorcode-bluetoothManager.md#2900003-蓝牙开关关闭) | Bluetooth disabled. |
| [2900004](../errorcode-bluetoothManager.md#2900004-配置文件不支持) | Profile not supported. |
| [2900099](../errorcode-bluetoothManager.md#2900099-操作失败) | Internal system error. For example, IPC error. |

**示例**

```TypeScript
try {
    let hf = hfp.createHfpHfProfile();
    hf.disconnect('XX:XX:XX:XX:XX:XX');
} catch (err) {
    console.error(`errCode: ${err.code}, errMessage: ${err.message}`);
}
```
