# ScanFilter

扫描BLE广播的过滤条件，只有符合该条件的广播报文才会上报。

**起始版本：** 10

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## 导入模块

```TypeScript
import { ble } from '@kit.ConnectivityKit';
```

## irk

```TypeScript
irk?: Uint8Array
```

通过蓝牙设备地址解析密钥（Identity Resolving Key, IRK）过滤携带[可解析私有地址](arkts-connectivity-common-bluetoothrawaddresstype-e.md)的BLE广播报文。默认值为空，表示不按IRK过滤广播报文。

蓝牙设备的可解析私有地址会随时间变化，若已知该设备的IRK和Public类型地址或者Static Random类型的地址，即可过滤同一个蓝牙设备在不同时间发出的BLE广播报文。

使用本参数时，必须同时通过[ScanFilter](arkts-connectivity-ble-scanfilter-i.md)中的address参数指定地址和地址类型等信息。其中，地址必须为有效的Public类型地址或Static Random类型地址，[addressType](arkts-connectivity-common-bluetoothaddresstype-e.md)必须设置为REAL，[rawAddressType](arkts-connectivity-common-bluetoothrawaddresstype-e.md)必须根据address的实际情况进行设置，否则将无法正确过滤携带可解析私有地址的BLE广播报文。

**类型：** Uint8Array

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**系统接口：** 此接口为系统接口。
