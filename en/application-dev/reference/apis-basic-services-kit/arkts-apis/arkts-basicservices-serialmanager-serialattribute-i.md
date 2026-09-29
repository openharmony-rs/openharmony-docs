# SerialAttribute

```TypeScript
interface SerialAttribute
```

Represents the configuration parameters of a serial port.

**Since:** 19

<!--Device-serialManager-interface SerialAttribute--><!--Device-serialManager-interface SerialAttribute-End-->

**System capability:** SystemCapability.USB.USBManager.Serial

## Modules to Import

```TypeScript
import { serialManager } from '@kit.BasicServicesKit';
```

## baudRate

```TypeScript
baudRate: BaudRates
```

Baud rate of the serial port, in bit/s. This parameter indicates the data transmission rate.

**Type:** [BaudRates](arkts-basicservices-serialmanager-baudrates-e.md)

**Since:** 19

<!--Device-SerialAttribute-baudRate: BaudRates--><!--Device-SerialAttribute-baudRate: BaudRates-End-->

**System capability:** SystemCapability.USB.USBManager.Serial

## dataBits

```TypeScript
dataBits?: DataBits
```

Data bits of the serial port, in bits. The default value is **8**. This parameter indicates the number of valid data bits in a packet.

**Type:** [DataBits](arkts-basicservices-serialmanager-databits-e.md)

**Default:** DATABIT_8

**Since:** 19

<!--Device-SerialAttribute-dataBits?: DataBits--><!--Device-SerialAttribute-dataBits?: DataBits-End-->

**System capability:** SystemCapability.USB.USBManager.Serial

## parity

```TypeScript
parity?: Parity
```

Parity check. The default value is **PARITY_NONE**, indicating that no parity check is performed. This parameter is used to detect data transmission errors.

**Type:** [Parity](arkts-basicservices-serialmanager-parity-e.md)

**Default:** NONE

**Since:** 19

<!--Device-SerialAttribute-parity?: Parity--><!--Device-SerialAttribute-parity?: Parity-End-->

**System capability:** SystemCapability.USB.USBManager.Serial

## stopBits

```TypeScript
stopBits?: StopBits
```

Stop bits of the serial port, in bits. The default value is **1**. This parameter indicates the end of a packet.

**Type:** [StopBits](arkts-basicservices-serialmanager-stopbits-e.md)

**Default:** STOPBIT_1

**Since:** 19

<!--Device-SerialAttribute-stopBits?: StopBits--><!--Device-SerialAttribute-stopBits?: StopBits-End-->

**System capability:** SystemCapability.USB.USBManager.Serial
