# Album

```TypeScript
interface Album extends AbsAlbum
```

实体相册

**继承/实现关系：** Album extends [AbsAlbum](arkts-medialibrary-sendablephotoaccesshelper-absalbum-i.md)

**起始版本：** 12

<!--Device-sendablePhotoAccessHelper-interface Album extends AbsAlbum--><!--Device-sendablePhotoAccessHelper-interface Album extends AbsAlbum-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## 导入模块

```TypeScript
import { sendablePhotoAccessHelper } from '@kit.MediaLibraryKit';
```

## getFaceId

```TypeScript
getFaceId(): Promise<string>
```

获取人像相册或合影相册的封面人脸标识。使用Promise异步回调。

**起始版本：** 13

**需要权限：** ohos.permission.READ_IMAGEVIDEO

<!--Device-Album-getFaceId(): Promise<string>--><!--Device-Album-getFaceId(): Promise<string>-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;string&gt; | Promise对象，人像相册返回tag_id，合影相册返回group_tag，未找到返回空字符串。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-api权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | Permission verification failed. A non-system application calls a system API. |
| 14000011 | Internal system error |

<!--Del-->
**示例**

phAccessHelper的创建请参考[@ohos.file.sendablePhotoAccessHelper (基于Sendable对象的相册管理模块)](arkts-medialibrary-file-sendablephotoaccesshelper.md)的示例使用。

```TypeScript
import { dataSharePredicates } from '@kit.ArkData';
import { common } from '@kit.AbilityKit';

async function example(phAccessHelper: sendablePhotoAccessHelper.PhotoAccessHelper) {
  try {
    console.info('getFaceIdDemo');
    let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
    predicates.equalTo('user_display_level', 1);
    let fetchOptions: photoAccessHelper.FetchOptions = {
      fetchColumns: [],
      predicates: predicates
    };
    let fetchResult =
      await phAccessHelper.getAlbums(sendablePhotoAccessHelper.AlbumType.SMART,
        sendablePhotoAccessHelper.AlbumSubtype.PORTRAIT,
        fetchOptions);
    let album = await fetchResult?.getFirstObject();
    let faceId = await album?.getFaceId();
    console.info(`getFaceId successfully, faceId: ${faceId}`);
    fetchResult.close();
  } catch (err) {
    console.error(`getFaceId failed with err: ${err.code}, ${err.message}`);
  }
}
```

<!--DelEnd-->

## cloudId

```TypeScript
readonly cloudId?: string
```

相册CloudId。

**类型：** string

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Album-readonly cloudId?: string--><!--Device-Album-readonly cloudId?: string-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

## shareAlbumOwner

```TypeScript
readonly shareAlbumOwner?: string
```

共享相册的所有者。

**类型：** string

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Album-readonly shareAlbumOwner?: string--><!--Device-Album-readonly shareAlbumOwner?: string-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

## shareRiskStatus

```TypeScript
readonly shareRiskStatus?: ShareAlbumRiskStatus
```

共享相册的风控状态。

**类型：** [ShareAlbumRiskStatus](arkts-medialibrary-sendablephotoaccesshelper-sharealbumriskstatus-e-sys.md)

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Album-readonly shareRiskStatus?: ShareAlbumRiskStatus--><!--Device-Album-readonly shareRiskStatus?: ShareAlbumRiskStatus-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

## shareRiskType

```TypeScript
readonly shareRiskType?: string
```

共享相册的风控类型。

**类型：** string

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Album-readonly shareRiskType?: string--><!--Device-Album-readonly shareRiskType?: string-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。
