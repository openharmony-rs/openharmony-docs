# setScreenPrivacyMaskImage（系统接口）

## 导入模块

```TypeScript
import { screen } from '@kit.ArkUI';
```

<a id="setscreenprivacymaskimage"></a>
## setScreenPrivacyMaskImage

```TypeScript
function setScreenPrivacyMaskImage(screenId: number, image?: image.PixelMap): Promise<void>
```

设置屏幕的隐私蒙版图片，使用Promise异步回调。

**起始版本：** 19

<!--Device-screen-function setScreenPrivacyMaskImage(screenId: long, image?: image.PixelMap): Promise<void>--><!--Device-screen-function setScreenPrivacyMaskImage(screenId: long, image?: image.PixelMap): Promise<void>-End-->

**系统能力：** SystemCapability.Window.SessionManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| screenId | number | 是 | 屏幕的id，该参数仅支持正整数输入。 |
| image | image.PixelMap | 否 | 屏幕的隐私蒙版图片，不传入则使用默认隐私蒙版图片。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.2. Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported.Failed to call the API due to limited device capabilities. |
| [1400001](../errorcode-display.md#1400001-无效的显示设备) | Invalid display or screen. |
| [1400003](../errorcode-display.md#1400003-系统服务工作异常) | This display manager service works abnormally. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { image } from '@kit.ImageKit';

const color: ArrayBuffer = new ArrayBuffer(96); // 96为需要创建的像素buffer大小，取值为：height * width *4
let options: image.InitializationOptions = { editable: true, pixelFormat: image.PixelMapFormat.RGBA_8888, size: { height: 4, width: 6 } }
image.createPixelMap(color, options).then((pixelMap: image.PixelMap) => {
  console.info('Succeeded in creating pixelmap.');
  // 屏幕ID需通过getAllScreens()获取
  let screenId: number = 1; // 屏幕ID
  // 设置屏幕的隐私蒙版图片
  screen.setScreenPrivacyMaskImage(screenId, pixelMap).then(() => {
    console.info('Succeeded in setting the privacy mask image for the screen.');
  }).catch((err: BusinessError) => {
    console.error(`Failed to set the privacy mask image for the screen. Code: ${err.code}, message: ${err.message}`);
  });
}).catch((error: BusinessError) => {
  console.error(`Failed to create pixelmap. Code: ${error.code}, message: ${error.message}`);
});

```

