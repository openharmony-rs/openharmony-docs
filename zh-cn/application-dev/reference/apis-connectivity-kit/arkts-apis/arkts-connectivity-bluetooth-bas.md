# @ohos.bluetooth.bas(蓝牙bas模块)

提供了访问BAS（Battery Service，电量服务）相关能力的方法，包括读取远端设备电量信息、监听远端设备电量信息变化等。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { bas } from '@kit.ConnectivityKit';
```

## 汇总

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [getRemoteDeviceBatteryInfo](arkts-connectivity-bas-getremotedevicebatteryinfo-f-sys.md) | 查询远端设备的电量信息。 |
| [isBasSupported](arkts-connectivity-bas-isbassupported-f-sys.md) | 判断本机设备是否可以获取远端设备的电量。 |
| [offBatteryChange](arkts-connectivity-bas-offbatterychange-f-sys.md) | 取消订阅远端设备电量状态变化事件。 |
| [onBatteryChange](arkts-connectivity-bas-onbatterychange-f-sys.md) | 订阅远端设备电量状态变化事件。 |
<!--DelEnd-->

<!--Del-->
### 接口（系统接口）

| 名称 | 说明 |
| --- | --- |
| [BatteryInfo](arkts-connectivity-bas-batteryinfo-i-sys.md) | 描述设备的电量信息。 |
<!--DelEnd-->

<!--Del-->
### 类型（系统接口）

| 名称 | 说明 |
| --- | --- |
| [BluetoothAddress](arkts-connectivity-bas-bluetoothaddress-t-sys.md) | 描述蓝牙设备地址信息的参数结构，包括地址与地址类型。 |
<!--DelEnd-->
