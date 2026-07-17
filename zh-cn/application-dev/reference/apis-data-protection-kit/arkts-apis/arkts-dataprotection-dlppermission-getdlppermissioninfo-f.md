# getDLPPermissionInfo

## 导入模块

```TypeScript
import { dlpPermission } from '@kit.DataProtectionKit';
```

## getDLPPermissionInfo

```TypeScript
function getDLPPermissionInfo(): Promise<DLPPermissionInfo>
```

查询当前DLP沙箱的权限信息，包括文件授权类型及可执行操作（如查看、编辑、复制等）。仅支持在DLP沙箱应用中调用，使用Promise异步回调。

在DLP沙箱中处理文件时，可根据权限信息判断当前用户可以执行哪些操作，避免调用无权限的功能。

**起始版本：** 10

<!--Device-dlpPermission-function getDLPPermissionInfo(): Promise<DLPPermissionInfo>--><!--Device-dlpPermission-function getDLPPermissionInfo(): Promise<DLPPermissionInfo>-End-->

**系统能力：** SystemCapability.Security.DataLossPrevention

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<DLPPermissionInfo> | Promise对象。返回查询的DLP文件的权限信息，无异常则表明查询成功。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [19100001](../errorcode-dlp.md#19100001-入参错误) | Invalid parameter value. |
| [19100006](../errorcode-dlp.md#19100006-非dlp沙箱应用) | No permission to call this API,which is available only for DLP sandbox applications. |
| [19100011](../errorcode-dlp.md#19100011-系统服务工作异常) | The system ability works abnormally. |

**示例：**

```TypeScript
import { dlpPermission } from '@kit.DataProtectionKit';

dlpPermission.isInSandbox().then(async (inSandbox) => { // 是否在沙箱内。
  if (inSandbox) {
    dlpPermission.getDLPPermissionInfo().then((permissionInfo: dlpPermission.DLPPermissionInfo) => {
      console.info('permissionInfo', JSON.stringify(permissionInfo));
    }).catch((error: BusinessError)=> {
      console.error(JSON.stringify(error));
    })
  }
});

```


## getDLPPermissionInfo

```TypeScript
function getDLPPermissionInfo(callback: AsyncCallback<DLPPermissionInfo>): void
```

查询当前DLP沙箱的权限信息。返回的权限信息包括文件的授权类型和可执行的操作权限(如查看、编辑、复制等)。仅支持在DLP沙箱应用中调用。使用callback异步回调。

在DLP沙箱中处理文件时，可根据权限信息判断当前用户可以执行哪些操作，避免调用无权限的功能。

**起始版本：** 10

<!--Device-dlpPermission-function getDLPPermissionInfo(callback: AsyncCallback<DLPPermissionInfo>): void--><!--Device-dlpPermission-function getDLPPermissionInfo(callback: AsyncCallback<DLPPermissionInfo>): void-End-->

**系统能力：** SystemCapability.Security.DataLossPrevention

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<DLPPermissionInfo> | 是 | 回调函数。err为undefined时表示查询成功；否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Incorrect parameter types. |
| [19100001](../errorcode-dlp.md#19100001-入参错误) | Invalid parameter value. |
| [19100006](../errorcode-dlp.md#19100006-非dlp沙箱应用) | No permission to call this API,which is available only for DLP sandbox applications. |
| [19100011](../errorcode-dlp.md#19100011-系统服务工作异常) | The system ability works abnormally. |

**示例：**

```TypeScript
import { dlpPermission } from '@kit.DataProtectionKit';

dlpPermission.isInSandbox().then((inSandbox) => { // 是否在沙箱内。
  if (inSandbox) {
    dlpPermission.getDLPPermissionInfo((err, permissionInfo) => { 
      if (err != undefined) {
        console.error('getDLPPermissionInfo error', err.code, err.message);
      } else {
        console.info('permissionInfo', JSON.stringify(permissionInfo));
      }
    }); // 获取当前权限信息。
  }
});

```

