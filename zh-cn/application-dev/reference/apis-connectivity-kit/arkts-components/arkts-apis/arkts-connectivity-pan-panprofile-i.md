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

## isPanSupported

```TypeScript
isPanSupported(): boolean
```

本端作为NAP角色时使用，查询本端设备是否支持PAN能力。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 当前设备支持PAN时返回true，不支持时返回false。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [2900099](../errorcode-bluetoothManager.md#2900099-操作失败) | Operation failed. |

**示例**

```TypeScript
try {
    let panProfile: pan.PanProfile = pan.createPanProfile();
    let isPanSupported: boolean = panProfile.isPanSupported();
} catch (err) {
    console.error(`errCode: ${err.code}, errMessage: ${err.message}`);
}
```

## isTetheringOn

```TypeScript
isTetheringOn(): boolean
```

本端作为NAP时使用，获取本端网络共享状态。

**起始版本：** 26.0.0

**需要权限：** ohos.permission.ACCESS_BLUETOOTH

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 网络共享开启返回true，网络共享关闭返回false。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Non-system applications are not allowed to use system APIs.<br>**适用版本：** 10 - 24 |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. Only can be called on phone, tablet, and 2in1 devices. Failed to call the API when the short-range chip is not inserted on 2in1 device. |

**示例**

```TypeScript
try {
    let panProfile: pan.PanProfile = pan.createPanProfile();
    let isTetheringOn: boolean = panProfile.isTetheringOn();
} catch (err) {
    console.error(`errCode: ${err.code}, errMessage: ${err.message}`);
}
```
