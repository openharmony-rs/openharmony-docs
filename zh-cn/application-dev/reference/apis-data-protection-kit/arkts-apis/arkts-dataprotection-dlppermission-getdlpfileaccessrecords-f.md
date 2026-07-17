# getDLPFileAccessRecords

## 导入模块

```TypeScript
import { dlpPermission } from '@kit.DataProtectionKit';
```

## getDLPFileAccessRecords

```TypeScript
function getDLPFileAccessRecords(): Promise<Array<AccessedDLPFileInfo>>
```

查询最近访问的DLP文件列表。调用成功后返回文件访问记录，用于追踪和管理DLP文件的使用情况。仅支持在非DLP沙箱应用中调用。使用Promise异步回调。

该接口用于获取最近访问的DLP文件记录列表，便于审计追踪和文件使用情况管理。

**起始版本：** 10

<!--Device-dlpPermission-function getDLPFileAccessRecords(): Promise<Array<AccessedDLPFileInfo>>--><!--Device-dlpPermission-function getDLPFileAccessRecords(): Promise<Array<AccessedDLPFileInfo>>-End-->

**系统能力：** SystemCapability.Security.DataLossPrevention

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<Array<AccessedDLPFileInfo>> | Promise对象。返回最近访问的DLP文件列表。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [19100001](../errorcode-dlp.md#19100001-入参错误) | Invalid parameter value. |
| [19100007](../errorcode-dlp.md#19100007-dlp沙箱应用不允许调用此接口) | No permission to call this API,which is available only for non-DLP sandbox applications. |
| [19100011](../errorcode-dlp.md#19100011-系统服务工作异常) | The system ability works abnormally. |

**示例：**

```TypeScript
import { dlpPermission } from '@kit.DataProtectionKit';

dlpPermission.getDLPFileAccessRecords().then((accessRecords) => { // 获取DLP访问列表。
  console.info('accessRecords', JSON.stringify(accessRecords));
}).catch((error: BusinessError)=> {
  console.error(JSON.stringify(error));
});

```


## getDLPFileAccessRecords

```TypeScript
function getDLPFileAccessRecords(callback: AsyncCallback<Array<AccessedDLPFileInfo>>): void
```

查询最近访问的DLP文件列表。调用成功后返回文件访问记录，用于追踪和管理DLP文件的使用情况。使用callback异步回调。

该接口用于获取最近访问的DLP文件记录列表，便于审计追踪和文件使用情况管理。

**起始版本：** 10

<!--Device-dlpPermission-function getDLPFileAccessRecords(callback: AsyncCallback<Array<AccessedDLPFileInfo>>): void--><!--Device-dlpPermission-function getDLPFileAccessRecords(callback: AsyncCallback<Array<AccessedDLPFileInfo>>): void-End-->

**系统能力：** SystemCapability.Security.DataLossPrevention

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<Array<AccessedDLPFileInfo>> | 是 | 回调函数。err为undefined时表示查询成功；否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Incorrect parameter types. |
| [19100001](../errorcode-dlp.md#19100001-入参错误) | Invalid parameter value. |
| [19100007](../errorcode-dlp.md#19100007-dlp沙箱应用不允许调用此接口) | No permission to call this API,which is available only for non-DLP sandbox applications. |
| [19100011](../errorcode-dlp.md#19100011-系统服务工作异常) | The system ability works abnormally. |

**示例：**

```TypeScript
import { dlpPermission } from '@kit.DataProtectionKit';

dlpPermission.getDLPFileAccessRecords((err, accessRecords) => {
  if (err != undefined) {
    console.error('getDLPFileAccessRecords error,', err.code, err.message);
  } else {
    console.info('accessRecords', JSON.stringify(accessRecords));
  }
}); // 获取DLP访问列表。

```

