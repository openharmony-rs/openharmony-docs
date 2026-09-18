# @ohos.bluetooth.access(蓝牙access模块)

本模块提供了打开和关闭蓝牙、获取蓝牙开关状态以及其他相关方法。

**起始版本：** 10

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## 导入模块

```TypeScript
import { access } from '@kit.ConnectivityKit';
```

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [addPersistentDeviceId](arkts-connectivity-access-addpersistentdeviceid-f.md) | 持久化存储蓝牙设备的虚拟MAC地址。使用Promise异步回调。 |
| [convertUuid](arkts-connectivity-access-convertuuid-f.md) | 将指定格式的的UUID转换为128bit的UUID。 |
| [deletePersistentDeviceId](arkts-connectivity-access-deletepersistentdeviceid-f.md) | 删除已持久化存储的蓝牙虚拟MAC地址。使用Promise异步回调。 |
| [disableBluetooth](arkts-connectivity-access-disablebluetooth-f.md) | 关闭蓝牙。 |
| [disableBluetoothAsync](arkts-connectivity-access-disablebluetoothasync-f.md) | 关闭蓝牙。使用Promise异步回调。 |
| [enableBluetooth](arkts-connectivity-access-enablebluetooth-f.md) | 开启蓝牙。 |
| [enableBluetoothAsync](arkts-connectivity-access-enablebluetoothasync-f.md) | 开启蓝牙。使用Promise异步回调。 |
| [getPersistentDeviceIds](arkts-connectivity-access-getpersistentdeviceids-f.md) | 获取应用持久化存储过的蓝牙虚拟MAC地址。 |
| [getState](arkts-connectivity-access-getstate-f.md) | 获取蓝牙开关状态。 |
| [isBluetoothSupported](arkts-connectivity-access-isbluetoothsupported-f.md) | 查询本机是否支持蓝牙能力。 |
| [isValidRandomDeviceId](arkts-connectivity-access-isvalidrandomdeviceid-f.md) | 判断对端蓝牙设备的虚拟MAC地址是否有效。 |
| [off](arkts-connectivity-access-off-f.md#offstatechange) | 取消订阅本端蓝牙开关状态变化事件。从API18开始不再校验ohos.permission.ACCESS_BLUETOOTH权限。 |
| [on](arkts-connectivity-access-on-f.md#onstatechange) | 订阅本端蓝牙开关状态变化事件。使用Callback异步回调。从API18开始不再校验ohos.permission.ACCESS_BLUETOOTH权限。 |

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [factoryReset](arkts-connectivity-access-factoryreset-f-sys.md) | 恢复蓝牙出厂设置。使用Callback异步回调。 |
| [factoryReset](arkts-connectivity-access-factoryreset-f-sys.md) | 恢复蓝牙出厂设置。使用Promise异步回调。 |
| [getLocalAddress](arkts-connectivity-access-getlocaladdress-f-sys.md) | 获取本端设备的蓝牙地址。 |
| [notifyDialogResult](arkts-connectivity-access-notifydialogresult-f-sys.md) | 将用户操作蓝牙对话框的行为通知给蓝牙服务。使用Promise异步回调。 |
| [restrictBluetooth](arkts-connectivity-access-restrictbluetooth-f-sys.md) | 约束当前蓝牙设备的BR/EDR能力，约束后设备的经典蓝牙功能将受限，适用于仅需使用低功耗蓝牙的场景。使用Promise异步回调。 |
<!--DelEnd-->

<!--Del-->
### 接口（系统接口）

| 名称 | 说明 |
| --- | --- |
| [NotifyDialogResultParams](arkts-connectivity-access-notifydialogresultparams-i-sys.md) | 用户操作对话框的行为。 |
<!--DelEnd-->

### 枚举

| 名称 | 说明 |
| --- | --- |
| [BluetoothState](arkts-connectivity-access-bluetoothstate-e.md) | 枚举，蓝牙开关状态。 |

<!--Del-->
### 枚举（系统接口）

| 名称 | 说明 |
| --- | --- |
| [DialogType](arkts-connectivity-access-dialogtype-e-sys.md) | 枚举，对话框类型。 |
<!--DelEnd-->
