# CloudEnhancement（系统接口）

云增强管理类，该类用于生成AI云增强照片任务的管理、获取原照片与AI云增强照片的关联关系。

**起始版本：** 13

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { photoAccessHelper } from '@kit.MediaLibraryKit';
```

## cancelAllCloudEnhancementTasks

```TypeScript
cancelAllCloudEnhancementTasks(): Promise<void>
```

取消全部云增强任务。

**起始版本：** 13

**需要权限：** ohos.permission.WRITE_IMAGEVIDEO

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，返回void。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Called by non-system application |
| 14000011 | Internal system error |

**示例**

```TypeScript
async function example(context: Context) {
  console.info('cancelAllCloudEnhancementTasksDemo');
  try {
    let cloudEnhancementInstance: photoAccessHelper.CloudEnhancement
      = photoAccessHelper.CloudEnhancement.getCloudEnhancementInstance(context);
    await cloudEnhancementInstance.cancelAllCloudEnhancementTasks();
  } catch (err) {
    console.error(`cancelAllCloudEnhancementTasksDemo failed with error: ${err.code}, ${err.message}`);
  }
}
```

## cancelCloudEnhancementTasks

```TypeScript
cancelCloudEnhancementTasks(photoAssets: Array<PhotoAsset>): Promise<void>
```

取消指定云增强任务。

**起始版本：** 13

**需要权限：** ohos.permission.WRITE_IMAGEVIDEO

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| photoAssets | Array&lt;[PhotoAsset](arkts-medialibrary-photoaccesshelper-photoasset-i.md)&gt; | 是 | 需要取消云增强任务的[PhotoAsset](arkts-medialibrary-photoaccesshelper-photoasset-i.md)集合。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，返回void。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Called by non-system application |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes:<br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| 14000011 | Internal system error |

**示例**

```TypeScript
phAccessHelper的创建请参考[photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper)的示例使用。
```

## getCloudEnhancementInstance

```TypeScript
static getCloudEnhancementInstance(context: Context): CloudEnhancement
```

获取云增强类实例。

**起始版本：** 13

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | [Context](../../apis-ability-kit/arkts-apis/arkts-ability-context-c.md) | 是 | 传入Ability实例的Context。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [CloudEnhancement](arkts-medialibrary-photoaccesshelper-cloudenhancement-c-sys.md) | 返回云增强管理类实例。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Called by non-system application |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes:<br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| 14000011 | Internal system error |

**示例**

```TypeScript
import { dataSharePredicates } from '@kit.ArkData';

async function example(context: Context) {
  console.info('getCloudEnhancementInstanceDemo');
  let photoPredicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
  let photoFetchOptions: photoAccessHelper.FetchOptions = {
    fetchColumns: [],
    predicates: photoPredicates
  };
  let phAccessHelper = photoAccessHelper.getPhotoAccessHelper(context);
  try {
    let fetchResult = await phAccessHelper.getAssets(photoFetchOptions);
    let asset = await fetchResult.getLastObject();
    let cloudEnhancementInstance: photoAccessHelper.CloudEnhancement
      = photoAccessHelper.CloudEnhancement.getCloudEnhancementInstance(context);
    let hasCloudWatermark = true;
    await cloudEnhancementInstance.submitCloudEnhancementTasks([asset], hasCloudWatermark);
  } catch (err) {
    console.error(`getCloudEnhancementInstanceDemo failed with error: ${err.code}, ${err.message}`);
  }
}
```

## getCloudEnhancementPair

```TypeScript
getCloudEnhancementPair(asset: PhotoAsset): Promise<PhotoAsset>
```

查询云增强配对照片。

**起始版本：** 13

**需要权限：** ohos.permission.READ_IMAGEVIDEO

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| asset | [PhotoAsset](arkts-medialibrary-photoaccesshelper-photoasset-i.md) | 是 | 需要查询云增强配对照片的[PhotoAsset](arkts-medialibrary-photoaccesshelper-photoasset-i.md)。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[PhotoAsset](arkts-medialibrary-photoaccesshelper-photoasset-i.md)&gt; | 返回云增强配对照片。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Called by non-system application |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes:<br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| 14000011 | Internal system error |

**示例**

```TypeScript
phAccessHelper的创建请参考[photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper)的示例使用。
```

## prioritizeCloudEnhancementTask

```TypeScript
prioritizeCloudEnhancementTask(photoAsset: PhotoAsset): Promise<void>
```

提升指定云增强任务的优先级。

**起始版本：** 13

**需要权限：** ohos.permission.WRITE_IMAGEVIDEO

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| photoAsset | [PhotoAsset](arkts-medialibrary-photoaccesshelper-photoasset-i.md) | 是 | 需要修改云增强优先级照片的[PhotoAsset](arkts-medialibrary-photoaccesshelper-photoasset-i.md)。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，返回void。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Called by non-system application |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes:<br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| 14000011 | Internal system error |

**示例**

```TypeScript
phAccessHelper的创建请参考[photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper)的示例使用。
```

## queryCloudEnhancementTaskState

```TypeScript
queryCloudEnhancementTaskState(photoAsset: PhotoAsset): Promise<CloudEnhancementTaskState>
```

查询云增强任务信息。

**起始版本：** 13

**需要权限：** ohos.permission.READ_IMAGEVIDEO

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| photoAsset | [PhotoAsset](arkts-medialibrary-photoaccesshelper-photoasset-i.md) | 是 | 需要查询云增强任务信息的[PhotoAsset](arkts-medialibrary-photoaccesshelper-photoasset-i.md)。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[CloudEnhancementTaskState](arkts-medialibrary-photoaccesshelper-cloudenhancementtaskstate-i-sys.md)&gt; | 返回云增强任务信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Called by non-system application |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes:<br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| 14000011 | Internal system error |

**示例**

```TypeScript
phAccessHelper的创建请参考[photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper)的示例使用。
```

## submitCloudEnhancementTasks

```TypeScript
submitCloudEnhancementTasks(photoAssets: Array<PhotoAsset>, hasCloudWatermark: boolean): Promise<void>
```

提交云增强任务。使用Promise异步回调。

**起始版本：** 13

**需要权限：** ohos.permission.WRITE_IMAGEVIDEO

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| photoAssets | Array&lt;[PhotoAsset](arkts-medialibrary-photoaccesshelper-photoasset-i.md)&gt; | 是 | 需要增强照片的[PhotoAsset](arkts-medialibrary-photoaccesshelper-photoasset-i.md)集合。 |
| hasCloudWatermark | boolean | 是 | 增强后图片是否添加云增强水印。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，返回void。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Called by non-system application |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes:<br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| 14000011 | Internal system error |

**示例**

```TypeScript
phAccessHelper的创建请参考[photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper)的示例使用。
```

## submitCloudEnhancementTasks

```TypeScript
submitCloudEnhancementTasks(
      photoAssets: Array<PhotoAsset>,
      hasCloudWatermark: boolean,
      triggerMode?: number
    ): Promise<void>
```

提交云增强任务，支持选择云增强任务触发类型。使用Promise异步回调。

**起始版本：** 18

**需要权限：** ohos.permission.WRITE_IMAGEVIDEO

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| photoAssets | Array&lt;[PhotoAsset](arkts-medialibrary-photoaccesshelper-photoasset-i.md)&gt; | 是 | 需要增强照片的[PhotoAsset](arkts-medialibrary-photoaccesshelper-photoasset-i.md)集合。 |
| hasCloudWatermark | boolean | 是 | 若为true，增强后图片添加云增强水印；若为false，增强后图片不添加云增强水印。 |
| triggerMode | number | 否 | 云增强任务触发类型。<br>- 0：手动触发。<br>- 1：自动触发。<br>- 默认值为0。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，返回void。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Called by non-system application |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes:<br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| 14000011 | Internal system error |

**示例**

参见 [submitCloudEnhancementTasks](#submitcloudenhancementtasks)

## syncCloudEnhancementTaskStatus

```TypeScript
syncCloudEnhancementTaskStatus(): Promise<void>
```

同步云增强任务状态。

**起始版本：** 13

**需要权限：** ohos.permission.READ_IMAGEVIDEO

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，返回void。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Called by non-system application |
| 14000011 | Internal system error |

**示例**

```TypeScript
async function example(context: Context) {
  console.info('syncCloudEnhancementTaskStatusDemo');
  try {
    let cloudEnhancementInstance: photoAccessHelper.CloudEnhancement
      = photoAccessHelper.CloudEnhancement.getCloudEnhancementInstance(context);
    await cloudEnhancementInstance.syncCloudEnhancementTaskStatus();
  } catch (err) {
    console.error(`syncCloudEnhancementTaskStatusDemo failed with error: ${err.code}, ${err.message}`);
  }
}
```
