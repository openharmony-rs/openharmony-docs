# deactivateUserKey（系统接口）

## deactivateUserKey

```TypeScript
function deactivateUserKey(userId: number):void
```

用户锁屏时，同步卸载指定用户对应密钥。**（该接口目前仅开放给锁屏应用）**

**起始版本：** 15

**需要权限：** ohos.permission.STORAGE_MANAGER_CRYPT

**系统能力：** SystemCapability.FileManagement.StorageService.Encryption

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| userId | number | 是 | 用户id。锁屏应用感知设备当前登录的用户，指定为该用户。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-Permission) | Permission verification failed. |
| [202](../../errorcode-universal.md#202-The) | The caller is not a system application. |
| [401](../../errorcode-universal.md#401-The) | The input parameter is invalid. Possible causes: Mandatory<br/>parameters are left unspecified; Or input parameter has type different from the type the interface requires. |
| [13600001](../../errorcode-universal.md#13600001-IPC) | IPC error. |
| [13600008](../../errorcode-universal.md#13600008-No) | No such object. Possible causes: Cannot find userkey for the specified user. |
| [13600009](../../errorcode-universal.md#13600009-User) | User ID out of range. Possible causes: input parameter userId 10736. |

**示例：**

```TypeScript
import { keyManager } from "@kit.CoreFileKit";
import { BusinessError } from '@kit.BasicServicesKit';
let userId: number = 100;
try {
  keyManager.deactivateUserKey(userId);
  console.info("deactivateUserKey success");
} catch (err) {
  let error: BusinessError = err as BusinessError;
  console.error("deactivateUserKey failed with error:" + JSON.stringify(error));
}

```

