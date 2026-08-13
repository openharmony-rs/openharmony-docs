# checkPersistentPermission

## checkPersistentPermission

```TypeScript
function checkPersistentPermission(policies: Array<PolicyInfo>): Promise<Array<boolean>>
```

校验所选择的多个文件或目录URI是否已持久化授权，使用Promise异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-fileShare-function checkPersistentPermission(policies: Array<PolicyInfo>): Promise<Array<boolean>>--><!--Device-fileShare-function checkPersistentPermission(policies: Array<PolicyInfo>): Promise<Array<boolean>>-End-->

**系统能力：** SystemCapability.FileManagement.AppFileService.FolderAuthorization

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| policies | Array&lt;[PolicyInfo](arkts-corefile-fileshare-policyinfo-i.md)&gt; | 是 | 需要校验持久化授权状态的URI策略信息数组。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;boolean&gt;&gt; | Promise对象，返回URI权限的持久化状态数组。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error.Possible causes:1.Mandatory parameters are left unspecified; &lt;br&gt;2.Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| 13900042 | Out of memory |

## 示例

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { picker } from '@kit.CoreFileKit';

async function checkPersistentPermissionExample() {
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
      // 可以组合校验多个权限，例如读写权限可使用 fileShare.OperationMode.READ_MODE | fileShare.OperationMode.WRITE_MODE
      operationMode: fileShare.OperationMode.READ_MODE,
    };
    let policies: Array<fileShare.PolicyInfo> = [policyInfo];
    fileShare.checkPersistentPermission(policies).then(async (data) => {
      let result: Array<boolean> = data;
      for (let i = 0; i < result.length; i++) {
        console.info(`checkPersistentPermission result: ${JSON.stringify(result[i])}`);
        if (!result[i]) {
          let info: fileShare.PolicyInfo = {
            uri: policies[i].uri,
            operationMode: policies[i].operationMode,
          };
          let policy: Array<fileShare.PolicyInfo> = [info];
          await fileShare.persistPermission(policy);
        }
      }
    }).catch((err: BusinessError<Array<fileShare.PolicyErrorResult>>) => {
      console.error(`checkPersistentPermission failed with error message: ${err.message}, error code: ${err.code}`);
    });
  } catch (error) {
    let err: BusinessError = error as BusinessError;
    console.error(`checkPersistentPermission failed with err: ${JSON.stringify(err)}`);
  }
}
```

