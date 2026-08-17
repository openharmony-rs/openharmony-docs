# PhotoViewPicker

图库选择器对象用于支持选择图片、视频等用户场景。使用前，需先创建PhotoViewPicker实例。 > **说明：** > > - 如果需要重复拉起PhotoViewPicker，需要先通过NavDestination或跟随进程销毁前一个photoViewPicker。

**起始版本：** 26.0.0

**ArkTS模式：** 起始版本为26.0.0。

**废弃版本：** -1

<!--Device-photoAccessHelper-class PhotoViewPicker--><!--Device-photoAccessHelper-class PhotoViewPicker-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## select

```TypeScript
select(option?: PhotoSelectOptions): Promise<PhotoSelectResult>
```

通过选择模式拉起photoPicker界面，用户可以选择一个或多个图片/视频。使用Promise异步回调。传入可选参数PhotoSelectOptions对象，返回PhotoSelectResult对象。 > **注意：** > > 此接口返回的PhotoSelectResult对象中的photoUris具有永久授权，可通过调用接口 > [photoAccessHelper.getAssets](arkts-medialibrary-photoaccesshelper-photoaccesshelper-i.md#getassets) > 去使用。具体操作请参考[媒体文件URI的使用方式](../../../file-management/user-file-uri-intro.md#媒体文件uri的使用方式)。

**起始版本：** 26.0.0

**ArkTS模式：** 起始版本为26.0.0。

**废弃版本：** -1

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-PhotoViewPicker-select(option?: PhotoSelectOptions): Promise<PhotoSelectResult>--><!--Device-PhotoViewPicker-select(option?: PhotoSelectOptions): Promise<PhotoSelectResult>-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| option | PhotoSelectOptions | 否 | photoPicker选择选项，若无此参数，则默认选择媒体文件类型为图片和视频类型，默认选择媒体文件数量的最大值为50。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;PhotoSelectResult&gt; | Promise对象。返回photoPicker选择后的结果集 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: <br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| [23800151](../errorcode-medialibrary.md#23800151-场景参数校验不通过) | Scene parameters validate failed, possible causes: <br>1. An illegal enumeration value was passed to PhotoSelectOptions.globalMovingPhotoState. Only MOVING_PHOTO_ENABLED and MOVING_PHOTO_DISABLED are supported for configuration; <br>2. An illegal enumeration value was passed to PhotoSelectOptions.assetCompatibleAbility.<br>**适用版本：** 12+ |
| 13900042 | Unknown error |

## select

```TypeScript
select(option: PhotoSelectOptions, callback: AsyncCallback<PhotoSelectResult>): void
```

通过选择模式拉起photoPicker界面，用户可以选择一个或多个图片/视频。接口采用callback异步返回形式，传入参数PhotoSelectOptions对象，返回PhotoSelectResult对象。 > **注意：** > > 此接口返回的PhotoSelectResult对象中的photoUris具有永久授权，可通过调用接口 > [photoAccessHelper.getAssets](arkts-medialibrary-photoaccesshelper-photoaccesshelper-i.md#getassets) > 去使用。具体操作请参考[媒体文件URI的使用方式](../../../file-management/user-file-uri-intro.md#媒体文件uri的使用方式)。

**起始版本：** 26.0.0

**ArkTS模式：** 起始版本为26.0.0。

**废弃版本：** -1

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-PhotoViewPicker-select(option: PhotoSelectOptions, callback: AsyncCallback<PhotoSelectResult>): void--><!--Device-PhotoViewPicker-select(option: PhotoSelectOptions, callback: AsyncCallback<PhotoSelectResult>): void-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| option | PhotoSelectOptions | 是 | photoPicker选择选项。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;PhotoSelectResult&gt; | 是 | callback 返回photoPicker选择后的结果集。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: <br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| [23800151](../errorcode-medialibrary.md#23800151-场景参数校验不通过) | Scene parameters validate failed, possible causes: <br>1. An illegal enumeration value was passed to PhotoSelectOptions.globalMovingPhotoState. Only MOVING_PHOTO_ENABLED and MOVING_PHOTO_DISABLED are supported for configuration;<br>**适用版本：** 12+ |
| 13900042 | Unknown error |

## select

```TypeScript
select(callback: AsyncCallback<PhotoSelectResult>): void
```

通过选择模式拉起photoPicker界面，用户可以选择一个或多个图片/视频。接口采用callback异步返回形式，返回PhotoSelectResult对象。 > **注意：** > > 此接口返回的PhotoSelectResult对象中的photoUris具有永久授权，可通过调用接口 > [photoAccessHelper.getAssets](arkts-medialibrary-photoaccesshelper-photoaccesshelper-i.md#getassets) > 去使用。具体操作请参考[媒体文件URI的使用方式](../../../file-management/user-file-uri-intro.md#媒体文件uri的使用方式)。

**起始版本：** 26.0.0

**ArkTS模式：** 起始版本为26.0.0。

**废弃版本：** -1

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-PhotoViewPicker-select(callback: AsyncCallback<PhotoSelectResult>): void--><!--Device-PhotoViewPicker-select(callback: AsyncCallback<PhotoSelectResult>): void-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;PhotoSelectResult&gt; | 是 | callback 返回photoPicker选择后的结果集。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: <br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types. |
| 13900042 | Unknown error |

