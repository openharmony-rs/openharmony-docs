# saveHdrPicture（系统接口）

## saveHdrPicture

```TypeScript
function saveHdrPicture(options?: HdrScreenshotOptions): Promise<Array<image.PixelMap>>
```

��ȡ��Ļ��ͼ��ʹ��Promise�첽�ص���SDRΪ��׼��̬��Χͼ��HDRΪ�߶�̬��Χͼ��

- ������������HDR��Դ������HDR��Դ���ڵ���ʱ������HDR�Ƿ������ýӿڷ���һ������SDR��HDR��PixelMap���顣
- ��������������HDR��Դʱ����[save](arkts-arkui-screenshot-save-f-sys.md#save-1)
�ӿڷ���һ��SDR��PixelMap��ͬ���ýӿڷ��ذ���һ��SDR��PixelMap���顣ͬʱ�ýӿڲ��߱�
[save](arkts-arkui-screenshot-save-f-sys.md#save-1)�ӿڵĲü������졢��ת���ܡ�

**起始版本：** 20

**需要权限：** ohos.permission.CAPTURE_SCREEN, ohos.permission.CAPTURE_SCREEN or ohos.permission.CUSTOM_SCREEN_RECORDING

**系统能力：** SystemCapability.Window.SessionManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | HdrScreenshotOptions | 否 | Ҫ��ȡ��HDRͼ����Ϣ��Ĭ��Ϊ�ա� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;image.PixelMap&gt;&gt; | Promise used to return an array of PixelMap objects. If the screen<br/>contains HDR resources (even if they are partially obscured), the array contains two PixelMaps: the first is an<br/>SDR PixelMap, and the second is an HDR PixelMap. If there are no HDR resources, the array contains a single SDR<br/>PixelMap. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-Permission) | Permission verification failed. The application does not have the permission<br/>required to call the API. |
| [202](../../errorcode-universal.md#202-Permission) | Permission verification failed. A non-system application calls a system API. |
| [801](../../errorcode-universal.md#801-Capability) | Capability not supported. Failed to call the API due to limited device<br/>capabilities. |
| [1400001](../../errorcode-universal.md#1400001-Invalid) | Invalid display or screen. |
| [1400003](../../errorcode-universal.md#1400003-This) | This display manager service works abnormally. |
| [1400004](../../errorcode-universal.md#1400004-Parameter) | Parameter error. Possible cause: 1.Invalid parameter range. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { image } from '@kit.ImageKit';

let hdrScreenshotOptions: screenshot.HdrScreenshotOptions = {
  "displayId": 0,
  "isNotificationNeeded": true,
  "isCaptureFullOfScreen": true,
  "displayIntent": screenshot.DisplayIntentType.CANONICAL
};
try {
  let promise = screenshot.saveHdrPicture(hdrScreenshotOptions);
  promise.then((pixelMapArray: Array<image.PixelMap>) => {
    for (let i = 0; i < pixelMapArray.length; i++) {
      const pixelMap = pixelMapArray[i];
      console.info('succeeded in saving screenshot ${i}. Pixel bytes number' + pixelMap.getPixelBytesNumber());
      pixelMap.release();
    }
  }).catch((err: BusinessError) => {
    console.error(`Failed to save SDR and HDR screenshot. Code: ${err.code} , message : ${err.message}`);
  });
} catch (exception) {
  console.error(`Failed to save SDR and HDR screenshot. Code: ${exception.code} , message : ${exception.message}`);
};

```

