# getExternalDiskInfos

## 导入模块

```TypeScript
import { volumeManager } from '@kit.CoreFileKit';
```

## getExternalDiskInfos

```TypeScript
function getExternalDiskInfos(): Promise<Array<ExternalDiskInfo>>
```

获取所有外置存储物理磁盘信息，使用Promise异步回调。

**起始版本：** 26.0.1

**需要权限：** ohos.permission.GET_STORAGE_VOLUME_INFO

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-volumeManager-function getExternalDiskInfos(): Promise<Array<ExternalDiskInfo>>--><!--Device-volumeManager-function getExternalDiskInfos(): Promise<Array<ExternalDiskInfo>>-End-->

**系统能力：** SystemCapability.FileManagement.StorageService.Volume

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;[ExternalDiskInfo](arkts-corefile-volumemanager-externaldiskinfo-i.md)&gt;&gt; | Promise对象，返回外置存储物理磁盘信息列表。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-api权限校验失败) | Permission verification failed. |
| 13600001 | IPC error. |
