# revokePermission

## revokePermission

```TypeScript
function revokePermission(policies: Array<PolicyInfo>): Promise<void>
```

对所选择的多个文件或目录URI取消持久化授权，使用Promise异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**需要权限：** ohos.permission.FILE_ACCESS_PERSIST

<!--Device-fileShare-function revokePermission(policies: Array<PolicyInfo>): Promise<void>--><!--Device-fileShare-function revokePermission(policies: Array<PolicyInfo>): Promise<void>-End-->

**系统能力：** SystemCapability.FileManagement.AppFileService.FolderAuthorization

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| policies | Array&lt;[PolicyInfo](arkts-corefile-fileshare-policyinfo-i.md)&gt; | 是 | 需要取消持久化授权的URI策略信息数组。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error.Possible causes:1.Mandatory parameters are left unspecified; &lt;br&gt;2.Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| 13900001 | Operation not permitted. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed, usually the result returned by VerifyAccessToken. |
| 13900042 | Out of memory |

## 示例

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { picker } from '@kit.CoreFileKit';

async function revokePermissionExample() {
  try {
    let documentSelectOptions = new picker.DocumentSelectOptions();
    let documentPicker = new picker.DocumentViewPicker();
    let uris = await documentPicker.select(documentSelectOptions);
    if (uris.length === 0) {
      console.error('No file selected');
      return;
    }
    let policyInfo: fileShare.PolicyInfo = {
      uri: uris[0],
      // 可以组合取消多个权限，例如读写权限可使用 fileShare.OperationMode.READ_MODE | fileShare.OperationMode.WRITE_MODE
      operationMode: fileShare.OperationMode.READ_MODE,
    };
    let policies: Array<fileShare.PolicyInfo> = [policyInfo];
    fileShare.revokePermission(policies).then(() => {
      console.info('revokePermission successfully');
    }).catch((err: BusinessError<Array<fileShare.PolicyErrorResult>>) => {
      console.error(`revokePermission failed with error message: ${err.message}, error code: ${err.code}`);
      if (err.code === 13900001 && err.data) {
        for (let i = 0; i < err.data.length; i++) {
          console.error(`error code: ${JSON.stringify(err.data[i].code)}`);
          console.error(`error URI: ${JSON.stringify(err.data[i].uri)}`);
          console.error(`error reason: ${JSON.stringify(err.data[i].message)}`);
        }
      }
    });
  } catch (error) {
    let err: BusinessError = error as BusinessError;
    console.error(`revokePermission failed with err: ${JSON.stringify(err)}`);
  }
}
```

