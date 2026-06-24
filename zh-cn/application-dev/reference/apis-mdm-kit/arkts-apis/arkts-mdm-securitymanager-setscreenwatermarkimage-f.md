# setScreenWatermarkImage

## setScreenWatermarkImage

```TypeScript
function setScreenWatermarkImage(admin: Want, pixelMap: image.PixelMap): void
```

������Ļˮӡ

**起始版本：** 26.0.0

**需要权限：** ohos.permission.ENTERPRISE_MANAGE_SECURITY

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| admin | Want | 是 | ��ҵ�豸������չ��� |
| pixelMap | image.PixelMap | 是 | ˮӡͼƬ��ͼ�������� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [9200001](../../errorcode-universal.md#9200001-The) | The application is not an administrator application of the device. |
| [9200002](../../errorcode-universal.md#9200002-The) | The administrator application does not have permission to manage the device. |
| [9200012](../../errorcode-universal.md#9200012-Parameter) | Parameter verification failed. |
| [201](../../errorcode-universal.md#201-Permission) | Permission verification failed.<br/>The application does not have the permission required to call the API. |

**示例：**

```TypeScript
import { securityManager } from '@kit.MDMKit';
import { common, Want } from '@kit.AbilityKit';
import { image } from '@kit.ImageKit';

let wantTemp: Want = {
  // 需根据实际情况进行替换
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};
// 请在组件内获取context，确保this.getUIContext().getHostContext()返回结果为UIAbilityContext
const context = this.getUIContext().getHostContext() as common.UIAbilityContext;
// 此处'test.png'仅作示例，请开发者自行替换
const path: string = context.filesDir + "/test.png";
// 创建ImageSource
const imageSource: image.ImageSource = image.createImageSource(path);
// 创建PixelMap
imageSource.createPixelMap().then((pixelMap: image.PixelMap) => {
  try {
    securityManager.setScreenWatermarkImage(wantTemp, pixelMap);
    console.info(`Succeeded in setting screen watermark image.`);
  } catch(err) {
    console.error(`Failed to set screen watermark image. Code: ${err.code}, message: ${err.message}`);
  }
}).catch((err: Error) => {
  console.error(`Failed to create PixelMap. message: ${err.message}`);
});

```

