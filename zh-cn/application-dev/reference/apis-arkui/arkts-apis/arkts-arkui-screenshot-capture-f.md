# capture

## capture

```TypeScript
function capture(options?: CaptureOption): Promise<image.PixelMap>
```

��ȡ��Ļȫ����ͼ��ʹ��Promise�첽�ص���

�˽ӿڿ���ͨ�����ò�ͬ��displayId��ȡ��ͬ��Ļ�Ľ�ͼ����ֻ�ܽ�ȡȫ����[pick](arkts-arkui-screenshot-pick-f.md#pick-1)�ӿڿ�ʵ�����������

**起始版本：** 14

**需要权限：** ohos.permission.CUSTOM_SCREEN_CAPTURE, ohos.permission.CUSTOM_SCREEN_CAPTURE or ohos.permission.CUSTOM_SCREEN_RECORDING

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | CaptureOption | 否 | ��ȡͼ��������Ϣ���˲�������ʱ��Ĭ�Ͻ�ȡdisplayIdΪ0����Ļ��ͼ�� [since 22] |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;image.PixelMap&gt; | Promise used to return a PixelMap object. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-Permission) | Permission verification failed.<br/>The application does not have the permission required to call the API. |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes:<br/>1.Incorrect parameter types.<br/>2.Parameter verification failed. |
| [801](../../errorcode-universal.md#801-Capability) | Capability not supported on this device. |
| [1400003](../../errorcode-universal.md#1400003-This) | This display manager service works abnormally. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { image } from '@kit.ImageKit';

let captureOption: screenshot.CaptureOption = {
  "displayId": 0
};
try {
  let promise = screenshot.capture(captureOption);
  promise.then((pixelMap: image.PixelMap) => {
    console.info('Succeeded in saving screenshot. Pixel bytes number: ' + pixelMap.getPixelBytesNumber());
    pixelMap.release(); // PixelMap使用完后及时释放内存
  }).catch((err: BusinessError) => {
    console.error(`Failed to save screenshot. Code: ${err.code}, message: ${err.message}`);
  });
} catch (exception) {
  console.error(`Failed to save screenshot. Code: ${exception.code}, message: ${exception.message}`);
};

```

