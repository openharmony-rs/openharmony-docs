# PhotoAsset

提供封装文件属性的方法。

**继承/实现关系：** PhotoAsset extends lang.ISendable

**起始版本：** 12

<!--Device-sendablePhotoAccessHelper-interface PhotoAsset--><!--Device-sendablePhotoAccessHelper-interface PhotoAsset-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## 导入模块

```TypeScript
import { sendablePhotoAccessHelper } from '@kit.MediaLibraryKit';
```

## commitModify

```TypeScript
commitModify(): Promise<void>
```

修改文件的元数据。使用Promise异步回调。

**起始版本：** 12

**需要权限：** ohos.permission.WRITE_IMAGEVIDEO

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-PhotoAsset-commitModify(): Promise<void>--><!--Device-PhotoAsset-commitModify(): Promise<void>-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: <br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied |
| 14000011 | Internal system error |

**示例**

phAccessHelper的创建请参考sendablePhotoAccessHelper.getPhotoAccessHelper的示例使用。

```TypeScript
import { dataSharePredicates } from '@kit.ArkData';
import { photoAccessHelper } from '@kit.MediaLibraryKit';

async function example(phAccessHelper: sendablePhotoAccessHelper.PhotoAccessHelper) {
  console.info('commitModifyDemo');
  let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
  let fetchOption: photoAccessHelper.FetchOptions = {
    fetchColumns: ['title'],
    predicates: predicates
  };
  let fetchResult: sendablePhotoAccessHelper.FetchResult<sendablePhotoAccessHelper.PhotoAsset> = await phAccessHelper.getAssets(fetchOption);
  let photoAsset: sendablePhotoAccessHelper.PhotoAsset = await fetchResult.getFirstObject();
  let title: string = photoAccessHelper.PhotoKeys.TITLE.toString();
  let photoAssetTitle: photoAccessHelper.MemberType = photoAsset.get(title);
  console.info('photoAsset get photoAssetTitle = ', photoAssetTitle);
  photoAsset.set(title, 'newTitle3');
  try {
    await photoAsset.commitModify();
    let newPhotoAssetTitle: photoAccessHelper.MemberType = photoAsset.get(title);
    console.info('photoAsset get newPhotoAssetTitle = ', newPhotoAssetTitle);
  } catch (err) {
    console.error(`commitModify failed. error: ${err.code}, ${err.message}`);
  }
}
```

## convertToPhotoAsset

```TypeScript
convertToPhotoAsset(): photoAccessHelper.PhotoAsset
```

将Sendable类型PhotoAsset转换为非Sendable类型PhotoAsset。

**起始版本：** 12

<!--Device-PhotoAsset-convertToPhotoAsset(): photoAccessHelper.PhotoAsset--><!--Device-PhotoAsset-convertToPhotoAsset(): photoAccessHelper.PhotoAsset-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| photoAccessHelper.PhotoAsset | 返回非Sendable类型的 [PhotoAsset]{ |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| 14000011 | Internal system error |

**示例**

phAccessHelper的创建请参考sendablePhotoAccessHelper.getPhotoAccessHelper的示例使用。

```TypeScript
import { dataSharePredicates } from '@kit.ArkData';
import { photoAccessHelper } from '@kit.MediaLibraryKit';

async function example(phAccessHelper: sendablePhotoAccessHelper.PhotoAccessHelper) {
  console.info('convertToPhotoAssetDemo');
  try {
    let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
    let fetchOption: photoAccessHelper.FetchOptions = {
      fetchColumns: ['title'],
      predicates: predicates
    };
    let fetchResult: sendablePhotoAccessHelper.FetchResult<sendablePhotoAccessHelper.PhotoAsset> = await phAccessHelper.getAssets(fetchOption);
    let sendablePhotoAsset: sendablePhotoAccessHelper.PhotoAsset = await fetchResult.getFirstObject();
    let photoAsset: photoAccessHelper.PhotoAsset = sendablePhotoAsset.convertToPhotoAsset();
    console.info(`get no sendable uri success : ${photoAsset.uri}`);
  } catch (err) {
    console.error(`convertToPhotoAsset failed. error: ${err.code}, ${err.message}`);
  }
}
```

## get

```TypeScript
get(member: string): photoAccessHelper.MemberType
```

获取PhotoAsset成员参数的值。

**起始版本：** 12

<!--Device-PhotoAsset-get(member: string): photoAccessHelper.MemberType--><!--Device-PhotoAsset-get(member: string): photoAccessHelper.MemberType-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| member | string | 是 | 成员参数名称，在get时，除了'uri'、'media_type'、'subtype'和'display_name'四个属性之外， 其他的属性都需要在fetchColumns中填入需要get的PhotoKeys，例如：get title属性 fetchColumns: ['title']。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| photoAccessHelper.MemberType | 获取PhotoAsset成员参数的值。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: <br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |

**示例**

phAccessHelper的创建请参考sendablePhotoAccessHelper.getPhotoAccessHelper的示例使用。

```TypeScript
import { dataSharePredicates } from '@kit.ArkData';
import { photoAccessHelper } from '@kit.MediaLibraryKit';

async function example(phAccessHelper: sendablePhotoAccessHelper.PhotoAccessHelper) {
  console.info('photoAssetGetDemo');
  try {
    let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
    let fetchOption: photoAccessHelper.FetchOptions = {
      fetchColumns: ['title'],
      predicates: predicates
    };
    let fetchResult: sendablePhotoAccessHelper.FetchResult<sendablePhotoAccessHelper.PhotoAsset> = await phAccessHelper.getAssets(fetchOption);
    if (fetchResult === undefined) {
      console.error('photoAssetGet fetchResult is undefined');
      return;
    }
    let photoAsset: sendablePhotoAccessHelper.PhotoAsset = await fetchResult.getFirstObject();
    let title: photoAccessHelper.PhotoKeys = photoAccessHelper.PhotoKeys.TITLE;
    let photoAssetTitle: photoAccessHelper.MemberType = photoAsset.get(title.toString());
    console.info('photoAsset Get photoAssetTitle = ', photoAssetTitle);
  } catch (err) {
    console.error(`get failed. error: ${err.code}, ${err.message}`);
  }
}
```

## getThumbnail

```TypeScript
getThumbnail(size?: image.Size): Promise<image.PixelMap>
```

获取文件的缩略图，传入缩略图尺寸。使用Promise异步回调。

**起始版本：** 12

**需要权限：** ohos.permission.READ_IMAGEVIDEO

<!--Device-PhotoAsset-getThumbnail(size?: image.Size): Promise<image.PixelMap>--><!--Device-PhotoAsset-getThumbnail(size?: image.Size): Promise<image.PixelMap>-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| size | image.Size | 否 | 缩略图尺寸。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;image.PixelMap&gt; | Promise对象，返回缩略图的PixelMap。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: <br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied |
| 14000011 | Internal system error |

**示例**

phAccessHelper的创建请参考sendablePhotoAccessHelper.getPhotoAccessHelper的示例使用。

```TypeScript
import { dataSharePredicates } from '@kit.ArkData';
import { image } from '@kit.ImageKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { photoAccessHelper } from '@kit.MediaLibraryKit';

async function example(phAccessHelper: sendablePhotoAccessHelper.PhotoAccessHelper) {
  console.info('getThumbnailDemo');
  let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
  let fetchOption: photoAccessHelper.FetchOptions = {
    fetchColumns: [],
    predicates: predicates
  };
  let size: image.Size = { width: 720, height: 720 };
  let fetchResult: sendablePhotoAccessHelper.FetchResult<sendablePhotoAccessHelper.PhotoAsset> = await phAccessHelper.getAssets(fetchOption);
  let asset = await fetchResult.getFirstObject();
  if (asset === undefined) {
    console.error('getThumbnailPromise albums is undefined');
    return;
  }
  console.info('asset displayName = ', asset.displayName);
  asset.getThumbnail(size).then((pixelMap) => {
    console.info('getThumbnail successful ' + pixelMap);
  }).catch((err: BusinessError) => {
    console.error(`getThumbnail fail with error: ${err.code}, ${err.message}`);
  });
}
```

## set

```TypeScript
set(member: string, value: string): void
```

设置PhotoAsset成员参数。

**起始版本：** 12

<!--Device-PhotoAsset-set(member: string, value: string): void--><!--Device-PhotoAsset-set(member: string, value: string): void-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| member | string | 是 | 成员参数名称例如： [PhotoKeys](arkts-medialibrary-photoaccesshelper-photokeys-e.md) .TITLE。字符串长度的取值范围为[1, 255]。 |
| value | string | 是 | 设置成员参数名称，只能修改 [PhotoKeys](arkts-medialibrary-photoaccesshelper-photokeys-e.md).TITLE的值。title的参数规格为： <br>- 不应包含扩展名。 <br>- 文件名字符串长度的取值范围为[1, 255]（资产文件名为标题+扩展名）。 <br>- 不允许出现的非法英文字符，包括：. \ / : ? " ' ` &lt; &gt; \| { } [ ] |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: <br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |

**示例**

phAccessHelper的创建请参考sendablePhotoAccessHelper.getPhotoAccessHelper的示例使用。

```TypeScript
import { dataSharePredicates } from '@kit.ArkData';
import { photoAccessHelper } from '@kit.MediaLibraryKit';

async function example(phAccessHelper: sendablePhotoAccessHelper.PhotoAccessHelper) {
  console.info('photoAssetSetDemo');
  try {
    let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
    let fetchOption: photoAccessHelper.FetchOptions = {
      fetchColumns: ['title'],
      predicates: predicates
    };
    let fetchResult: sendablePhotoAccessHelper.FetchResult<sendablePhotoAccessHelper.PhotoAsset> = await phAccessHelper.getAssets(fetchOption);
    let photoAsset: sendablePhotoAccessHelper.PhotoAsset = await fetchResult.getFirstObject();
    let title: string = photoAccessHelper.PhotoKeys.TITLE.toString();
    photoAsset.set(title, 'newTitle');
  } catch (err) {
    console.error(`set failed. error: ${err.code}, ${err.message}`);
  }
}
```

## displayName

```TypeScript
readonly displayName: string
```

显示文件名，包含后缀名。字符串长度的取值范围为[1, 255]。

**类型：** string

**起始版本：** 12

<!--Device-PhotoAsset-readonly displayName: string--><!--Device-PhotoAsset-readonly displayName: string-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## photoType

```TypeScript
readonly photoType: PhotoType
```

媒体文件类型。

**类型：** PhotoType

**起始版本：** 12

<!--Device-PhotoAsset-readonly photoType: PhotoType--><!--Device-PhotoAsset-readonly photoType: PhotoType-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## uri

```TypeScript
readonly uri: string
```

媒体文件资源URI（如：file://media/Photo/1/IMG_datetime_0001/displayName.jpg），详情参见用户文件URI介绍中的 [媒体文件URI](../../../file-management/user-file-uri-intro.md#媒体文件uri)。 服务中使用。

**类型：** string

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-PhotoAsset-readonly uri: string--><!--Device-PhotoAsset-readonly uri: string-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

