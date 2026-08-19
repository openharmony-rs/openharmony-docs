# MediaAssetsChangeRequest（系统接口）

批量资产变更请求。

**继承/实现关系：** MediaAssetsChangeRequest implements [MediaChangeRequest](arkts-medialibrary-photoaccesshelper-mediachangerequest-i.md)

**起始版本：** 23

<!--Device-photoAccessHelper-class MediaAssetsChangeRequest--><!--Device-photoAccessHelper-class MediaAssetsChangeRequest-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { photoAccessHelper } from '@kit.MediaLibraryKit';
```

## constructor

```TypeScript
constructor(assets: Array<PhotoAsset>)
```

构造函数。用于初始化批量资产变更请求。

**起始版本：** 23

<!--Device-MediaAssetsChangeRequest-constructor(assets: Array<PhotoAsset>)--><!--Device-MediaAssetsChangeRequest-constructor(assets: Array<PhotoAsset>)-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| assets | Array&lt;PhotoAsset&gt; | 是 | 需要变更的资产数组。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 14000011 | System inner fail |

## setFavorite

```TypeScript
setFavorite(favoriteState: boolean): void
```

批量将文件设置为收藏文件。

**起始版本：** 23

<!--Device-MediaAssetsChangeRequest-setFavorite(favoriteState: boolean): void--><!--Device-MediaAssetsChangeRequest-setFavorite(favoriteState: boolean): void-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| favoriteState | boolean | 是 | 是否设置为收藏文件， true：设置为收藏文件；false：取消收藏。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 14000011 | System inner fail |

## setHidden

```TypeScript
setHidden(hiddenState: boolean): void
```

将文件设置为隐藏文件。

**起始版本：** 23

<!--Device-MediaAssetsChangeRequest-setHidden(hiddenState: boolean): void--><!--Device-MediaAssetsChangeRequest-setHidden(hiddenState: boolean): void-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| hiddenState | boolean | 是 | 是否设置为隐藏文件，true：将文件资产放入隐藏相册；false：从隐藏相册中恢复。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: <br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Called by non-system application |
| 14000011 | System inner fail |

**示例**

phAccessHelper的创建请参考[photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper)的示例使用。

```TypeScript
import { dataSharePredicates } from '@kit.ArkData';
import { BusinessError } from '@kit.BasicServicesKit';

async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper) {
  console.info('setHiddenDemo');
  let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
  let fetchOption: photoAccessHelper.FetchOptions = {
    fetchColumns: [],
    predicates: predicates
  };
  let fetchResult: photoAccessHelper.FetchResult<photoAccessHelper.PhotoAsset> = await phAccessHelper.getAssets(fetchOption);
  let photoAssetList: Array<photoAccessHelper.PhotoAsset> = await fetchResult.getAllObjects();
  let assetsChangeRequest: photoAccessHelper.MediaAssetsChangeRequest = new photoAccessHelper.MediaAssetsChangeRequest(photoAssetList);
  assetsChangeRequest.setHidden(true);
  phAccessHelper.applyChanges(assetsChangeRequest).then(() => {
    console.info('apply setHidden successfully');
  }).catch((err: BusinessError) => {
    console.error(`apply setHidden failed with error: ${err.code}, ${err.message}`);
  });
}
```

## setIsRecentShow

```TypeScript
setIsRecentShow(isRencentShow: boolean): void
```

设置当前资产是否在“最近”列表中显示。

**起始版本：** 23

<!--Device-MediaAssetsChangeRequest-setIsRecentShow(isRencentShow: boolean): void--><!--Device-MediaAssetsChangeRequest-setIsRecentShow(isRencentShow: boolean): void-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| isRencentShow | boolean | 是 | 表示当前资产是否在“最近”列表中显示。true表示显示，false表示不显示。 **false** otherwise. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: <br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Called by non-system application |
| 14000011 | System inner fail |

**示例**

phAccessHelper的创建请参考[photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper)的示例使用。

```TypeScript
import { dataSharePredicates } from '@kit.ArkData';
import { BusinessError } from '@kit.BasicServicesKit';

async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper) {
  console.info('setIsRecentShowDemo');
  let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
  let fetchOption: photoAccessHelper.FetchOptions = {
    fetchColumns: [],
    predicates: predicates
  };
  let fetchResult: photoAccessHelper.FetchResult<photoAccessHelper.PhotoAsset> = await phAccessHelper.getAssets(fetchOption);
  let photoAssetList: Array<photoAccessHelper.PhotoAsset> = await fetchResult.getAllObjects();
  let assetsChangeRequest: photoAccessHelper.MediaAssetsChangeRequest = new photoAccessHelper.MediaAssetsChangeRequest(photoAssetList);
  assetsChangeRequest.setIsRecentShow(true);
  phAccessHelper.applyChanges(assetsChangeRequest).then(() => {
    console.info('apply setIsRecentShow successfully');
  }).catch((err: BusinessError) => {
    console.error(`apply setIsRecentShow failed with error: ${err.code}, ${err.message}`);
  });
}
```

## setUserComment

```TypeScript
setUserComment(userComment: string): void
```

修改媒体资产的备注信息。

**起始版本：** 23

<!--Device-MediaAssetsChangeRequest-setUserComment(userComment: string): void--><!--Device-MediaAssetsChangeRequest-setUserComment(userComment: string): void-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| userComment | string | 是 | 待修改的资产备注信息，备注信息最长为420字符。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: <br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Called by non-system application |
| 14000011 | System inner fail |

**示例**

phAccessHelper的创建请参考[photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper)的示例使用。

```TypeScript
import { dataSharePredicates } from '@kit.ArkData';
import { BusinessError } from '@kit.BasicServicesKit';

async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper) {
  console.info('setUserCommentDemo');
  let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
  let fetchOption: photoAccessHelper.FetchOptions = {
    fetchColumns: [],
    predicates: predicates
  };
  let fetchResult: photoAccessHelper.FetchResult<photoAccessHelper.PhotoAsset> = await phAccessHelper.getAssets(fetchOption);
  let photoAssetList: Array<photoAccessHelper.PhotoAsset> = await fetchResult.getAllObjects();
  let assetsChangeRequest: photoAccessHelper.MediaAssetsChangeRequest = new photoAccessHelper.MediaAssetsChangeRequest(photoAssetList);
  assetsChangeRequest.setUserComment('test_set_user_comment');
  phAccessHelper.applyChanges(assetsChangeRequest).then(() => {
    console.info('apply setUserComment successfully');
  }).catch((err: BusinessError) => {
    console.error(`apply setUserComment failed with error: ${err.code}, ${err.message}`);
  });
}
```

## comment

```TypeScript
readonly comment: string
```

用于[MediaChangeRequest](arkts-medialibrary-photoaccesshelper-mediachangerequest-i.md) 类型校验。 <br>如果类（如MediaAssetsChangeRequest）对象可以访问，就说明该类是MediaChangeRequest的实现类。

**类型：** string

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-MediaAssetsChangeRequest-readonly comment: string--><!--Device-MediaAssetsChangeRequest-readonly comment: string-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

