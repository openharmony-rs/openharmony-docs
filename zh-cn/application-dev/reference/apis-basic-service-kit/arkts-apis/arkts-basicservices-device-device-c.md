# Device

getInfo interface

**起始版本：** 3

**废弃版本：** 6

<!--Device-unnamed-export default class Device--><!--Device-unnamed-export default class Device-End-->

**系统能力：** SystemCapability.Startup.SystemInfo.Lite

## 导入模块

```TypeScript
import { DeviceResponse, GetDeviceOptions } from '@kit.BasicServicesKit';
```

<a id="getinfo"></a>
## getInfo

```TypeScript
static getInfo(options?: GetDeviceOptions): void
```

Obtains the device information.

**起始版本：** 3

**废弃版本：** 6

<!--Device-Device-static getInfo(options?: GetDeviceOptions): void--><!--Device-Device-static getInfo(options?: GetDeviceOptions): void-End-->

**系统能力：** SystemCapability.Startup.SystemInfo.Lite

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [GetDeviceOptions](arkts-basicservices-device-getdeviceoptions-i.md) | 否 | Options |

**示例：**

ArkTS（方舟编程语言）示例：

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

JS示例：

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

