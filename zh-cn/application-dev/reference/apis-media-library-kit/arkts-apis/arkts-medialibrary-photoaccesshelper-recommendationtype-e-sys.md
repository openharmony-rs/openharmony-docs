# RecommendationType（系统接口）

```TypeScript
enum RecommendationType
```

枚举，推荐的图片类型。

**起始版本：** 11

<!--Device-photoAccessHelper-enum RecommendationType--><!--Device-photoAccessHelper-enum RecommendationType-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## ARCHITECTURE

```TypeScript
ARCHITECTURE = 15
```

ARCHITECTURE表示建筑照片会被推荐。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-RecommendationType-ARCHITECTURE = 15--><!--Device-RecommendationType-ARCHITECTURE = 15-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

## CAT

```TypeScript
CAT = 13
```

CAT表示猫咪照片会被推荐。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-RecommendationType-CAT = 13--><!--Device-RecommendationType-CAT = 13-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

## COLOR_STYLE_PHOTO

```TypeScript
COLOR_STYLE_PHOTO = 12
```

推荐风格。

**起始版本：** 18

<!--Device-RecommendationType-COLOR_STYLE_PHOTO = 12--><!--Device-RecommendationType-COLOR_STYLE_PHOTO = 12-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

## DOG

```TypeScript
DOG = 14
```

DOG表示狗照片会被推荐。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-RecommendationType-DOG = 14--><!--Device-RecommendationType-DOG = 14-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

## FEATURED_SINGLE_PET

```TypeScript
FEATURED_SINGLE_PET = 18
```

推荐人像。

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-RecommendationType-FEATURED_SINGLE_PET = 18--><!--Device-RecommendationType-FEATURED_SINGLE_PET = 18-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

## GAUSSIAN_SPLAT_3D

```TypeScript
GAUSSIAN_SPLAT_3D = 17
```

GAUSSIAN_SPLAT_3D表示通过3D高斯技术生成的照片会被推荐。

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-RecommendationType-GAUSSIAN_SPLAT_3D = 17--><!--Device-RecommendationType-GAUSSIAN_SPLAT_3D = 17-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

## LANDSCAPE

```TypeScript
LANDSCAPE = 16
```

LANDSCAPE表示风景照片会被推荐。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-RecommendationType-LANDSCAPE = 16--><!--Device-RecommendationType-LANDSCAPE = 16-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

<!--Del-->
**示例**

```TypeScript
import { photoAccessHelper } from '@kit.MediaLibraryKit';
import { BusinessError } from '@kit.BasicServicesKit';

async function example() {
  try {
    let recommendOptions: photoAccessHelper.RecommendationOptions = {
      recommendationType: photoAccessHelper.RecommendationType.ID_CARD
    };
    let options: photoAccessHelper.PhotoSelectOptions = {
      MIMEType: photoAccessHelper.PhotoViewMIMETypes.IMAGE_TYPE,
      maxSelectNumber: 1,
      recommendationOptions: recommendOptions
    };
    let photoPicker = new photoAccessHelper.PhotoViewPicker();
    photoPicker.select(options).then((photoSelectResult: photoAccessHelper.PhotoSelectResult) => {
      console.info('PhotoViewPicker.select successfully, photoSelectResult uri: ' + JSON.stringify(photoSelectResult));
    }).catch((err: BusinessError) => {
      console.error(`PhotoViewPicker.select failed with err: ${err.code}, ${err.message}`);
    });
  } catch (error) {
    let err: BusinessError = error as BusinessError;
    console.error(`PhotoViewPicker failed with err: ${err.code}, ${err.message}`);
  }
}
```

<!--DelEnd-->
