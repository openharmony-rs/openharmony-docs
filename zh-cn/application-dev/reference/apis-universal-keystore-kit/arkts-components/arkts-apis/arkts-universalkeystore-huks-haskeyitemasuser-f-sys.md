# hasKeyItemAsUser（系统接口）

## 导入模块

```TypeScript
import { huks } from '@kit.UniversalKeystoreKit';
```

## hasKeyItemAsUser

```TypeScript
function hasKeyItemAsUser(userId: number, keyAlias: string, huksOptions: HuksOptions): Promise<boolean>
```

指定用户身份判断密钥是否存在，使用Promise回调异步返回结果。

**起始版本：** 12

**需要权限：** ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS

**系统能力：** SystemCapability.Security.Huks.Extension

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| userId | number | 是 | 用户ID。 |
| keyAlias | string | 是 | 所需查找的密钥的别名。 |
| huksOptions | [HuksOptions](arkts-universalkeystore-huks-huksoptions-i.md) | 是 | 用于查询时指定密钥的属性TAG，如使用[HuksAuthStorageLevel](arkts-universalkeystore-huks-huksauthstoragelevel-e.md)指定需查询密钥的安全级别，<br>可传空，当API version ≥ 12时，传空默认为CE，当API version ＜ 12时，传空默认为DE。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;boolean&gt; | Promise对象。若密钥存在，返回值为true，若密钥不存在，返回值为false。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | the application permission is not sufficient, which may be caused by lack of<br>cross-account permission, or the system has not been unlocked by user, or the user does not exist. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | non-system applications are not allowed to use system APIs. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | api is not supported |
| [12000002](../errorcode-huks.md#12000002-缺少密钥算法参数) | algorithm param is missing |
| [12000003](../errorcode-huks.md#12000003-无效的密钥算法参数) | algorithm param is invalid |
| [12000004](../errorcode-huks.md#12000004-文件错误) | operating file failed |
| [12000005](../errorcode-huks.md#12000005-进程通信错误) | IPC communication failed |
| [12000006](../errorcode-huks.md#12000006-算法库操作失败) | error occurred in crypto engine |
| [12000012](../errorcode-huks.md#12000012-外部错误) | Device environment or input parameter abnormal |
| [12000014](../errorcode-huks.md#12000014-内存不足) | memory is insufficient |
| [12000001](../errorcode-huks.md#12000001-该子功能不支持特性) | Feature is not supported. Possible causes: 1. The group key is not supported. 2. The crypto extension key is not supported.<br>**适用版本：** 23+ |

**示例**

```TypeScript
以下代码示例接口调用的前置条件同上文generateKeyItemAsUser的前置条件
```
