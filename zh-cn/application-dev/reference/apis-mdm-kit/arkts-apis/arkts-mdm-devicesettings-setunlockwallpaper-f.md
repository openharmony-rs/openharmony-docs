# setUnlockWallpaper

## 导入模块

```TypeScript
import { deviceSettings } from '@kit.MDMKit';
```

## setUnlockWallpaper

```TypeScript
function setUnlockWallpaper(admin: Want, fd: number):  Promise<void>
```

设置锁屏壁纸，使用Promise异步回调。

**起始版本：** 20

**需要权限：** ohos.permission.ENTERPRISE_SET_WALLPAPER

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-deviceSettings-function setUnlockWallpaper(admin: Want, fd: number):  Promise<void>--><!--Device-deviceSettings-function setUnlockWallpaper(admin: Want, fd: number):  Promise<void>-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| admin | [Want](../../apis-arkui/arkts-apis/arkts-arkui-want-t-sys.md) | 是 | 企业设备管理扩展组件。Want中必须包含企业设备管理扩展能力的abilityName和所在应用的bundleName。 |
| fd | number | 是 | 需要设置为锁屏壁纸图片的文件描述符，可以通过file.fs的[openSync](../../../../reference/apis-core-file-kit/js-apis-file-fs.md#fileioopensync)接口获取应用沙箱目录下的图片文件描述符。壁纸图片大小不能超过100MB。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<void> | 无返回结果的Promise对象。当设置锁屏壁纸失败后会抛出错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [9200001](../errorcode-enterpriseDeviceManager.md#9200001-应用没有激活成设备管理器) | The application is not an administrator application of the device. |
| [9200002](../errorcode-enterpriseDeviceManager.md#9200002-设备管理器权限不够) | The administrator application does not have permission to manage the device. |
| [9200012](../errorcode-enterpriseDeviceManager.md#9200012-参数校验失败) | The parameter validation failed. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed.The application does not have the permission required to call the API |

**示例：**

```TypeScript
import { deviceSettings } from '@kit.MDMKit';
import { common, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { fileIo as fs }  from '@kit.CoreFileKit';

let wantTemp: Want = {
  // 需根据实际情况进行替换
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};

// 请在组件内获取context，确保this.getUIContext().getHostContext()返回结果为UIAbilityContext
const context = this.getUIContext().getHostContext() as common.UIAbilityContext;
// 参数根据实际情况进行替换
let filename: string = "lockwallpaper.jpg";
let filePath: string = context.filesDir + '/' + filename;
let fd: number = fs.openSync(filePath, fs.OpenMode.READ_WRITE).fd;
deviceSettings.setUnlockWallpaper(wantTemp, fd).then(() => {
  console.info('Succeeded in setting lock wallpaper');
}).catch((err: BusinessError) => {
  console.error(`Failed to set lock wallpaper. Code: ${err.code}, message: ${err.message}`);
});

```

