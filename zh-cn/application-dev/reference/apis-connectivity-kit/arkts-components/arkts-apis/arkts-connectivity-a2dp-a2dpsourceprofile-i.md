# A2dpSourceProfile

该实例表示蓝牙媒体音频中的A2DP Source角色。

该类继承于[BaseProfile](arkts-connectivity-a2dp-baseprofile-t.md)，因此可以使用其父类中的方法。使用该类的方法前，需通过[createA2dpSrcProfile](arkts-connectivity-a2dp-createa2dpsrcprofile-f.md)方法构造该类的实例。和该实例角色相对应的是A2DP Sink。

**继承/实现关系：** A2dpSourceProfile extends [BaseProfile](arkts-connectivity-a2dp-baseprofile-t.md)

**起始版本：** 10

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## 导入模块

```TypeScript
import { a2dp } from '@kit.ConnectivityKit';
```

## getPlayingState

```TypeScript
getPlayingState(deviceId: string): PlayingState
```

获取本端和对端设备间的媒体音频播放状态。例如，在音乐播放器应用中可用于检查蓝牙音频是否正在播放，从而同步更新界面的播放/暂停按钮状态。

从API version 21开始，此接口支持使用对端设备的实际MAC地址获取媒体音频播放状态。

**起始版本：** 10

**需要权限：** ohos.permission.ACCESS_BLUETOOTH

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| deviceId | string | 是 | 对端设备地址，例如："XX:XX:XX:XX:XX:XX"。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [PlayingState](arkts-connectivity-a2dp-playingstate-e.md) | 蓝牙媒体音频播放状态。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Invalid parameter. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [2900001](../errorcode-bluetoothManager.md#2900001-蓝牙服务停止) | Service stopped. |
| [2900003](../errorcode-bluetoothManager.md#2900003-蓝牙开关关闭) | Bluetooth disabled. |
| [2900004](../errorcode-bluetoothManager.md#2900004-配置文件不支持) | Profile not supported. |
| [2900099](../errorcode-bluetoothManager.md#2900099-操作失败) | Operation failed. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
try {
    let a2dpSrc = a2dp.createA2dpSrcProfile();
    let state = a2dpSrc.getPlayingState('XX:XX:XX:XX:XX:XX');
} catch (err) {
    console.error('errCode: ' + (err as BusinessError).code + ', errMessage: ' + (err as BusinessError).message);
}
```
