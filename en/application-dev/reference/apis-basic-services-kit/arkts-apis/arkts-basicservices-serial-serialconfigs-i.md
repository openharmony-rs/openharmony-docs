# SerialConfigs

```TypeScript
interface SerialConfigs
```

Defines the communication parameters of the serial port.

**Since:** 26.0.0

**System capability:** SystemCapability.BusManager.Serial

## Modules to Import

```TypeScript
import { serial } from '@kit.BasicServicesKit';
```

## baudRate

```TypeScript
baudRate?: number
```

Baud rate. The value must be a positive integer. Whether non-standard baud rates are supported depends on the hardware. Unit: bit/s. The default value is **115200**.

**Type:** number

**Default:** 115200

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.BusManager.Serial

## dataBits

```TypeScript
dataBits?: DataBits
```

Data bits. The default value is **EIGHT**, indicating 8 data bits for standard communication. Values **FIVE**, **SIX**, and **SEVEN** are used for old devices or special protocols.

**Type:** [DataBits](arkts-basicservices-serial-databits-e.md)

**Default:** EIGHT

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.BusManager.Serial

## parity

```TypeScript
parity?: Parity
```

Parity bit. The default value is **NONE**, indicating no parity check. **EVEN** and **ODD** are used in scenarios that require high data accuracy. **MARK** and **SPACE** are used for special communication protocols.

**Type:** [Parity](arkts-basicservices-serial-parity-e.md)

**Default:** NONE

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.BusManager.Serial

## rtscts

```TypeScript
rtscts?: boolean
```

Whether to enable hardware-based automatic flow control via RTS/CTS. Hardware-based flow control via RTS/CTS is an automatic data flow control mechanism implemented through hardware signals. The RTS and CTS signal lines work together to prevent buffer overflow. If this flow control is enabled, the system automatically controls RTS and CTS signals to manage mobile data. The value **true** indicates this feature is enabled, and **false** indicates otherwise. The default value is **false**.

**Type:** boolean

**Default:** false

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.BusManager.Serial

## stopBits

```TypeScript
stopBits?: StopBits
```

Stop bits. The default value is **ONE**. One stop bit is used for standard communication. Two stop bits are used to enhance signal stability during low-speed communication or communication with old devices.

**Type:** [StopBits](arkts-basicservices-serial-stopbits-e.md)

**Default:** ONE

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.BusManager.Serial

## xany

```TypeScript
xany?: boolean
```

Whether to enable XANY (Any Character Resume) to control the flow. XANY is an extended mode in the software flow control protocol and takes effect only when XON or XOFF is enabled. When XANY is enabled, any character can be used as the signal to resume transmission, not just the XON character. If software flow control (XON/XOFF) is not enabled, the XANY setting is invalid. The value **true** indicates this feature is enabled, and **false** indicates otherwise. The default value is **false**.

**Type:** boolean

**Default:** false

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.BusManager.Serial

## xoff

```TypeScript
xoff?: boolean
```

Whether to enable XOFF (Xmitter Off) to control the sending of flows. XOFF indicates transmitter off. XOFF is a control character (with the ASCII value of 19) in the software flow control protocol. When the receive buffer is about to overflow, XOFF is sent to instruct the sender to stop sending data. The value **true** indicates this feature is enabled, and **false** indicates otherwise. The default value is **false**.

**Type:** boolean

**Default:** false

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.BusManager.Serial

## xon

```TypeScript
xon?: boolean
```

Whether to enable XON (Xmitter On) to control the sending of flows. XON indicates transmitter on. XON is a control character (with the ASCII value of 17) in the software flow control protocol. When there is space in the receive buffer, XON is sent to instruct the sender to resume data transmission. The value **true** indicates this feature is enabled, and **false** indicates otherwise. The default value is **false**.

**Type:** boolean

**Default:** false

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.BusManager.Serial
