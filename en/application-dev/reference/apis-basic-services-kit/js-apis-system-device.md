# @system.device (Device Information)
<!--Kit: Basic Services Kit-->
<!--Subsystem: Startup-->
<!--Owner: @chenjinxiang3-->
<!--Designer: @chenjinxiang3-->
<!--Tester: @liuhaonan2-->
<!--Adviser: @fang-jinxu-->
<!-- md-trans-meta sourceCommit=454dfe4281e84492b6b293a96c820eee9e3d0c18 translatedAt=2026-09-01T08:20:04.743Z pushedAt=2026-09-02T05:47:27.155Z -->

This module provides information about the current device. It reads system configurations to obtain basic information such as the device brand, model, manufacturer, and screen parameters, which can be used for device adaptation and function determination.

> **NOTE**
>
> - Module maintenance strategy:
>
>    \- For lite wearables, this module is constantly maintained and available.
>
>     \- For other device types, this module is no longer maintained since API version 6, and you are advised to use [@ohos.deviceInfo](js-apis-device-info.md) (supported since API version 6) to query device information.
>
> - The initial APIs of this module are supported since API version 3. Newly added APIs will be marked with a superscript to indicate their earliest API version.

## Modules to Import

```typescript
import Device from '@system.device';
```
## Device
### Device.getInfo<sup>(deprecated)</sup>

getInfo(options?: GetDeviceOptions): void

Obtains the device information. This API asynchronously reads the system device information and uses a callback to return the device brand, model, screen parameters, and other data.

> **NOTE**<br>
> Do not call **Device.getInfo** before the **onShow** event of the home page.

**System capability**: SystemCapability.Startup.SystemInfo.Lite

**Return value**

| Type | Description |
| -------- | -------- |
| void | No return value. The device information is returned through a callback function. |

**Parameters**

| Name | Type | Required | Description |
| -------- | -------- | -------- | -------- |
| options | [GetDeviceOptions](#getdeviceoptionsdeprecated) | No | Parameters for obtaining the device information. If the parameters are not specified, the default configuration is used to obtain basic device information. |

**Example**

ArkTS example:

```typescript
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

```xml
<div class="container">
    <text class="title">Device Information</text>
    <input type="button" value="Get Device Brand" class="button" onclick="getDeviceInfo"></input>
    <text class="info">{{brandInfo}}</text>
</div>
```

```css
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

```js
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

## GetDeviceOptions<sup>(deprecated)</sup>

Defines the parameters for obtaining the device information.

**System capability**: SystemCapability.Startup.SystemInfo.Lite

| Name | Type | Required | Description |
| -------- | -------- | -------- | -------- |
| success | (data: [DeviceResponse](#deviceresponsedeprecated)) => void | No | Callback invoked when the API call is successful. **data** is the device information returned. If this parameter is not passed, the device information cannot be obtained. You are advised to set this callback. |
| fail | (data: any, code: number) => void | No | Callback invoked when the API call fails. **data** is the error object or error description string, and **code** is the error code. **code:200**: Certain information cannot be obtained. You are advised to set this callback to handle errors. |
| complete | () => void | No | Callback invoked when the API call is complete (regardless of whether the call is successful or fails). This callback can be used in the cleanup or finalization work. If this parameter is not passed, the callback will not be executed when the API call is complete. |

**Error codes**

| ID | Error Message |
| --- | --- |
| 200 | Certain information cannot be obtained. Possible causes are as follows: the device does not support some information fields, the system permission is restricted, or the device configuration is missing. Solution: You are advised to check the device compatibility, confirm the app permission configuration, and set this callback to handle errors. |

## DeviceResponse<sup>(deprecated)</sup>

Defines the device profile information.

**System capability**: SystemCapability.Startup.SystemInfo.Lite

| Name | Type | Description |
| -------- | -------- | -------- |
| brand | string | Brand. |
| manufacturer | string | Manufacturer. |
| model | string | Model. |
| product | string | Product code. |
| language<sup>4+</sup> | string | System language. |
| region<sup>4+</sup> | string | System region. |
| windowWidth | number | Available window width, in px. The available window size varies on different devices. |
| windowHeight | number | Available window height, in px. The available window size varies on different devices. |
| screenDensity<sup>4+</sup> | number | Screen pixel density, which indicates the number of pixels per inch on the screen, in dots per inch (DPI). The screen pixel density varies depending on the device. |
| screenShape<sup>4+</sup> | string | Screen shape. The options are as follows:<br>-&nbsp;**rect**: rectangular screen<br>-&nbsp;**circle**: round screen |
| apiVersion<sup>4+</sup> | number | API version. |
| deviceType<sup>4+</sup> | string | Device type. The options are as follows: **phone**, **tablet**, **tv**, and **wearable**. |
| sdkMinorApiVersion | number  | SDK minor API version. Since API version 26.0.0, the API version is in the format of **apiVersion.sdkMinorApiVersion.sdkPatchApiVersion**. If the value fails to be obtained, **-1** is returned, which does not affect the overall return status of the **getInfo** API.<br/>**Model constraint:** This API can be used only in the FA model.<br/>**Since version**: 26.0.0<br/>Example: 0 |
| sdkPatchApiVersion  | number  | SDK patch API version. Since API version 26.0.0, the API version is in the format of **apiVersion.sdkMinorApiVersion.sdkPatchApiVersion**. If the value fails to be obtained, **-1** is returned, which does not affect the overall return status of the **getInfo** API.<br/>**Model constraint:** This API can be used only in the FA model.<br/>**Since version**: 26.0.0<br/>Example: 0 |