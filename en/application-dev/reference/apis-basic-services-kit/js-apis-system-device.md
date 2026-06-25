# @system.device (Device Information)
<!--Kit: Basic Services Kit-->
<!--Subsystem: Startup-->
<!--Owner: @chenjinxiang3-->
<!--Designer: @chenjinxiang3-->
<!--Tester: @liuhaonan2-->
<!--Adviser: @fang-jinxu-->

The **device** module provides APIs for checking information about the current device.

> **NOTE**
>
> - Module maintenance strategy:
>
>    \- For lite wearables, this module is constantly maintained and available.
>
>     \- For other device types, this module is no longer maintained since API version 6, and you are advised to use [@ohos.deviceInfo](js-apis-device-info.md) to query device information.
>
> - The initial APIs of this module are supported since API version 3. Newly added APIs will be marked with a superscript to indicate their earliest API version.

## Modules to Import

```typescript
import Device from '@system.device';
```
## Device
### Device.getInfo<sup>(deprecated)</sup>

getInfo(options?: GetDeviceOptions): void

Obtains the device information.

> **NOTE**<br>
> Do not call **device.getInfo** before the **onShow** event of the home page.

**System capability**: SystemCapability.Startup.SystemInfo.Lite

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| options | [GetDeviceOptions](#getdeviceoptionsdeprecated) | No| Parameters for obtaining the device information.|

**Example**

ArkTS example:

```typescript
export default class Page {
  getInfo() {
    interface DeviceData {
      brand: string;
    }

    try {
      Device.getInfo({
        success: (data: DeviceData) => {
          console.info('Device information obtained successfully. Device brand:' + data.brand);
        },
        fail: (data: string, code: number) => {
          console.info('Failed to obtain device information. Error code:' + code + '; Error information: ' + data);
        },
      });
    } catch (error) {
      console.error('Device information API is not supported');
    }
  }
}
```

JS example:

```xml
<div class="container">
    <text class="title">Device Information</text>
    <input type="button" value="Get Device Brand" class="button" onclick="getDeviceInfo"></input>
    <text class="info">{{brandInfo}}</text>
</div>
```

```css
/*xxx.css*/
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

```js
//xxx.js
import Device from '@system.device';

export default {
    data: {
        brandInfo: 'Click the button to get device brand'
    },
    
    getDeviceInfo() {
        try {
            Device.getInfo({
                success: (data) => {
                    console.info('Device information obtained successfully. Device brand:' + data.brand);
                    this.brandInfo = 'Device brand: ' + data.brand;
                },
                fail: (data, code) => {
                    console.info('Failed to obtain device information. Error code:' + code + '; Error information: ' + data);
                    this.brandInfo = 'Failed to obtain, error code: ' + code;
                },
            });
        } catch (error) {
            console.error('Device information API is not supported');
            this.brandInfo = 'Current device does not support this API';
        }
    }
}
```

## GetDeviceOptions<sup>(deprecated)</sup>

Defines the parameters for obtaining the device information.

**System capability**: SystemCapability.Startup.SystemInfo.Lite

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| success | (data: DeviceResponse) => void | No| Called when an API call is successful. **data** indicates the returned device information. For details, see [DeviceResponse](#deviceresponsedeprecated).|
| fail | (data: any,code:number)=> void | No| Called when an API call has failed. **code** indicates the error code returned upon a failure.<br>**code:200**: Certain information could not be obtained.|
| complete | () => void | No| Called when an API call is complete.|

## DeviceResponse<sup>(deprecated)</sup>

Defines the device information.

**System capability**: SystemCapability.Startup.SystemInfo.Lite

| Name| Type| Description|
| -------- | -------- | -------- |
| brand | string | Brand.|
| manufacturer | string | Manufacturer.|
| model | string | Model.|
| product | string | Product number.|
| language<sup>4+</sup> | string | System language.|
| region<sup>4+</sup> | string | System region.|
| windowWidth | number | Available window width, in px.|
| windowHeight | number | Available window height, in px.|
| screenDensity<sup>4+</sup> | number | Screen density, in dpi.|
| screenShape<sup>4+</sup> | string | Screen shape. The options are as follows:<br>- **rect**: rectangular screen<br>- **circle**: round screen|
| apiVersion<sup>4+</sup> | number | API version.|
| deviceType<sup>4+</sup> | string | Device type.|
