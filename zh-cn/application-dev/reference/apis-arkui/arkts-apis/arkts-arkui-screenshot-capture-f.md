# capture

## 导入模块

```TypeScript
import { screenshot } from '@kit.ArkUI';
```

## capture

```TypeScript
function capture(options?: CaptureOption): Promise<image.PixelMap>
```

获取屏幕全屏截图，使用Promise异步回调。

此接口可以通过设置不同的displayId截取不同屏幕的截图，且只能截取全屏；[pick](arkts-arkui-screenshot-pick-f.md#pick)接口可实现区域截屏。

**起始版本：** 14

**需要权限：** 
- API版本22+：ohos.permission.CUSTOM_SCREEN_CAPTURE or ohos.permission.CUSTOM_SCREEN_RECORDING
- API版本14 - 21：ohos.permission.CUSTOM_SCREEN_CAPTURE

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

<!--Device-screenshot-function capture(options?: CaptureOption): Promise<image.PixelMap>--><!--Device-screenshot-function capture(options?: CaptureOption): Promise<image.PixelMap>-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [CaptureOption](arkts-arkui-screenshot-captureoption-i.md) | 否 | 截取图像的相关信息。此参数不填时，默认截取displayId为0的屏幕截图。<br>**起始版本：** 22 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;image.PixelMap&gt; | Promise used to return a PixelMap object. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed.The application does not have the permission required to call the API. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1.Incorrect parameter types.2.Parameter verification failed. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported on this device. |
| [1400003](../errorcode-display.md#1400003-系统服务工作异常) | This display manager service works abnormally. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { image } from '@kit.ImageKit';

// 配置截图参数，指定截取displayId为0的屏幕
let captureOption: screenshot.CaptureOption = {
  "displayId": 0
};
try {
  // 调用capture接口获取全屏截图
  let promise = screenshot.capture(captureOption);
  promise.then((pixelMap: image.PixelMap) => {
    console.info(`Succeeded in saving screenshot. Pixel bytes number: ${pixelMap.getPixelBytesNumber()}`);
    pixelMap.release(); // PixelMap使用完后及时释放内存
  }).catch((err: BusinessError) => {
    console.error(`Failed to save screenshot. Code: ${err.code}, message: ${err.message}`);
  });
} catch (exception) {
  console.error(`Failed to save screenshot. Code: ${exception.code}, message: ${exception.message}`);
}

```

