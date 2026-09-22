# Device

```TypeScript
export default class Device
```

getInfo interface

**Since:** 3

**Deprecated since:** 6

**System capability:** SystemCapability.Startup.SystemInfo.Lite

## Modules to Import

```TypeScript
import { Device, DeviceResponse, GetDeviceOptions } from '@kit.BasicServicesKit';
```

## getInfo

```TypeScript
static getInfo(options?: GetDeviceOptions): void
```

Obtains the device information. This API asynchronously reads the system device information and uses a callback to return the device brand, model, screen parameters, and other data.

> **NOTE:** 
> 
> Do not call **Device.getInfo** before the **onShow** event of the home page.

**Since:** 3

**Deprecated since:** 6

**Model restriction:** This API can be used in both the stage model and FA model.

**System capability:** SystemCapability.Startup.SystemInfo.Lite

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [GetDeviceOptions](arkts-basicservices-system-device-getdeviceoptions-i.md) | No | Parameters for obtaining the device information. If the parameters are not specified, the default configuration is used to obtain basic device information. |

**Examples**

ArkTS example:

```TypeScript
interface DeviceData {
  brand: string;
}

export default class Page {
  getInfo() {
    try {
      Device.getInfo({
        success: (data: DeviceData) => {
          console.info(`Device information obtained successfully. Device brand: ${data.brand}`);
        },
        fail: (data: any, code: number) => {
          console.error(`Failed to obtain device information. Code: ${code}, message: ${data}`);
        },
      });
    } catch (error) {
      console.error('Failed to call device information API:', error);
    }
  }
}
```

JS example:

```TypeScript
<div class="container">
    <text class="title">Device Information</text>
    <input type="button" value="Get Device Brand" class="button" onclick="getDeviceInfo"></input>
    <text class="info">{{brandInfo}}</text>
</div>
```

```TypeScript
/* xxx.css */
.container {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    left: 0px;
    top: 0px;
    width: 100%;
    height: 100%;
}

.title {
    font-size: 40px;
    text-align: center;
    width: 100%;
    height: 80px;
    margin-bottom: 50px;
}

.button {
    font-size: 30px;
    text-align: center;
    width: 240px;
    height: 80px;
    margin: 20px;
}

.info {
    font-size: 28px;
    text-align: center;
    width: 100%;
    height: 60px;
    margin-top: 50px;
    color: #007dff;
}
```

```TypeScript
// xxx.js
import Device from '@system.device';

export default {
  data: {
    brandInfo: 'Click the button to get device brand'
  },
  
  getDeviceInfo() {
    try {
      Device.getInfo({
        success: (data) => {
          console.info(`Device information obtained successfully. Device brand: ${data.brand}`);
          this.brandInfo = 'Device brand: ' + data.brand;
        },
        fail: (data, code) => {
          console.error(`Failed to obtain device information. Code: ${code}, message: ${data}`);
          this.brandInfo = 'Failed to obtain, error code: ' + code;
        },
      });
    } catch (error) {
      console.error('Failed to call device information API:', error);
      this.brandInfo = 'Current device does not support this API';
    }
  }
}
```
