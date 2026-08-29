# sendImage（系统接口）

## 导入模块

```TypeScript
import { abilityConnectionManager } from '@kit.DistributedServiceKit';
```

## sendImage

```TypeScript
function sendImage(sessionId: number, image: image.PixelMap, quality?: number): Promise<void>
```

应用连接成功并创建传输流后，设备A或设备B可向对端设备发送图片。 图片会根据指定的压缩质量进行编码后，通过传输流通道发送至对端设备。 发送成功后，对端设备可通过注册的回调接收图片，使用Promise异步回调。 业务结束后应及时销毁传输流，否则会增加系统功耗，使用场景包括跨设备视频通话中发送视频帧、 远程协作时发送截图、跨设备图片共享等需要向对端发送图片数据的场景。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedSched.AppCollaboration

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| sessionId | number | 是 | 表示协同会话ID，需先创建协同会话后获取。 |
| image | image.PixelMap | 是 | 表示图片信息。 |
| quality | number | 否 | 表示图像压缩质量，取值范围为0到100，默认值为30。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise &lt;void&gt; | 无返回值的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system App. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |

**示例**

```TypeScript
import { abilityConnectionManager } from '@kit.DistributedServiceKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { BusinessError } from '@kit.BasicServicesKit';
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
        abilityConnectionManager.sendImage(sessionId, pixelMap).then(() => {
          hilog.info(0x0000, 'testTag', 'sendImage success');
        }).catch((err: BusinessError) => {
          hilog.error(0x0000, 'testTag', `sendImage failed with error. Code: ${err.code}, message: ${err.message}`);
        });
      });
    } else {
      hilog.info(0x0000, 'testTag', 'imageSourceApi is undefined');
    }
  })
} catch (error) {
  const err = error as BusinessError;
  hilog.error(0x0000, 'testTag', `photoPicker failed with error. Code: ${err.code}, message: ${err.message}`);
}
```
