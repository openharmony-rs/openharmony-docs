# MediaAssetEditData（系统接口）

资产编辑数据。

**起始版本：** 23

<!--Device-photoAccessHelper-class MediaAssetEditData--><!--Device-photoAccessHelper-class MediaAssetEditData-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { photoAccessHelper } from '@kit.MediaLibraryKit';
```

## constructor

```TypeScript
constructor(compatibleFormat: string, formatVersion: string)
```

构造函数。

**起始版本：** 23

<!--Device-MediaAssetEditData-constructor(compatibleFormat: string, formatVersion: string)--><!--Device-MediaAssetEditData-constructor(compatibleFormat: string, formatVersion: string)-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| compatibleFormat | string | 是 | 编辑数据的格式。 |
| formatVersion | string | 是 | 编辑数据格式的版本。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: <br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Called by non-system application |
| 14000011 | System inner fail |

**示例**

```TypeScript
let assetEditData: photoAccessHelper.MediaAssetEditData = new photoAccessHelper.MediaAssetEditData('system', '1.0');
```

## compatibleFormat

```TypeScript
compatibleFormat: string
```

编辑数据的格式。

**类型：** string

**起始版本：** 23

<!--Device-MediaAssetEditData-compatibleFormat: string--><!--Device-MediaAssetEditData-compatibleFormat: string-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

## data

```TypeScript
data: string
```

编辑数据的内容。

**类型：** string

**起始版本：** 23

<!--Device-MediaAssetEditData-data: string--><!--Device-MediaAssetEditData-data: string-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

## formatVersion

```TypeScript
formatVersion: string
```

编辑数据格式的版本。

**类型：** string

**起始版本：** 23

<!--Device-MediaAssetEditData-formatVersion: string--><!--Device-MediaAssetEditData-formatVersion: string-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

