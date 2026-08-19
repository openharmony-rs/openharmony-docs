# setWatermarkImage

## 导入模块

```TypeScript
import { securityManager } from '@kit.MDMKit';
```

## setWatermarkImage

```TypeScript
function setWatermarkImage(admin: Want, bundleName: string, source: string | image.PixelMap, accountId: number): void
```

为指定用户的指定应用设置水印策略。当前只支持最多保存100个策略。 > **说明：** > > 1.本接口适用于企业场景下为三方应用设置水印，降低企业信息泄露风险。不建议为系统应用设置水印（如：桌面应用），可能存在未知异常。 > > 2.水印图片会以平铺方式重复覆盖整个应用界面。

**起始版本：** 14

**需要权限：** ohos.permission.ENTERPRISE_MANAGE_SECURITY

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-securityManager-function setWatermarkImage(admin: Want, bundleName: string, source: string | image.PixelMap, accountId: number): void--><!--Device-securityManager-function setWatermarkImage(admin: Want, bundleName: string, source: string | image.PixelMap, accountId: number): void-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| admin | [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md) | 是 | 企业设备管理扩展组件。Want中必须包含企业设备管理扩展能力的abilityName和所在应用的bundleName。 |
| bundleName | string | 是 | 被设置水印的应用包名。 |
| source | string \| image.PixelMap | 是 | string表示图像路径，图像路径为应用沙箱路径(应用沙箱路径和真实路径的对应关系可参见： [应用沙箱路径和真实物理路径的对应关系](../../../file-management/app-sandbox-directory.md#应用沙箱路径和真实物理路径的对应关系))等应用有权限访问的路径。 <br>image.PixelMap表示图像对象。 <br>图像像素占用大小不得超过500KB。 <br>图像像素占用大小计算公式：图像宽度(像素)×图像高度 (像素)×每个像素占用的字节数（通常为4）。例如：一张 100x100 的图片，图像像素占用大小为100×100×4=40000字节。 |
| accountId | number | 是 | 用户ID。accountId可以通过@ohos.account.osAccount中的 [getOsAccountLocalId](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-osaccount-accountmanager-i.md#getosaccountlocalid)等接口来获取。*@ohos.account.osAccount** to obtain the user ID. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [9200001](../errorcode-enterpriseDeviceManager.md#9200001-应用没有激活成设备管理器) | The application is not an administrator application of the device. |
| [9200002](../errorcode-enterpriseDeviceManager.md#9200002-设备管理器权限不够) | The administrator application does not have permission to manage the device. |

**示例**

```TypeScript
import { securityManager } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // 需根据实际情况进行替换
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};
// 需根据实际情况进行替换
let bundleName: string = 'com.example.myapplication';
let source: string = '/data/storage/el1/base/test.png';
let accountId: number = 100;
try {
  securityManager.setWatermarkImage(wantTemp, bundleName, source, accountId);
  console.info(`Succeeded in setting watermarkImage policy.`);
} catch (err) {
  console.error(`Failed to set watermarkImage policy. Code: ${err.code}, message: ${err.message}`);
}
```


## setWatermarkImage

```TypeScript
function setWatermarkImage(admin: Want, bundleName: string, source: string | image.PixelMap, accountId: number, properties: WatermarkProperties): void
```

为指定用户的指定应用设置水印策略。当前只支持最多保存100个策略。 > **说明：** > > 本接口适用于企业场景下为三方应用设置水印，降低企业信息泄露风险。不建议为系统应用设置水印（如：桌面应用），可能存在未知异常。 > > 当水印属性[properties](arkts-mdm-securitymanager-watermarkproperties-i.md)行列参数的取值范围是[1, 255]内的整数。若传入小于1或大于255的值，接口会返回错误码920001 > 2。 > > 当水印属性行数和列数都为1时，居中显示单个水印图片。当水印属性行数为m，列数为n时，按m行n列的网格布局排列显示m\*n个水印图片。当水印属性行列参数过大，导致网格布局无法适应窗口大小时，水印会以窗口左上角为原点，以平铺方式重 > 复覆盖整个应用窗口界面，水印图片超出界面右侧、下侧的部分会被裁剪（例如屏幕宽高是1260\*2720，水印图片宽高是100\*100，若设置的行数超过27，或设置的列数超过12，水印会以平铺方式重复覆盖整个应用窗口界面）。

**起始版本：** 26.0.0

**需要权限：** ohos.permission.ENTERPRISE_MANAGE_SECURITY

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-securityManager-function setWatermarkImage(admin: Want, bundleName: string, source: string | image.PixelMap, accountId: number, properties: WatermarkProperties): void--><!--Device-securityManager-function setWatermarkImage(admin: Want, bundleName: string, source: string | image.PixelMap, accountId: number, properties: WatermarkProperties): void-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| admin | [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md) | 是 | 企业设备管理扩展组件。Want中必须包含企业设备管理扩展能力的abilityName和所在应用的bundleName。 |
| bundleName | string | 是 | 被设置水印的应用包名。 |
| source | string \| image.PixelMap | 是 | string表示图像路径，图像路径为应用沙箱路径(应用沙箱路径和真实路径的对应关系可参见： [应用沙箱路径和真实物理路径的对应关系](../../../file-management/app-sandbox-directory.md#应用沙箱路径和真实物理路径的对应关系))等应用有权限访问的路径。 <br>image.PixelMap表示图像对象。 <br>图像像素占用大小不得超过500KB。 <br>图像像素占用大小计算公式：图像宽度(像素)×图像高度 (像素)×每个像素占用的字节数（通常为4）。例如：一张 100x100 的图片，图像像素占用大小为100×100×4=40000字节。 |
| accountId | number | 是 | 用户ID，指定具体用户，取值范围：大于等于0。accountId可以通过@ohos.account.osAccount中的 [getOsAccountLocalId](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-osaccount-accountmanager-i.md#getosaccountlocalid)等接口来获取。*@ohos.account.osAccount** to obtain the user ID. |
| properties | [WatermarkProperties](arkts-mdm-securitymanager-watermarkproperties-i.md) | 是 | 配置水印的行列数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [9200012](../errorcode-enterpriseDeviceManager.md#9200012-参数校验失败) | Parameter verification failed. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [9200001](../errorcode-enterpriseDeviceManager.md#9200001-应用没有激活成设备管理器) | The application is not an administrator application of the device. |
| [9200002](../errorcode-enterpriseDeviceManager.md#9200002-设备管理器权限不够) | The administrator application does not have permission to manage the device. |

**示例**

```TypeScript
import { securityManager } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // 需根据实际情况进行替换
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};
// 需根据实际情况进行替换
let bundleName: string = 'com.example.myapplication';
let source: string = '/data/storage/el1/base/test.png';
let accountId: number = 100;
// 需根据实际情况进行替换。示例代码水印属性行数和列数都设为1，会居中显示单个水印图片
let properties: securityManager.WatermarkProperties = {
  intervalsRow: 1,
  intervalsCol: 1
};
try {
  securityManager.setWatermarkImage(wantTemp, bundleName, source, accountId, properties);
  console.info(`Succeeded in setting watermarkImage policy.`);
} catch (err) {
  console.error(`Failed to set watermarkImage policy. Code: ${err.code}, message: ${err.message}`);
}
```

```TypeScript
import { securityManager } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // 需根据实际情况进行替换
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};
// 需根据实际情况进行替换
let bundleName: string = 'com.example.myapplication';
let source: string = '/data/storage/el1/base/test.png';
let accountId: number = 100;
// 需根据实际情况进行替换。设备屏幕宽高是1260*2720，水印图片宽高是100*100，示例代码水印属性行数为27，列数为12，按27行12列的网格布局排列显示27*12个水印图片
let properties: securityManager.WatermarkProperties = {
  intervalsRow: 27,
  intervalsCol: 12
};
try {
  securityManager.setWatermarkImage(wantTemp, bundleName, source, accountId, properties);
  console.info(`Succeeded in setting watermarkImage policy.`);
} catch (err) {
  console.error(`Failed to set watermarkImage policy. Code: ${err.code}, message: ${err.message}`);
}
```

```TypeScript
import { securityManager } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // 需根据实际情况进行替换
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};
// 需根据实际情况进行替换
let bundleName: string = 'com.example.myapplication';
let source: string = '/data/storage/el1/base/test.png';
let accountId: number = 100;
// 需根据实际情况进行替换。设备屏幕宽高是1260*2720，水印图片宽高是100*100，示例代码水印属性行数为28，列数为12，28 * 100 > 2720，网格布局无法适应窗口大小，水印会以窗口左上角为原点，以平铺方式重复覆盖整个应用窗口界面，超出界面右侧、下侧的水印图片会被裁剪
let properties: securityManager.WatermarkProperties = {
  intervalsRow: 28,
  intervalsCol: 12
};
try {
  securityManager.setWatermarkImage(wantTemp, bundleName, source, accountId, properties);
  console.info(`Succeeded in setting watermarkImage policy.`);
} catch (err) {
  console.error(`Failed to set watermarkImage policy. Code: ${err.code}, message: ${err.message}`);
}
```

