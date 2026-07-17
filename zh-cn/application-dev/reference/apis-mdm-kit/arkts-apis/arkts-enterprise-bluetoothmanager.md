# @ohos.enterprise.bluetoothManager

本模块提供设备蓝牙管理的能力，包括设置和查询蓝牙信息等。

> **说明：**  
>  
> 本模块接口仅可在Stage模型下使用。  
>  
> 本模块接口仅对设备管理应用开放，且调用接口前需激活设备管理应用，具体请参考[MDM Kit开发指南](../../../../mdm/mdm-kit-guide.md)。  
>  
> 全局通用限制类策略由restrictions统一提供，若要全局禁用蓝牙，请参考  
> [@ohos.enterprise.restrictions （限制类策略）](arkts-enterprise-restrictions.md)。

**起始版本：** 11

<!--Device-unnamed-declare namespace bluetoothManager--><!--Device-unnamed-declare namespace bluetoothManager-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## 导入模块

```TypeScript
import { bluetoothManager } from '@kit.MDMKit';
```

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [addAllowedBluetoothDevices](arkts-mdm-bluetoothmanager-addallowedbluetoothdevices-f.md#addallowedbluetoothdevices-1) | 添加蓝牙设备可用名单。添加蓝牙设备可用名单后当前设备仅允许连接该名单下的蓝牙设备。从API version 22开始，数组中的MAC地址必须符合蓝牙MAC规范（例如：00:1A:2B:3C:4D:5E），添加时会移除不合法的MAC地址，仅添加合法的MAC地址。以下情况下，通过本接口添加蓝牙设备可用名单，会报策略冲突：1. 已经通过[setDisallowedPolicy](arkts-mdm-restrictions-setdisallowedpolicy-f.md#setdisallowedpolicy-1)接口禁用了蓝牙。通过[setDisallowedPolicy](arkts-mdm-restrictions-setdisallowedpolicy-f.md#setdisallowedpolicy-1)接口启用蓝牙后，可解除冲突。2. 已经通过[addDisallowedBluetoothDevices](arkts-mdm-bluetoothmanager-adddisallowedbluetoothdevices-f.md#adddisallowedbluetoothdevices-1)接口添加了蓝牙设备禁用名单。通过[removeDisallowedBluetoothDevices](arkts-mdm-bluetoothmanager-removedisallowedbluetoothdevices-f.md#removedisallowedbluetoothdevices-1)移除蓝牙设备禁用名单后，可解除冲突。 |
| [addDisallowedBluetoothDevices](arkts-mdm-bluetoothmanager-adddisallowedbluetoothdevices-f.md#adddisallowedbluetoothdevices-1) | 添加蓝牙设备禁用名单。添加禁用名单后当前设备不允许连接该名单下的蓝牙设备。从API version 22开始，数组中的MAC地址必须符合蓝牙MAC规范（例如：00:1A:2B:3C:4D:5E），添加时会移除不合法的MAC地址，仅添加合法的MAC地址。以下情况下，通过本接口添加蓝牙设备禁用名单，会报策略冲突：1. 已经通过[setDisallowedPolicy](arkts-mdm-restrictions-setdisallowedpolicy-f.md#setdisallowedpolicy-1)接口禁用了蓝牙。通过[setDisallowedPolicy](arkts-mdm-restrictions-setdisallowedpolicy-f.md#setdisallowedpolicy-1)接口启用蓝牙后，可解除冲突。2. 已经通过[addAllowedBluetoothDevices](arkts-mdm-bluetoothmanager-addallowedbluetoothdevices-f.md#addallowedbluetoothdevices-1)接口添加了蓝牙设备可用名单。通过[removeAllowedBluetoothDevices](arkts-mdm-bluetoothmanager-removeallowedbluetoothdevices-f.md#removeallowedbluetoothdevices-1)移除蓝牙设备可用名单后，可解除冲突。 |
| [addDisallowedBluetoothProtocols](arkts-mdm-bluetoothmanager-adddisallowedbluetoothprotocols-f.md#adddisallowedbluetoothprotocols-1) | 添加蓝牙协议禁用名单。添加后，指定用户将无法使用该禁用名单中的蓝牙协议向其他设备外发文件。通过该接口禁用GATT或SPP协议，对系统服务和系统应用不生效。当传入SPP协议时，会同时禁用接收和发送功能。 |
| [addDisallowedBluetoothProtocols](arkts-mdm-bluetoothmanager-adddisallowedbluetoothprotocols-f.md#adddisallowedbluetoothprotocols-2) | 添加蓝牙协议至禁用名单。添加后，指定用户将无法根据指定的传输策略使用该禁用名单中的蓝牙协议。 |
| [getAllowedBluetoothDevices](arkts-mdm-bluetoothmanager-getallowedbluetoothdevices-f.md#getallowedbluetoothdevices-1) | 获取蓝牙设备可用名单。 |
| [getBluetoothInfo](arkts-mdm-bluetoothmanager-getbluetoothinfo-f.md#getbluetoothinfo-1) | 查询设备蓝牙信息。 |
| [getDisallowedBluetoothDevices](arkts-mdm-bluetoothmanager-getdisallowedbluetoothdevices-f.md#getdisallowedbluetoothdevices-1) | 获取蓝牙设备禁用名单。 |
| [getDisallowedBluetoothProtocols](arkts-mdm-bluetoothmanager-getdisallowedbluetoothprotocols-f.md#getdisallowedbluetoothprotocols-1) | 获取指定用户的蓝牙协议禁用名单。 |
| [getDisallowedBluetoothProtocols](arkts-mdm-bluetoothmanager-getdisallowedbluetoothprotocols-f.md#getdisallowedbluetoothprotocols-2) | 获取指定用户指定传输策略下已禁用的蓝牙协议列表。 |
| [removeAllowedBluetoothDevices](arkts-mdm-bluetoothmanager-removeallowedbluetoothdevices-f.md#removeallowedbluetoothdevices-1) | 移除蓝牙设备可用名单。 |
| [removeDisallowedBluetoothDevices](arkts-mdm-bluetoothmanager-removedisallowedbluetoothdevices-f.md#removedisallowedbluetoothdevices-1) | 移除蓝牙设备禁用名单。若移除禁用名单中的部分蓝牙设备，则当前设备不允许连接禁用名单内剩余的蓝牙设备。若移除禁用名单中的所有蓝牙设备，则当前设备可以连接任意的蓝牙设备。 |
| [removeDisallowedBluetoothProtocols](arkts-mdm-bluetoothmanager-removedisallowedbluetoothprotocols-f.md#removedisallowedbluetoothprotocols-1) | 移除蓝牙协议禁用名单。若移除禁用名单中某个用户的部分蓝牙协议，则该用户不能使用禁用名单内剩余的蓝牙协议向其他设备外发文件。若移除禁用名单中某个用户的所有蓝牙协议，则该用户可以使用任意蓝牙协议向其他设备外发文件。若移除禁用名单中不存在的蓝牙协议，接口可调用成功，但不会移除禁用名单中不存在的蓝牙协议。 |
| [removeDisallowedBluetoothProtocols](arkts-mdm-bluetoothmanager-removedisallowedbluetoothprotocols-f.md#removedisallowedbluetoothprotocols-2) | 从禁用名单中移除蓝牙协议。移除后，指定用户将不再受该传输策略的限制，可以正常使用这些蓝牙协议。 |
| [turnOffBluetooth](arkts-mdm-bluetoothmanager-turnoffbluetooth-f.md#turnoffbluetooth-1) | 关闭蓝牙。蓝牙关闭后用户可以手动打开。 |
| [turnOnBluetooth](arkts-mdm-bluetoothmanager-turnonbluetooth-f.md#turnonbluetooth-1) | 开启蓝牙。蓝牙开启后用户可以手动关闭。 |

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [isBluetoothDisabled](arkts-mdm-bluetoothmanager-isbluetoothdisabled-f-sys.md#isbluetoothdisabled-1) | 查询蓝牙是否被禁用。 |
| [setBluetoothDisabled](arkts-mdm-bluetoothmanager-setbluetoothdisabled-f-sys.md#setbluetoothdisabled-1) | 设置禁用蓝牙策略。 |
<!--DelEnd-->

### 接口

| 名称 | 说明 |
| --- | --- |
| [BluetoothInfo](arkts-mdm-bluetoothmanager-bluetoothinfo-i.md) | 设备的蓝牙信息。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [Protocol](arkts-mdm-bluetoothmanager-protocol-e.md) | 蓝牙协议类型。 |
| [TransferPolicy](arkts-mdm-bluetoothmanager-transferpolicy-e.md) | 传输策略。 |

