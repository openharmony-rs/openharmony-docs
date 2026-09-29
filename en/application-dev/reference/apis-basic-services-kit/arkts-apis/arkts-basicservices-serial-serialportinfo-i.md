# SerialPortInfo

```TypeScript
interface SerialPortInfo
```

Describes the serial port information.

**Since:** 26.0.0

<!--Device-serial-interface SerialPortInfo--><!--Device-serial-interface SerialPortInfo-End-->

**System capability:** SystemCapability.BusManager.Serial

## Modules to Import

```TypeScript
import { serial } from '@kit.BasicServicesKit';
```

## manufacturer

```TypeScript
manufacturer?: string
```

Manufacturer name of the USB virtual serial port.

**Type:** string

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-SerialPortInfo-manufacturer?: string--><!--Device-SerialPortInfo-manufacturer?: string-End-->

**System capability:** SystemCapability.BusManager.Serial

## portName

```TypeScript
portName: string
```

Port name.

**Type:** string

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-SerialPortInfo-portName: string--><!--Device-SerialPortInfo-portName: string-End-->

**System capability:** SystemCapability.BusManager.Serial

## productId

```TypeScript
productId?: number
```

Product ID of the USB virtual serial port.

**Type:** number

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-SerialPortInfo-productId?: int--><!--Device-SerialPortInfo-productId?: int-End-->

**System capability:** SystemCapability.BusManager.Serial

## vendorId

```TypeScript
vendorId?: number
```

Vendor ID of the USB virtual serial port.

**Type:** number

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-SerialPortInfo-vendorId?: int--><!--Device-SerialPortInfo-vendorId?: int-End-->

**System capability:** SystemCapability.BusManager.Serial
