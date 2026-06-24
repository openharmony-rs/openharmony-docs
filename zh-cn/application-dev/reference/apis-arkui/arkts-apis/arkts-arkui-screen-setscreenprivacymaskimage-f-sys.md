# setScreenPrivacyMaskImage（系统接口）

## setScreenPrivacyMaskImage

```TypeScript
function setScreenPrivacyMaskImage(screenId: number, image?: image.PixelMap): Promise<void>
```

������Ļ����˽�ɰ�ͼƬ��ʹ��Promise�첽�ص���

**起始版本：** 19

**系统能力：** SystemCapability.Window.SessionManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| screenId | number | 是 | ��Ļ��id���ò�����֧�����������롣 |
| image | image.PixelMap | 否 | ��Ļ����˽�ɰ�ͼƬ����������ʹ��Ĭ����˽�ɰ�ͼƬ�� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | �޷��ؽ����Promise���� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-Permission) | Permission verification failed. A non-system application calls a system API. |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br/>2. Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-Capability) | Capability not supported.<br/>Failed to call the API due to limited device capabilities. |
| [1400001](../../errorcode-universal.md#1400001-Invalid) | Invalid display or screen. |
| [1400003](../../errorcode-universal.md#1400003-This) | This display manager service works abnormally. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { image } from '@kit.ImageKit';

const color: ArrayBuffer = new ArrayBuffer(96); // 96为需要创建的像素buffer大小，取值为：height * width *4
let opts: image.InitializationOptions = { editable: true, pixelFormat: image.PixelMapFormat.RGBA_8888, size: { height: 4, width: 6 } }
image.createPixelMap(color, opts).then((pixelMap: image.PixelMap) => {
  console.info('Succeeded in creating pixelmap.');
  let screenId: number = 1;
  screen.setScreenPrivacyMaskImage(screenId, pixelMap).then(() => {
    console.info('Succeeded in setting the privacy mask image for the screen.');
  }).catch((err: BusinessError) => {
    console.error(`Failed to set the privacy mask image for the screen. Code:${err.code}, message is ${err.message}`);
  });
}).catch((error: BusinessError) => {
  console.error(`Failed to create pixelmap. code is ${error.code}, message is ${error.message}`);
})

```

