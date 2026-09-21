# PerceptionDeviceInfo (System API)

```TypeScript
export interface PerceptionDeviceInfo
```

Defines the device information discovered by perception scanning, including the device type, device ID, and custom data carried in the advertising.

**Since:** 26.0.1

**System capability:** SystemCapability.Communication.SoftBus.Core

**System API:** This is a system API.

## Modules to Import

```TypeScript
```

## customData

```TypeScript
customData: ArrayBuffer
```

Custom data carried in the advertising, which is binary data in ArrayBuffer format. The length is the same as the length of the custom data carried in the advertising of the discovered device. bytes. The maximum length is 5 bytes.

**Type:** ArrayBuffer

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Communication.SoftBus.Core

**System API:** This is a system API.

## deviceId

```TypeScript
deviceId: ArrayBuffer
```

Device ID, which is binary data in **ArrayBuffer** format. The bytes are in network byte order (big-endian). The maximum length is 6 bytes.

**Type:** ArrayBuffer

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Communication.SoftBus.Core

**System API:** This is a system API.

## deviceType

```TypeScript
deviceType: number
```

Device type. The specific value is subject to the system definition. The value should be an integer.

**Type:** number

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Communication.SoftBus.Core

**System API:** This is a system API.
