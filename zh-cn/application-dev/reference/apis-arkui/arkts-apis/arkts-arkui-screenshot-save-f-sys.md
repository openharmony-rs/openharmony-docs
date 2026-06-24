# save（系统接口）

## save

```TypeScript
function save(options: ScreenshotOptions, callback: AsyncCallback<image.PixelMap>): void
```

��ȡ��Ļ��ͼ��ʹ��callback�첽�ص���

**起始版本：** 7

**需要权限：** ohos.permission.CAPTURE_SCREEN, ohos.permission.CAPTURE_SCREEN or ohos.permission.CUSTOM_SCREEN_RECORDING

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | ScreenshotOptions | 是 | Ҫ��ȡ��ͼ����Ϣ����ָ����ȡ��ĻΪ������ʱ����ȡͼ��Ϊ������ |
| callback | AsyncCallback&lt;image.PixelMap&gt; | 是 | �ص�����������һ��PixelMap�������СΪָ����imageSize��С����δָ��Ĭ��ΪdisplayId�����߼����Ĵ�С�� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-Permission) | Permission verification failed.<br/>The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-Permission) | Permission verification failed. A non-system application calls a system<br/>API.&lt;br&gt;**适用版本：** 11+ |
| [1400001](../../errorcode-universal.md#1400001-Invalid) | Invalid display or screen.&lt;br&gt;**适用版本：** 11+ |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import  { image } from '@kit.ImageKit';

let screenshotOptions: screenshot.ScreenshotOptions = {
  "screenRect": {
    "left": 200,
    "top": 100,
    "width": 200,
    "height": 200 },
  "imageSize": {
    "width": 300,
    "height": 300 },
  "rotation": 0,
  "displayId": 0,
  "isNotificationNeeded": true,
  "isCaptureFullOfScreen": true
};
screenshot.save(screenshotOptions, (err: BusinessError, pixelMap: image.PixelMap) => {
  if (err) {
    console.error(`Failed to save screenshot. Code: ${err.code} , message : ${err.message}`);
    return;
  }
  console.info('Succeeded in saving screenshot. Pixel bytes number: ' + pixelMap.getPixelBytesNumber());
  pixelMap.release(); // PixelMap使用完后及时释放内存
});

```


## save

```TypeScript
function save(callback: AsyncCallback<image.PixelMap>): void
```

��ȡ��Ļ��ͼ��ʹ��callback�첽�ص���

**起始版本：** 7

**需要权限：** ohos.permission.CAPTURE_SCREEN, ohos.permission.CAPTURE_SCREEN or ohos.permission.CUSTOM_SCREEN_RECORDING

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | AsyncCallback&lt;image.PixelMap&gt; | 是 | �ص�����������һ��PixelMap���� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-Permission) | Permission verification failed. The application does not have the permission<br/>required to call the API. |
| [202](../../errorcode-universal.md#202-Permission) | Permission verification failed. A non-system application calls a system API. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { image } from '@kit.ImageKit';

screenshot.save((err: BusinessError, pixelMap: image.PixelMap) => {
  if (err) {
    console.error(`Failed to save screenshot. Code: ${err.code} , message : ${err.message}`);
    return;
  }
  console.info('Succeeded in saving screenshot. Pixel bytes number: ' + pixelMap.getPixelBytesNumber());
  pixelMap.release(); // PixelMap使用完后及时释放内存
});

```


## save

```TypeScript
function save(options?: ScreenshotOptions): Promise<image.PixelMap>
```

��ȡ��Ļ��ͼ��ʹ��Promise�첽�ص���

**起始版本：** 7

**需要权限：** ohos.permission.CAPTURE_SCREEN, ohos.permission.CAPTURE_SCREEN or ohos.permission.CUSTOM_SCREEN_RECORDING

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | ScreenshotOptions | 否 | Ҫ��ȡ��ͼ����Ϣ����ָ����ȡ��ĻΪ������ʱ����ȡͼ��Ϊ������ [since 22] |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;image.PixelMap&gt; | Promise used to return a PixelMap object. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-Permission) | Permission verification failed.<br/>The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-Permission) | Permission verification failed. A non-system application calls a system API. |
| [1400001](../../errorcode-universal.md#1400001-Invalid) | Invalid display or screen. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { image } from '@kit.ImageKit';

let screenshotOptions: screenshot.ScreenshotOptions = {
  "screenRect": {
    "left": 200,
    "top": 100,
    "width": 200,
    "height": 200 },
  "imageSize": {
    "width": 300,
    "height": 300 },
  "rotation": 0,
  "displayId": 0,
  "isNotificationNeeded": true,
  "isCaptureFullOfScreen": true
};
try {
  let promise = screenshot.save(screenshotOptions);
  promise.then((pixelMap: image.PixelMap) => {
    let pixelNumber = pixelMap.getPixelBytesNumber();
    console.info(`Succeeded in saving screenshot. Pixel bytes number: ${pixelNumber}`);
    pixelMap.release(); // PixelMap使用完后及时释放内存
  }).catch((err: BusinessError) => {
    console.error(`Failed to save screenshot. Code: ${err.code} , message : ${err.message}`);
  });
} catch (exception) {
  console.error(`Failed to save screenshot. Code: ${exception.code} , message : ${exception.message}`);
};

```

