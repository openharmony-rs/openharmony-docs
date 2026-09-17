# NNRTDeviceDescription

Provides the nnrt device description

**Since:** 12

**System capability:** SystemCapability.AI.MindSporeLite

## Modules to Import

```TypeScript
import { mindSporeLite } from '@kit.MindSporeLiteKit';
```

## deviceID

```TypeScript
deviceID() : bigint
```

Get device id

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.AI.MindSporeLite

**Return value:**

| Type | Description |
| --- | --- |
| bigint | the number of device id |

**Examples**

```TypeScript
let context: mindSporeLite.Context = {};
context.target = ["nnrt"];
context.nnrt = {};
let allDevices = mindSporeLite.getAllNNRTDeviceDescriptions();
if (allDevices == null || allDevices.length === 0) {
  console.error(`Failed to get NNRT device descriptions. Context: ${JSON.stringify(context)}, Result: null or empty`);
} else {
  console.info(`Succeeded in getting NNRT device descriptions. Device count: ${allDevices.length}`);
    for (let i: number = 0; i < allDevices.length; i++) {
      console.info(`Device ${i} ID: ${allDevices[i].deviceID().toString()}`);
  }
}
```

## deviceName

```TypeScript
deviceName() : string
```

Get device name.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.AI.MindSporeLite

**Return value:**

| Type | Description |
| --- | --- |
| string | device name |

**Examples**

```TypeScript
let context: mindSporeLite.Context = {};
context.target = ["nnrt"];
context.nnrt = {};
let allDevices = mindSporeLite.getAllNNRTDeviceDescriptions();
if (allDevices == null || allDevices.length === 0) {
  console.error(`Failed to get NNRT device descriptions. Context: ${JSON.stringify(context)}, Result: null or empty`);
} else {
console.info(`Succeeded in getting NNRT device descriptions. Device count: ${allDevices.length}`);
  for (let i: number = 0; i < allDevices.length; i++) {
    console.info(`Device ${i} name: ${allDevices[i].deviceName()}`);
  }
}
```

## deviceType

```TypeScript
deviceType() : NNRTDeviceType
```

Get device type.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.AI.MindSporeLite

**Return value:**

| Type | Description |
| --- | --- |
| [NNRTDeviceType](arkts-mindsporelite-mindsporelite-nnrtdevicetype-e.md) | the device type |

**Examples**

```TypeScript
let context: mindSporeLite.Context = {};
context.target = ["nnrt"];
context.nnrt = {};
let allDevices = mindSporeLite.getAllNNRTDeviceDescriptions();
if (allDevices == null || allDevices.length === 0) {
  console.error(`Failed to get NNRT device descriptions. Context: ${JSON.stringify(context)}, Result: null or empty`);
} else {
console.info(`Succeeded in getting NNRT device descriptions. Device count: ${allDevices.length}`);
  for (let i: number = 0; i < allDevices.length; i++) {
    console.info(`Device ${i} type: ${allDevices[i].deviceType().toString()}`);
  }
}
```
