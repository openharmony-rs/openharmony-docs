# FetchResult

文件检索结果集。

**起始版本：** 23

<!--Device-photoAccessHelper-interface FetchResult--><!--Device-photoAccessHelper-interface FetchResult-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## 导入模块

```TypeScript
import { photoAccessHelper } from '@kit.MediaLibraryKit';
```

## getRangeObjects

```TypeScript
getRangeObjects(index: int, offset: int): Promise<T[]>
```

在文件检索结果中，从指定索引（第一个参数）开始，获取指定长度（第二个参数）的文件资产数组。使用Promise异步回调。

**起始版本：** 23

<!--Device-FetchResult-getRangeObjects(index: int, offset: int): Promise<T[]>--><!--Device-FetchResult-getRangeObjects(index: int, offset: int): Promise<T[]>-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| index | int | 是 | 开始获取的文件资产索引，大于等于0，小于文件检索结果中对象数量。 |
| offset | int | 是 | 要获取的文件资产数量，大于0。 <br>index和offset之和需要小于检索结果中的对象数量，否则抛出23800151错误码。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;T[]&gt; | 返回Promise异步回调数组。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [23800301](../errorcode-medialibrary.md#23800301-系统内部错误) | Internal system error. You are advised to retry and check the logs. <br>Possible causes: <br>1. The database is corrupted. <br>2. The file system is abnormal. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Called by non-system application<br>**适用版本：** 21 - 22 |
| [23800151](../errorcode-medialibrary.md#23800151-场景参数校验不通过) | The scenario parameter verification fails. <br>Possible causes: index or offset validity check failed. |

