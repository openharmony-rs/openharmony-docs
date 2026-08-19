# createPicture

## 导入模块

```TypeScript
import { image } from '@kit.ImageKit';
```

## createPicture

```TypeScript
function createPicture(mainPixelmap : PixelMap): Picture
```

通过主图的PixelMap创建一个Picture对象。 由于图片占用内存较大，所以当Picture对象使用完成后，应主动调用[release](arkts-image-image-picture-i.md#release)方法及时释放内存。释放时应确保该对象的所有异步方法均执行完成，且后续不再使用该对象。

**起始版本：** 23

<!--Device-image-function createPicture(mainPixelmap : PixelMap): Picture--><!--Device-image-function createPicture(mainPixelmap : PixelMap): Picture-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| mainPixelmap | PixelMap | 是 | 主图的PixelMap。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Picture](arkts-image-image-picture-i.md) | 返回Picture对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error.Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types; 3.Parameter verification failed. |

**示例**

ArkTS-Dyn示例:

```TypeScript
async function CreatePicture(context: Context) {
  const resourceMgr = context.resourceManager;
  const rawFile = await resourceMgr.getRawFileContent("test.jpg");
  let opts: image.SourceOptions = {
    sourceDensity: 98,
  }
  let imageSource: image.ImageSource = image.createImageSource(rawFile.buffer as ArrayBuffer, opts);
  let commodityPixelMap: image.PixelMap = await imageSource.createPixelMap();
  let pictureObj: image.Picture = image.createPicture(commodityPixelMap);
  if (pictureObj != null) {
    console.info('Succeeded in creating picture.');
  } else {
    console.error('Failed to create picture.');
  }
}
```

ArkTS-Sta示例:

```TypeScript
import { resourceManager } from '@kit.LocalizationKit';

function CreatePictureFunc(context: common.UIAbilityContext): image.Picture | undefined {
  const resourceMgr: resourceManager.ResourceManager = context.resourceManager;
  // 此处'test_image.jpg'仅作示例，请开发者自行替换，否则imageSource会创建失败导致后续无法正常执行。
  let rawFileDescriptor: resourceManager.RawFileDescriptor = await resourceMgr.getRawFd('test_image.jpg');
  let sourceOptions: image.SourceOptions = { sourceDensity: 98 };
  let imageSource = image.createImageSource(rawFileDescriptor, sourceOptions);
  let pixelMap: image.PixelMap = await imageSource.createPixelMap();

  try {
    let picture: image.Picture = image.createPicture(pixelMap);
    return picture;
  } catch (err) {
    console.error(0x00000, 'CreatePictureFunc', 'CreatePictureFunc failed: ' + err);
    return undefined;
  }
}
```

