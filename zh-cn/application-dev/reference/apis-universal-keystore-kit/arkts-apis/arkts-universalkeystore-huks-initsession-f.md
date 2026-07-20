# initSession

## 导入模块

```TypeScript
import { huks } from '@kit.UniversalKeystoreKit';
```

<a id="initsession"></a>
## initSession

```TypeScript
function initSession(keyAlias: string, options: HuksOptions, callback: AsyncCallback<HuksSessionHandle>): void
```

initSession操作密钥接口。使用callback异步回调。

huks.initSession、huks.updateSession、huks.finishSession为三段式接口，需要一起使用。

> **说明：**  
>  
> 初始化[HuksKeySecurityLevel](arkts-universalkeystore-huks-hukskeysecuritylevel-e.md)中定义的SE安全级别密钥会话需要ohos.permission.ACCESS_SE_KEY权限。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-huks-function initSession(keyAlias: string, options: HuksOptions, callback: AsyncCallback<HuksSessionHandle>): void--><!--Device-huks-function initSession(keyAlias: string, options: HuksOptions, callback: AsyncCallback<HuksSessionHandle>): void-End-->

**系统能力：** SystemCapability.Security.Huks.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| keyAlias | string | 是 | initSession操作密钥的别名。 |
| options | [HuksOptions](arkts-universalkeystore-huks-huksoptions-i.md) | 是 | initSession操作的参数集合。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;HuksSessionHandle&gt; | 是 | 回调函数。当密钥操作init成功时，err为undefined，data为获取到的HuksSessionHandle；否则为错误对象。HuksSessionHandle的handle返回initSession生成的handle。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | The application permissions are insufficient, possibly because the ohos.permission.ACCESS_SE_KEY permission is missing.<br>**适用版本：** 26.0.0+ |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Mandatory parameters are left unspecified.2. Incorrect parameter types.3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | api is not supported |
| [12000001](../errorcode-huks.md#12000001-该子功能不支持特性) | algorithm mode is not supported |
| [12000002](../errorcode-huks.md#12000002-缺少密钥算法参数) | algorithm param is missing |
| [12000003](../errorcode-huks.md#12000003-无效的密钥算法参数) | algorithm param is invalid |
| [12000004](../errorcode-huks.md#12000004-文件错误) | operating file failed |
| [12000005](../errorcode-huks.md#12000005-进程通信错误) | IPC communication failed |
| [12000006](../errorcode-huks.md#12000006-算法库操作失败) | error occurred in crypto engine or UKey driver |
| [12000010](../errorcode-huks.md#12000010-密钥操作会话数已达上限) | the number of sessions has reached limit |
| [12000011](../errorcode-huks.md#12000011-目标对象不存在) | queried entity does not exist |
| [12000012](../errorcode-huks.md#12000012-外部错误) | Device environment or input parameter abnormal |
| [12000014](../errorcode-huks.md#12000014-内存不足) | memory is insufficient |
| [12000018](../errorcode-huks.md#12000018-输入参数非法) | the input parameter is invalid. Possible causes:1. the aead length is invalid.2. the group id specified by the access group tag is invalid.<br>**适用版本：** 22+ |
| [12000020](../errorcode-huks.md#12000020-依赖的模块报错) | the provider operation failed<br>**适用版本：** 22+ |
| [12000021](../errorcode-huks.md#12000021-ukey-pin码被锁定) | the UKey PIN is locked<br>**适用版本：** 22+ |
| [12000023](../errorcode-huks.md#12000023-ukey-pin码未认证) | the UKey PIN not authenticated<br>**适用版本：** 22+ |
| [12000024](../errorcode-huks.md#12000024-设备或资源繁忙) | the provider or UKey is busy<br>**适用版本：** 22+ |
| [12000026](../errorcode-huks.md#12000026-安全元件故障) | the secure element is not available<br>**适用版本：** 26.0.0+ |


<a id="initsession-1"></a>
## initSession

```TypeScript
function initSession(keyAlias: string, options: HuksOptions): Promise<HuksSessionHandle>
```

initSession操作密钥接口。使用Promise异步回调。

huks.initSession、huks.updateSession、huks.finishSession为三段式接口，需要一起使用。

> **说明：**  
>  
> 初始化[HuksKeySecurityLevel](arkts-universalkeystore-huks-hukskeysecuritylevel-e.md)中定义的SE安全级别密钥会话需要ohos.permission.ACCESS_SE_KEY权限。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-huks-function initSession(keyAlias: string, options: HuksOptions): Promise<HuksSessionHandle>--><!--Device-huks-function initSession(keyAlias: string, options: HuksOptions): Promise<HuksSessionHandle>-End-->

**系统能力：** SystemCapability.Security.Huks.Extension

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| keyAlias | string | 是 | initSession操作密钥的别名。 |
| options | [HuksOptions](arkts-universalkeystore-huks-huksoptions-i.md) | 是 | initSession参数集合。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;HuksSessionHandle&gt; | Promise对象，返回HuksSessionHandle。HuksSessionHandle的handle返回initSession生成的handle。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | The application permissions are insufficient, possibly because the ohos.permission.ACCESS_SE_KEY permission is missing.<br>**适用版本：** 26.0.0+ |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Mandatory parameters are left unspecified.2. Incorrect parameter types.3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | api is not supported |
| [12000001](../errorcode-huks.md#12000001-该子功能不支持特性) | algorithm mode is not supported |
| [12000002](../errorcode-huks.md#12000002-缺少密钥算法参数) | algorithm param is missing |
| [12000003](../errorcode-huks.md#12000003-无效的密钥算法参数) | algorithm param is invalid |
| [12000004](../errorcode-huks.md#12000004-文件错误) | operating file failed |
| [12000005](../errorcode-huks.md#12000005-进程通信错误) | IPC communication failed |
| [12000006](../errorcode-huks.md#12000006-算法库操作失败) | error occurred in crypto engine or UKey driver |
| [12000010](../errorcode-huks.md#12000010-密钥操作会话数已达上限) | the number of sessions has reached limit |
| [12000011](../errorcode-huks.md#12000011-目标对象不存在) | queried entity does not exist |
| [12000012](../errorcode-huks.md#12000012-外部错误) | Device environment or input parameter abnormal |
| [12000014](../errorcode-huks.md#12000014-内存不足) | memory is insufficient |
| [12000018](../errorcode-huks.md#12000018-输入参数非法) | the input parameter is invalid. Possible causes:1. the aead length is invalid.2. the group id specified by the access group tag is invalid.<br>**适用版本：** 22+ |
| [12000020](../errorcode-huks.md#12000020-依赖的模块报错) | the provider operation failed<br>**适用版本：** 22+ |
| [12000021](../errorcode-huks.md#12000021-ukey-pin码被锁定) | the UKey PIN is locked<br>**适用版本：** 22+ |
| [12000023](../errorcode-huks.md#12000023-ukey-pin码未认证) | the UKey PIN not authenticated<br>**适用版本：** 22+ |
| [12000024](../errorcode-huks.md#12000024-设备或资源繁忙) | the provider or UKey is busy<br>**适用版本：** 22+ |
| [12000026](../errorcode-huks.md#12000026-安全元件故障) | the secure element is not available<br>**适用版本：** 26.0.0+ |

