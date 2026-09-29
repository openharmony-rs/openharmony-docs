# ScanResults

```TypeScript
interface ScanResults
```

Represents the scanning results.

**Since:** 26.0.0

<!--Device-scan-interface ScanResults--><!--Device-scan-interface ScanResults-End-->

**System capability:** SystemCapability.Communication.NearLink.Base

## Modules to Import

```TypeScript
import { scan } from '@kit.ConnectivityKit';
```

## address

```TypeScript
address: string
```

Address of the device discovered. The address format is **11:22:33:AA:BB:FF**.

**Type:** string

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-ScanResults-address: string--><!--Device-ScanResults-address: string-End-->

**System capability:** SystemCapability.Communication.NearLink.Base

## data

```TypeScript
data: ArrayBuffer
```

Advertising packet data.

**Type:** ArrayBuffer

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-ScanResults-data: ArrayBuffer--><!--Device-ScanResults-data: ArrayBuffer-End-->

**System capability:** SystemCapability.Communication.NearLink.Base

## deviceClass

```TypeScript
deviceClass?: nearlinkConstant.DeviceClass
```

Type of the device discovered. This field is not returned if the device advertising information does not carry the device type.

**Type:** [nearlinkConstant.DeviceClass](arkts-connectivity-nearlinkconstant-deviceclass-e.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-ScanResults-deviceClass?: nearlinkConstant.DeviceClass--><!--Device-ScanResults-deviceClass?: nearlinkConstant.DeviceClass-End-->

**System capability:** SystemCapability.Communication.NearLink.Base

## deviceName

```TypeScript
deviceName: string
```

Name of the device discovered. The value contains 0 to 30 characters.

**Type:** string

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-ScanResults-deviceName: string--><!--Device-ScanResults-deviceName: string-End-->

**System capability:** SystemCapability.Communication.NearLink.Base

## isConnectable

```TypeScript
isConnectable: boolean
```

Whether the discovered device is connectable. The value **true** indicates that the discovered device is connectable, and the value **false** indicates the opposite.

**Type:** boolean

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-ScanResults-isConnectable: boolean--><!--Device-ScanResults-isConnectable: boolean-End-->

**System capability:** SystemCapability.Communication.NearLink.Base

## rssi

```TypeScript
rssi: number
```

RSSI of the device discovered. The value range is [–128, +127], in dBm. The value **127** is invalid. The value should be an integer.

**Type:** number

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-ScanResults-rssi: int--><!--Device-ScanResults-rssi: int-End-->

**System capability:** SystemCapability.Communication.NearLink.Base
