# save（系统接口）

## save

```TypeScript
function save(options: ScreenshotOptions, callback: AsyncCallback<image.PixelMap>): void
```

获取屏幕截图，使用callback异步回调。

**起始版本：** 7

**ArkTS模式：** ArkTS-Dyn起始版本为7；ArkTS-Sta起始版本为23。

**需要权限：** 
- API版本26.0.0+：ohos.permission.CUSTOM_SCREEN_CAPTURE or ohos.permission.CAPTURE_SCREEN or ohos.permission.CUSTOM_SCREEN_RECORDING
- API版本22 - 24：ohos.permission.CAPTURE_SCREEN or ohos.permission.CUSTOM_SCREEN_RECORDING
- API版本7 - 21：ohos.permission.CAPTURE_SCREEN

<!--Device-screenshot-function save(options: ScreenshotOptions, callback: AsyncCallback<image.PixelMap>): void--><!--Device-screenshot-function save(options: ScreenshotOptions, callback: AsyncCallback<image.PixelMap>): void-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 要截取的图像信息。当指定截取屏幕为虚拟屏时，截取图像为白屏。 |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;image.PixelMap&gt; | 是 | 回调函数。返回一个PixelMap对象，其大小为指定的imageSize大小，若未指定默认为displayId所在逻辑屏的大小。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed.The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 11+ |
| [1400001](../errorcode-display.md#1400001-无效的显示设备) | Invalid display or screen.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 11+ |

**示例：**

ArkTS-Dyn示例：

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { image } from '@kit.ImageKit';

let screenshotOptions: screenshot.ScreenshotOptions = {
  screenRect: {
    left: 200,
    top: 100,
    width: 200,
    height: 200 },
  imageSize: {
    width: 300,
    height: 300 },
  rotation: 0,
  displayId: 0,
  isNotificationNeeded: true,
  isCaptureFullOfScreen: true
};
// 调用save方法获取屏幕截图
screenshot.save(screenshotOptions, (err: BusinessError, pixelMap: image.PixelMap) => {
  if (err) {
    console.error(`Failed to save screenshot. Code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info(`Succeeded in saving screenshot. Pixel bytes number: ${pixelMap.getPixelBytesNumber()}`);
  pixelMap.release(); // PixelMap使用完后及时释放内存
});
```

ArkTS-Sta示例：

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
screenshot.save(screenshotOptions, (err: BusinessError | null, pixelMap: image.PixelMap | undefined) => {
  const errCode = err?.code;
  if (errCode) {
    console.error(`Failed to save screenshot. Code: ${err?.code}, message : ${err?.message}`);
    return;
  }
  console.info(`Succeeded in saving screenshot. Pixel bytes number: ${pixelMap?.getPixelBytesNumber()}`);
  pixelMap?.release(); // PixelMap使用完后及时释放内存
});
```


## save

```TypeScript
function save(callback: AsyncCallback<image.PixelMap>): void
```

获取屏幕截图，使用callback异步回调。

**起始版本：** 7

**ArkTS模式：** ArkTS-Dyn起始版本为7；ArkTS-Sta起始版本为23。

**需要权限：** 
- API版本26.0.0+：ohos.permission.CUSTOM_SCREEN_CAPTURE or ohos.permission.CAPTURE_SCREEN or ohos.permission.CUSTOM_SCREEN_RECORDING
- API版本22 - 24：ohos.permission.CAPTURE_SCREEN or ohos.permission.CUSTOM_SCREEN_RECORDING
- API版本7 - 21：ohos.permission.CAPTURE_SCREEN

<!--Device-screenshot-function save(callback: AsyncCallback<image.PixelMap>): void--><!--Device-screenshot-function save(callback: AsyncCallback<image.PixelMap>): void-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;image.PixelMap&gt; | 是 | 回调函数。返回一个PixelMap对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |

**示例：**

ArkTS-Dyn示例：

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { image } from '@kit.ImageKit';

// 调用save方法获取屏幕截图
screenshot.save((err: BusinessError, pixelMap: image.PixelMap) => {
  if (err) {
    console.error(`Failed to save screenshot. Code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info(`Succeeded in saving screenshot. Pixel bytes number: ${pixelMap.getPixelBytesNumber()}`);
  pixelMap.release(); // PixelMap使用完后及时释放内存
});
```

ArkTS-Sta示例：

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { image } from '@kit.ImageKit';

screenshot.save((err: BusinessError | null, pixelMap: image.PixelMap | undefined) => {
  const errCode = err?.code;
  if (errCode) {
    console.error(`Failed to save screenshot. Code: ${err?.code}, message: ${err?.message}`);
    return;
  }
  console.info(`Succeeded in saving screenshot. Pixel bytes number: ${pixelMap?.getPixelBytesNumber()}`);
  pixelMap?.release(); // PixelMap使用完后及时释放内存
});
```


## save

```TypeScript
function save(options?: ScreenshotOptions): Promise<image.PixelMap>
```

获取屏幕截图，使用Promise异步回调。

**起始版本：** 7

**ArkTS模式：** ArkTS-Dyn起始版本为7；ArkTS-Sta起始版本为23。

**需要权限：** 
- API版本26.0.0+：ohos.permission.CUSTOM_SCREEN_CAPTURE or ohos.permission.CAPTURE_SCREEN or ohos.permission.CUSTOM_SCREEN_RECORDING
- API版本22 - 24：ohos.permission.CAPTURE_SCREEN or ohos.permission.CUSTOM_SCREEN_RECORDING
- API版本7 - 21：ohos.permission.CAPTURE_SCREEN

<!--Device-screenshot-function save(options?: ScreenshotOptions): Promise<image.PixelMap>--><!--Device-screenshot-function save(options?: ScreenshotOptions): Promise<image.PixelMap>-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 否 | 要截取的图像信息。当指定截取屏幕为虚拟屏时，截取图像为白屏。\_\_\_HTML\_TAG\_USD\_0\_\_\_**起始版本：** 22 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;image.PixelMap&gt; | Promise used to return a PixelMap object. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed.The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [1400001](../errorcode-display.md#1400001-无效的显示设备) | Invalid display or screen. |

**示例：**

ArkTS-Dyn示例：

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { image } from '@kit.ImageKit';

let screenshotOptions: screenshot.ScreenshotOptions = {
  screenRect: {
    left: 200,
    top: 100,
    width: 200,
    height: 200 },
  imageSize: {
    width: 300,
    height: 300 },
  rotation: 0,
  displayId: 0,
  isNotificationNeeded: true,
  isCaptureFullOfScreen: true
};
try {
  let promise = screenshot.save(screenshotOptions);
  promise.then((pixelMap: image.PixelMap) => {
    let pixelBytesNumber = pixelMap.getPixelBytesNumber();
    console.info(`Succeeded in saving screenshot. Pixel bytes number: ${pixelBytesNumber}`);
    pixelMap.release(); // PixelMap使用完后及时释放内存
  }).catch((err: BusinessError) => {
    console.error(`Failed to save screenshot. Code: ${err.code}, message: ${err.message}`);
  });
} catch (exception) {
  console.error(`Failed to save screenshot. Code: ${exception.code}, message: ${exception.message}`);
}
```

ArkTS-Sta示例：

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
  }).catch((err: Error) => {
    console.error(`Failed to save screenshot. Code: ${err?.code}, message: ${err?.message}`);
  });
} catch (exception) {
  let error = exception as BusinessError;
  console.error(`Failed to save screenshot. Code: ${error.code}, message: ${error.message}`);
};
```

