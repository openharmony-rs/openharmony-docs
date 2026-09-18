# importWrappedKeyItemAsUser（系统接口）

## 导入模块

```TypeScript
import { huks } from '@kit.UniversalKeystoreKit';
```

## importWrappedKeyItemAsUser

```TypeScript
function importWrappedKeyItemAsUser(
    userId: number, keyAlias: string,
    wrappingKeyAlias: string,
    huksOptions: HuksOptions
  ): Promise<void>
```

Import Wrapped Key As User.

**起始版本：** 12

**需要权限：** ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS

**系统能力：** SystemCapability.Security.Huks.Extension

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| userId | number | 是 | User ID. |
| keyAlias | string | 是 | Alias of the wrapped key to import. |
| wrappingKeyAlias | string | 是 | Alias of the key used to decrypt the wrapped key. |
| huksOptions | [HuksOptions](arkts-universalkeystore-huks-huksoptions-i.md) | 是 | Options for importing the wrapped key. The algorithm, key purpose, and key length are mandatory. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | the application permission is not sufficient, which may be caused by lack of<br>cross-account permission, or the system has not been unlocked by user, or the user does not exist. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | non-system applications are not allowed to use system APIs. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | api is not supported |
| [12000001](../errorcode-huks.md#12000001-该子功能不支持特性) | Feature is not supported. Possible causes: 1. The algorithm mode is not supported. 2. The group key is not supported. 3. The crypto extension key is not supported. |
| [12000002](../errorcode-huks.md#12000002-缺少密钥算法参数) | algorithm param is missing |
| [12000003](../errorcode-huks.md#12000003-无效的密钥算法参数) | algorithm param is invalid |
| [12000004](../errorcode-huks.md#12000004-文件错误) | operating file failed |
| [12000005](../errorcode-huks.md#12000005-进程通信错误) | IPC communication failed |
| [12000006](../errorcode-huks.md#12000006-算法库操作失败) | error occurred in crypto engine |
| [12000011](../errorcode-huks.md#12000011-目标对象不存在) | queried entity does not exist |
| [12000012](../errorcode-huks.md#12000012-外部错误) | Device environment or input parameter abnormal |
| [12000013](../errorcode-huks.md#12000013-密钥设置生物访问控制时待绑定的凭据不存在) | queried credential does not exist |
| [12000014](../errorcode-huks.md#12000014-内存不足) | memory is insufficient |
| [12000015](../errorcode-huks.md#12000015-调用其他系统服务失败) | Failed to obtain the security information via UserIAM |
| [12000017](../errorcode-huks.md#12000017-同名密钥已存在) | The key with the same alias already exists<br>**适用版本：** 20+ |

**示例**

```TypeScript
以下代码示例接口调用的前置条件同上文generateKeyItemAsUser的前置条件。

注意：下文密码学相关的变量（如initializationVector、associatedData、nonce）赋值，均为参考样例，不能直接适用于业务功能逻辑。开发者需要根据自身场景使用合适的初始值。
```
