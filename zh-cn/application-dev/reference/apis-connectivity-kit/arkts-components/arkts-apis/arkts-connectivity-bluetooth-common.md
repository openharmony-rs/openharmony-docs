# @ohos.bluetooth.common(蓝牙common模块)

本模块提供了蓝牙公共接口和参数类型。首批接口包括在调用[connection.pairDevice](arkts-connectivity-connection-pairdevice-f.md)时用于指定目标设备的MAC地址与地址类型的相关参数。

**起始版本：** 21

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## 导入模块

```TypeScript
import { common } from '@kit.ConnectivityKit';
```

## 汇总

### 接口

| 名称 | 说明 |
| --- | --- |
| [BluetoothAddress](arkts-connectivity-common-bluetoothaddress-i.md) | 描述蓝牙设备地址信息的参数结构，包括地址与地址类型。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [BluetoothAddressType](arkts-connectivity-common-bluetoothaddresstype-e.md) | 枚举，蓝牙子系统定义的地址类型。蓝牙设备的实际MAC地址属于用户的隐私信息，在发现设备的过程中，蓝牙子系统会给每个蓝牙外设分配一个虚拟MAC地址，并保存该虚拟MAC地址和外设实际MAC地址的映射关系。关于地址类型的详细介绍请参见蓝牙设备地址类型。 |
| [BluetoothRawAddressType](arkts-connectivity-common-bluetoothrawaddresstype-e.md) | 枚举，蓝牙协议定义的蓝牙设备地址类型。关于地址类型的详细介绍请参见蓝牙设备地址类型。 |
