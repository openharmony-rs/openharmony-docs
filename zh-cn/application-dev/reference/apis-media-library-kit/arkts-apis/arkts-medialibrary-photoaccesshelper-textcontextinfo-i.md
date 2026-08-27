# TextContextInfo

文本信息，用于推荐图片的文本信息。

**起始版本：** 12

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## 导入模块

```TypeScript
import { photoAccessHelper } from '@kit.MediaLibraryKit';
```

## text

```TypeScript
text?: string
```

如果需要根据文本（支持250字以内的简体中文）推荐相应的图片，则配置此参数。text默认是空字符串。

**类型：** string

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper) {
  try {
    let textInfo: photoAccessHelper.TextContextInfo = {
      text: '上海野生动物园的大熊猫'
    }
    let recommendOptions: photoAccessHelper.RecommendationOptions = {
      textContextInfo: textInfo
    }
    let options: photoAccessHelper.PhotoSelectOptions = {
      MIMEType: photoAccessHelper.PhotoViewMIMETypes.IMAGE_TYPE,
      maxSelectNumber: 1,
      recommendationOptions: recommendOptions
    }
    let photoPicker = new photoAccessHelper.PhotoViewPicker();
    photoPicker.select(options).then((PhotoSelectResult: photoAccessHelper.PhotoSelectResult) => {
      console.info('PhotoViewPicker.select successfully, PhotoSelectResult uri: ' + JSON.stringify(PhotoSelectResult));
    }).catch((err: BusinessError) => {
      console.error(`PhotoViewPicker.select failed with err: ${err.code}, ${err.message}`);
    });
  } catch (error) {
    let err: BusinessError = error as BusinessError;
    console.error(`PhotoViewPicker failed with err: ${err.code}, ${err.message}`);
  }
}
```
