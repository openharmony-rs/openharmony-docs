# Device

getInfo interface

**起始版本：** 3

**废弃版本：** 6

<!--Device-unnamed-export default class Device--><!--Device-unnamed-export default class Device-End-->

**系统能力：** SystemCapability.Startup.SystemInfo.Lite

## 导入模块

```TypeScript
import { Device, DeviceResponse, GetDeviceOptions } from '@kit.BasicServicesKit';
```

## getInfo

```TypeScript
static getInfo(options?: GetDeviceOptions): void
```

获取当前设备的信息。该接口异步读取系统设备信息，通过回调函数返回设备品牌、型号、屏幕参数等数据。 > **说明：**<br> > > 在首页的onShow生命周期之前不建议调用Device.getInfo接口。 **系统能力：** SystemCapability.Startup.SystemInfo.Lite **返回值：** | 类型 | 说明 | | -------- | -------- | | void | 无返回值，设备信息通过回调函数返回。 |

**起始版本：** 3

**废弃版本：** 6

<!--Device-Device-static getInfo(options?: GetDeviceOptions): void--><!--Device-Device-static getInfo(options?: GetDeviceOptions): void-End-->

**系统能力：** SystemCapability.Startup.SystemInfo.Lite

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [GetDeviceOptions](arkts-basicservices-system-device-getdeviceoptions-i.md) | 否 | 定义设备信息获取的参数选项。省略时使用默认配置获取设备基本信息。 |

**示例**

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

