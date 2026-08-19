# Album

实体相册。

**继承/实现关系：** Album extends [AbsAlbum](arkts-medialibrary-photoaccesshelper-absalbum-i.md)

**起始版本：** 23

<!--Device-photoAccessHelper-interface Album--><!--Device-photoAccessHelper-interface Album-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## 导入模块

```TypeScript
import { photoAccessHelper } from '@kit.MediaLibraryKit';
```

## addAssets

```TypeScript
addAssets(assets: Array<PhotoAsset>, callback: AsyncCallback<void>): void
```

向用户相册中添加图片或视频，需预置相册和文件资源。使用callback异步回调。

**起始版本：** 10

**废弃版本：** 11

**替代接口：** [addAssets](arkts-medialibrary-photoaccesshelper-mediaalbumchangerequest-c.md#addassets)

**需要权限：** ohos.permission.WRITE_IMAGEVIDEO

<!--Device-Album-addAssets(assets: Array<PhotoAsset>, callback: AsyncCallback<void>): void--><!--Device-Album-addAssets(assets: Array<PhotoAsset>, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| assets | Array&lt;PhotoAsset&gt; | 是 | 待添加到相册中的图片或视频数组。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;void&gt; | 是 | 回调函数。当添加图片或视频成功，err为undefined，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 13900020 | Invalid argument |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: <br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied |
| 14000011 | System inner fail |

## addAssets

```TypeScript
addAssets(assets: Array<PhotoAsset>): Promise<void>
```

向用户相册添加图片或视频，需预置相册和文件资源。使用Promise异步回调。

**起始版本：** 10

**废弃版本：** 11

**替代接口：** [addAssets](arkts-medialibrary-photoaccesshelper-mediaalbumchangerequest-c.md#addassets)

**需要权限：** ohos.permission.WRITE_IMAGEVIDEO

<!--Device-Album-addAssets(assets: Array<PhotoAsset>): Promise<void>--><!--Device-Album-addAssets(assets: Array<PhotoAsset>): Promise<void>-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| assets | Array&lt;PhotoAsset&gt; | 是 | 待添加到相册中的图片或视频数组。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 13900020 | Invalid argument |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: <br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied |
| 14000011 | System inner fail |

## commitModify

```TypeScript
commitModify(callback: AsyncCallback<void>): void
```

更新相册属性修改到数据库中。使用callback异步回调。

**起始版本：** 23

**需要权限：** ohos.permission.WRITE_IMAGEVIDEO

<!--Device-Album-commitModify(callback: AsyncCallback<void>): void--><!--Device-Album-commitModify(callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;void&gt; | 是 | 回调函数。当相册属性修改成功，err为undefined，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 13900020 | Invalid argument |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: <br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied |
| 14000011 | System inner fail |

## commitModify

```TypeScript
commitModify(): Promise<void>
```

更新相册属性修改到数据库中。使用Promise异步回调。

**起始版本：** 23

**需要权限：** ohos.permission.WRITE_IMAGEVIDEO

<!--Device-Album-commitModify(): Promise<void>--><!--Device-Album-commitModify(): Promise<void>-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 13900020 | Invalid argument |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: <br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied |
| 14000011 | System inner fail |

## removeAssets

```TypeScript
removeAssets(assets: Array<PhotoAsset>, callback: AsyncCallback<void>): void
```

从用户相册移除图片或视频，需预置相册和文件资源。使用callback异步回调。

**起始版本：** 10

**废弃版本：** 11

**替代接口：** [removeAssets](arkts-medialibrary-photoaccesshelper-mediaalbumchangerequest-c.md#removeassets)

**需要权限：** ohos.permission.WRITE_IMAGEVIDEO

<!--Device-Album-removeAssets(assets: Array<PhotoAsset>, callback: AsyncCallback<void>): void--><!--Device-Album-removeAssets(assets: Array<PhotoAsset>, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| assets | Array&lt;PhotoAsset&gt; | 是 | 相册中待移除的图片或视频数组。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;void&gt; | 是 | 回调函数。当移除图片或视频成功，err为undefined，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 13900020 | Invalid argument |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: <br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied |
| 14000011 | System inner fail |

## removeAssets

```TypeScript
removeAssets(assets: Array<PhotoAsset>): Promise<void>
```

从用户相册中移除图片或视频，需预置相册和文件资源。使用Promise异步回调。

**起始版本：** 10

**废弃版本：** 11

**替代接口：** [removeAssets](arkts-medialibrary-photoaccesshelper-mediaalbumchangerequest-c.md#removeassets)

**需要权限：** ohos.permission.WRITE_IMAGEVIDEO

<!--Device-Album-removeAssets(assets: Array<PhotoAsset>): Promise<void>--><!--Device-Album-removeAssets(assets: Array<PhotoAsset>): Promise<void>-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| assets | Array&lt;PhotoAsset&gt; | 是 | 相册中待移除的图片或视频数组。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 13900020 | Invalid argument |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: <br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied |
| 14000011 | System inner fail |

## imageCount

```TypeScript
readonly imageCount?: int
```

相册中图片数量。

**类型：** int

**起始版本：** 23

<!--Device-Album-readonly imageCount?: int--><!--Device-Album-readonly imageCount?: int-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## videoCount

```TypeScript
readonly videoCount?: int
```

相册中视频数量。

**类型：** int

**起始版本：** 23

<!--Device-Album-readonly videoCount?: int--><!--Device-Album-readonly videoCount?: int-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

