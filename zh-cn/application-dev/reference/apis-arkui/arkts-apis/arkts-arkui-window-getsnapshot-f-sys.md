# getSnapshot（系统接口）

## getSnapshot

```TypeScript
function getSnapshot(windowId: int): Promise<image.PixelMap>
```

获取指定窗口相同尺寸截图，使用Promise异步回调。若当前窗口设置为隐私模式（可通过 [setWindowPrivacyMode]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_ 接口设置），截图结果为白屏。

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

<!--Device-window-function getSnapshot(windowId: int): Promise<image.PixelMap>--><!--Device-window-function getSnapshot(windowId: int): Promise<image.PixelMap>-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| windowId | ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：int | 是 | 窗口Id。可通过\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_MD\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_接口获取到相关窗口属性，其中属性id即对应为窗口ID。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;image.PixelMap&gt; | - Promise that returns no value. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_2. Incorrect parameter types. 3.Parameter verification failed. |
| [1300002](../errorcode-window.md#1300002-窗口状态异常) | This window state is abnormal.Possible cause: Internal task error. |
| [1300003](../errorcode-window.md#1300003-系统服务工作异常) | This window manager service works abnormally. |

**示例：**

ArkTS-Dyn示例：

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { image } from '@kit.ImageKit';

try {
  // 此处仅示意，请使用getWindowProperties获取对应窗口ID再进行使用
  let windowId: number = 40;
  let promise = window.getSnapshot(windowId);
  promise.then((pixelMap: image.PixelMap) => {
    console.info('Succeeded in getting snapshot window. Pixel bytes number:' + pixelMap.getPixelBytesNumber());
    pixelMap.release();
  }).catch((err: BusinessError) =>{
    console.error(`Failed to get snapshot. Cause code: ${err.code}, message: ${err.message}`);
  });
} catch (exception) {
  console.error(`Failed to get snapshot. Cause code: ${exception.code}, message: ${exception.message}`);
}
```

ArkTS-Sta示例：

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { image } from '@kit.ImageKit';

try {
  // 此处仅示意，请使用getWindowProperties获取对应窗口ID再进行使用
  let windowId: int = 40;
  let promise = window.getSnapshot(windowId);
  promise.then((pixelMap: image.PixelMap) => {
    console.info('Succeeded in getting snapshot window. Pixel bytes number:' + pixelMap.getPixelBytesNumber());
    pixelMap.release();
  }).catch((err: Error) =>{
    console.error(`Failed to get snapshot. Cause code: ${err.code}, message: ${err.message}`);
  });
} catch (exception) {
  let error = exception as BusinessError;
  console.error(`Failed to get snapshot. Cause code: ${error.code}, message: ${error.message}`);
}
```

