# sendImage（系统接口）

## sendImage

```TypeScript
function sendImage(sessionId: int, image: image.PixelMap, quality?: int): Promise<void>
```

Send image data.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-abilityConnectionManager-function sendImage(sessionId: int, image: image.PixelMap, quality?: int): Promise<void>--><!--Device-abilityConnectionManager-function sendImage(sessionId: int, image: image.PixelMap, quality?: int): Promise<void>-End-->

**系统能力：** SystemCapability.DistributedSched.AppCollaboration

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| sessionId | int | 是 | Ability connection Session id. |
| image | image.PixelMap | 是 | image data to be sent. |
| quality | int | 否 | image compression quality, range 0~100, default 30. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | The promise returned by the function. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system App. |

## 示例

```TypeScript
import { abilityConnectionManager } from '@kit.DistributedServiceKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { photoAccessHelper } from '@kit.MediaLibraryKit';
import { image } from '@kit.ImageKit';
import { fileIo } from '@kit.CoreFileKit';

try {
  let photoSelectOptions = new photoAccessHelper.PhotoSelectOptions();
  photoSelectOptions.MIMEType = photoAccessHelper.PhotoViewMIMETypes.IMAGE_TYPE;
  photoSelectOptions.maxSelectNumber = 5;
  let photoPicker = new photoAccessHelper.PhotoViewPicker();
  // 打开图片选择器，让用户选择图片
  photoPicker.select(photoSelectOptions).then((photoSelectResult) => {
    if (!photoSelectResult) {
      hilog.error(0x0000, 'testTag', 'photoSelectResult = null');
    return;
    }

    // 以只读方式打开图片文件
    let file = fileIo.openSync(photoSelectResult.photoUris[0], fileIo.OpenMode.READ_ONLY);
    hilog.info(0x0000, 'testTag', 'file.fd:' + file.fd);

    // 示例中sessionId为模拟值，实际需通过abilityConnectionManager.connectAbility等接口创建协同会话后获取
    let sessionId = 100;
    // 根据文件描述符创建图片源对象
    let imageSourceApi: image.ImageSource = image.createImageSource(file.fd);
    if (imageSourceApi) {
      // 将图片源转换为像素映射对象
      imageSourceApi.createPixelMap().then((pixelMap) => {
        // 发送图片到对端设备
        abilityConnectionManager.sendImage(sessionId, pixelMap)
      });
    } else {
      hilog.info(0x0000, 'testTag', 'imageSourceApi is undefined');
    }
  })
} catch (error) {
  hilog.error(0x0000, 'testTag', 'photoPicker failed with error: ' + JSON.stringify(error));
}
```

