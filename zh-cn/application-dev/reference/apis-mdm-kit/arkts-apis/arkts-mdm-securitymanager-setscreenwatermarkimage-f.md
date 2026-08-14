# setScreenWatermarkImage

## setScreenWatermarkImage

```TypeScript
function setScreenWatermarkImage(admin: Want, pixelMap: image.PixelMap): void
```

设置屏幕水印策略，对所有用户生效。 > **说明：** > > 1.屏幕水印策略会将设置的图片平铺覆盖整个屏幕，建议使用带透明度的图片以确保设备屏幕内容可见。 > > 2.当水印图片尺寸小于屏幕时，图片会被拉伸；当水印图片尺寸大于屏幕时，图片会被压缩。该实现方式与应用级别水印的重复平铺方式不同。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**需要权限：** ohos.permission.ENTERPRISE_MANAGE_SECURITY

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-securityManager-function setScreenWatermarkImage(admin: Want, pixelMap: image.PixelMap): void--><!--Device-securityManager-function setScreenWatermarkImage(admin: Want, pixelMap: image.PixelMap): void-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| admin | [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md) | 是 | 企业设备管理扩展组件。Want中必须包含企业设备管理扩展能力的abilityName和所在应用的bundleName。 |
| pixelMap | image.PixelMap | 是 | 图像对象。图片宽度不超过设备屏幕宽度的两倍，图片高度不超过设备屏幕高度的两倍。图片像素占用大小不得超过128MB。图片像素占用大小计算公式：图片宽度(像素) ×图片高度(像素)×每个像素占用的字节数（通常为4）。例如：一张100×100的图片，像素占用大小为100×100×4=40000字节。对于1920×1080分辨率的屏幕，若使用相同分辨率的图片，像素占用大小为1920×1 080×4=8294400字节（约7.9MB）。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [9200012](../errorcode-enterpriseDeviceManager.md#9200012-参数校验失败) | Parameter verification failed. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [9200001](../errorcode-enterpriseDeviceManager.md#9200001-应用没有激活成设备管理器) | The application is not an administrator application of the device. |
| [9200002](../errorcode-enterpriseDeviceManager.md#9200002-设备管理器权限不够) | The administrator application does not have permission to manage the device. |

## 示例

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

