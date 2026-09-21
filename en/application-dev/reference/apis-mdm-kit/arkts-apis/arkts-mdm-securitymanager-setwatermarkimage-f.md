# setWatermarkImage

## Modules to Import

```TypeScript
import { securityManager } from '@kit.MDMKit';
```

## setWatermarkImage

```TypeScript
function setWatermarkImage(admin: Want, bundleName: string, source: string | image.PixelMap, accountId: number): void
```

Sets a watermark policy for a specified application of a specified user. Currently, a maximum of 100 policies can be saved.

> **NOTE:** 
> 
> 1. This API is intended for setting watermarks on third-party applications in enterprise scenarios to reduce the risk of information leakage. You are not advised to set watermarks for system applications (such as the home screen application), as unknown exceptions may occur.
> 
> 2. The watermark image will be tiled repeatedly to cover the entire application interface.

**Since:** 14

**Required permissions:** ohos.permission.ENTERPRISE_MANAGE_SECURITY

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| admin | [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md) | Yes | EnterpriseAdminExtensionAbility. **Want** must contain the ability name of the EnterpriseAdminExtensionAbility and the bundle name of the application. |
| bundleName | string | Yes | Bundle name of the application for which the watermark is set. |
| source | string &#124; [image.PixelMap](../../apis-image-kit/arkts-apis/arkts-image-image-pixelmap-i.md) | Yes | **string** indicates the image path, which is the path that the app has the permission to access, such as the app sandbox path. For details about the mapping between the app sandbox path and the actual physical path, see [Mappings Between App Sandbox Paths and Physical Paths](../../../file-management/app-sandbox-directory.md#mappings-between-application-sandbox-paths-and-physical-paths). <br>**image.PixelMap** indicates the image object. <br>The size of the image pixel data cannot exceed 500 KB. <br>The size of the image pixel data is calculated as follows: Image width (pixels) × Image height (pixels) × Number of bytes per pixel (typically 4). For example, the size of a 100 × 100 image is 100 × 100 × 4 = 40,000 bytes. |
| accountId | number | Yes | User ID. You can call [getOsAccountLocalId](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-osaccount-accountmanager-i.md#getosaccountlocalid) of **@ohos.account.osAccount** to obtain the user ID. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [9200001](../errorcode-enterpriseDeviceManager.md#9200001-deviceadmin-not-enabled) | The application is not an administrator application of the device. |
| [9200002](../errorcode-enterpriseDeviceManager.md#9200002-permission-denied) | The administrator application does not have permission to manage the device. |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Examples**

```TypeScript
import { securityManager } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // Replace with actual values.
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};
// Replace with actual values.
let bundleName: string = 'com.example.myapplication';
let source: string = '/data/storage/el1/base/test.png';
let accountId: number = 100;
try {
  securityManager.setWatermarkImage(wantTemp, bundleName, source, accountId);
  console.info(`Succeeded in setting watermarkImage policy.`);
} catch(err) {
  console.error(`Failed to set watermarkImage policy. Code: ${err.code}, message: ${err.message}`);
}
```


<a id="setwatermarkimage-1"></a>

## setWatermarkImage

```TypeScript
function setWatermarkImage(admin: Want, bundleName: string, source: string | image.PixelMap, accountId: number, properties: WatermarkProperties): void
```

Sets a watermark policy for a specified application of a specified user. Currently, a maximum of 100 policies can be saved.

> **NOTE:** 
> 
> This API is intended for setting watermarks on third-party applications in enterprise scenarios to reduce the
> risk of information leakage. You are not advised to set watermarks for system applications (such as the home
> screen application), as unknown exceptions may occur.
> 
> The row and column parameters in the watermark [properties](arkts-mdm-securitymanager-watermarkproperties-i.md) must be
> integers in the range [1, 255]. If a value less than 1 or greater than 255 is passed, the API returns error code
> 9200012.
> 
> When both the row count and column count are set to **1**, a single watermark image is displayed at the center of
> the screen. When the row count is set to **m** and the column count to **n**, m × n watermark images are
> displayed in an m-by-n grid layout. If the specified row and column counts are too large for the grid layout to
> fit within the window, the watermark will be repeatedly tiled across the entire application window, starting from
> the top-left corner. Any part of the watermark image that exceeds the right or bottom edges of the window will be
> clipped. (For example, for a screen size of 1260 × 2720 pixels and a watermark image of 100 × 100 pixels, if the
> row count exceeds 27 or the column count exceeds 12, the watermark will be repeatedly tiled to cover the entire
> application window.)

**Since:** 26.0.0

**Required permissions:** ohos.permission.ENTERPRISE_MANAGE_SECURITY

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| admin | [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md) | Yes | EnterpriseAdminExtensionAbility. **Want** must contain the ability name of the EnterpriseAdminExtensionAbility and the bundle name of the application. |
| bundleName | string | Yes | Bundle name of the application for which the watermark is set. |
| source | string &#124; [image.PixelMap](../../apis-image-kit/arkts-apis/arkts-image-image-pixelmap-i.md) | Yes | **string** indicates the image path, which is the path that the app has the permission to access, such as the app sandbox path. For details about the mapping between the app sandbox path and the actual physical path, see [Mappings Between App Sandbox Paths and Physical Paths](../../../file-management/app-sandbox-directory.md#mappings-between-application-sandbox-paths-and-physical-paths). <br>**image.PixelMap** indicates the image object. <br>The size of the image pixel data cannot exceed 500 KB. <br>The size of the image pixel data is calculated as follows: Image width (pixels) × Image height (pixels) × Number of bytes per pixel (typically 4). For example, the size of a 100 × 100 image is 100 × 100 × 4 = 40,000 bytes. |
| accountId | number | Yes | User ID, which must be greater than or equal to 0. You can call [getOsAccountLocalId](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-osaccount-accountmanager-i.md#getosaccountlocalid) of **@ohos.account.osAccount** to obtain the user ID. |
| properties | [WatermarkProperties](arkts-mdm-securitymanager-watermarkproperties-i.md) | Yes | Number of rows and columns for the watermark. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [9200001](../errorcode-enterpriseDeviceManager.md#9200001-deviceadmin-not-enabled) | The application is not an administrator application of the device. |
| [9200002](../errorcode-enterpriseDeviceManager.md#9200002-permission-denied) | The administrator application does not have permission to manage the device. |
| [9200012](../errorcode-enterpriseDeviceManager.md#9200012-parameter-verification-failed) | Parameter verification failed. |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |

**Examples**

```TypeScript
import { securityManager } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // Replace with actual values.
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};
// Replace with actual values.
let bundleName: string = 'com.example.myapplication';
let source: string = '/data/storage/el1/base/test.png';
let accountId: number = 100;
// Set them with actual values. In the sample code, the number of rows and the number of columns are both set to 1 for the watermark, and a single watermark image is displayed in the center.
let properties: securityManager.WatermarkProperties = {
  intervalsRow: 1,
  intervalsCol: 1
}
try {
  securityManager.setWatermarkImage(wantTemp, bundleName, source, accountId, properties);
  console.info(`Succeeded in setting watermarkImage policy.`);
} catch(err) {
  console.error(`Failed to set watermarkImage policy. Code: ${err.code}, message: ${err.message}`);
}
```

```TypeScript
import { securityManager } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // Replace with actual values.
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};
// Replace with actual values.
let bundleName: string = 'com.example.myapplication';
let source: string = '/data/storage/el1/base/test.png';
let accountId: number = 100;
// Set them with actual values. The device screen size is 1260 × 2720, and the watermark image size is 100 × 100. In this example, the watermark properties are set to 27 rows and 12 columns, displaying 27 × 12 watermark images in a 27-row by 12-column grid layout.
let properties: securityManager.WatermarkProperties = {
  intervalsRow: 27,
  intervalsCol: 12
}
try {
  securityManager.setWatermarkImage(wantTemp, bundleName, source, accountId, properties);
  console.info(`Succeeded in setting watermarkImage policy.`);
} catch(err) {
  console.error(`Failed to set watermarkImage policy. Code: ${err.code}, message: ${err.message}`);
}
```

```TypeScript
import { securityManager } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // Replace with actual values.
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};
// Replace with actual values.
let bundleName: string = 'com.example.myapplication';
let source: string = '/data/storage/el1/base/test.png';
let accountId: number = 100;
// Set them with actual values. The device screen size is 1260 × 2720, and the watermark image size is 100 × 100. In this example, the watermark properties are set to 28 rows and 12 columns. Since 28 × 100 > 2720, the grid layout cannot fit within the window. As a result, the watermark will be repeatedly tiled across the entire application window, starting from the top-left corner. Any watermark image that exceeds the right or bottom edges of the window will be clipped.
let properties: securityManager.WatermarkProperties = {
  intervalsRow: 28,
  intervalsCol: 12
}
try {
  securityManager.setWatermarkImage(wantTemp, bundleName, source, accountId, properties);
  console.info(`Succeeded in setting watermarkImage policy.`);
} catch(err) {
  console.error(`Failed to set watermarkImage policy. Code: ${err.code}, message: ${err.message}`);
}
```
