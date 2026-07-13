# updateSession

## updateSession

```TypeScript
function updateSession(handle: number, options: HuksOptions, callback: AsyncCallback<HuksReturnResult>): void
```

updateSession操作密钥接口。使用callback异步回调。

huks.initSession、huks.updateSession、huks.finishSession为三段式接口，需要一起使用。

**起始版本：** 9

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Security.Huks.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| handle | number | 是 | updateSession操作的uint64类型的handle值。 |
| options | HuksOptions | 是 | updateSession的参数集合。 |
| callback | AsyncCallback&lt;HuksReturnResult&gt; | 是 | 回调函数。当密钥操作update成功时，err为undefined，data为获取到的HuksReturnResult；否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Mandatory parameters are left unspecified.2. Incorrect parameter types.3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | api is not supported |
| [12000001](../errorcode-huks.md#12000001-该子功能不支持特性) | algorithm mode is not supported |
| [12000002](../errorcode-huks.md#12000002-缺少密钥算法参数) | algorithm param is missing |
| [12000003](../errorcode-huks.md#12000003-无效的密钥算法参数) | algorithm param is invalid |
| [12000004](../errorcode-huks.md#12000004-文件错误) | operating file failed |
| [12000005](../errorcode-huks.md#12000005-进程通信错误) | IPC communication failed |
| [12000006](../errorcode-huks.md#12000006-算法库操作失败) | error occurred in crypto engine or UKey driver |
| [12000007](../errorcode-huks.md#12000007-密钥访问失败-密钥已失效) | this credential is already invalidated permanently |
| [12000008](../errorcode-huks.md#12000008-密钥访问失败-密钥认证失败) | verify auth token failed |
| [12000009](../errorcode-huks.md#12000009-密钥访问失败-密钥访问超时) | auth token is already timeout |
| [12000011](../errorcode-huks.md#12000011-目标对象不存在) | queried entity does not exist |
| [12000012](../errorcode-huks.md#12000012-外部错误) | Device environment or input parameter abnormal |
| [12000014](../errorcode-huks.md#12000014-内存不足) | memory is insufficient |
| [12000020](../errorcode-huks.md#12000020-依赖的模块报错) | the provider operation failed<br>**适用版本：** 22+ |
| [12000021](../errorcode-huks.md#12000021-ukey-pin码被锁定) | the UKey PIN is locked<br>**适用版本：** 22+ |
| [12000023](../errorcode-huks.md#12000023-ukey-pin码未认证) | the UKey PIN not authenticated<br>**适用版本：** 22+ |
| [12000024](../errorcode-huks.md#12000024-设备或资源繁忙) | the provider or UKey is busy<br>**适用版本：** 22+ |
| [12000018](../errorcode-huks.md#12000018-输入参数非法) | the group id specified by the access group tag is invalid<br>**适用版本：** 23+ |
| [12000026](../errorcode-huks.md#12000026-安全元件故障) | the secure element is not available<br>**适用版本：** 26.0.0+ |


## updateSession

```TypeScript
function updateSession(
    handle: number,
    options: HuksOptions,
    token: Uint8Array,
    callback: AsyncCallback<HuksReturnResult>
  ): void
```

Updates the key operation by segment. This API uses an asynchronous callback to return the result.
huks.initSession, huks.updateSession, and huks.finishSession must be used together.

**起始版本：** 9

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Security.Huks.Extension

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| handle | number | 是 | Handle of the **updateSession** operation, which is of the uint64 type. |
| options | HuksOptions | 是 | Parameter set used for the **updateSession** operation. |
| token | Uint8Array | 是 | Authentication token for[refined key access control](../../../../security/UniversalKeystoreKit/huks-identity-authentication-overview.md#refined-key-access-control). |
| callback | AsyncCallback&lt;HuksReturnResult&gt; | 是 | Callback used to return the result. If the operation issuccessful, **err** is **undefined**, and **data** is the obtained **HuksReturnResult**. Otherwise, **err** isan error object. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Mandatory parameters are left unspecified.2. Incorrect parameter types.3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | api is not supported |
| [12000001](../errorcode-huks.md#12000001-该子功能不支持特性) | algorithm mode is not supported |
| [12000002](../errorcode-huks.md#12000002-缺少密钥算法参数) | algorithm param is missing |
| [12000003](../errorcode-huks.md#12000003-无效的密钥算法参数) | algorithm param is invalid |
| [12000004](../errorcode-huks.md#12000004-文件错误) | operating file failed |
| [12000005](../errorcode-huks.md#12000005-进程通信错误) | IPC communication failed |
| [12000006](../errorcode-huks.md#12000006-算法库操作失败) | error occurred in crypto engine |
| [12000007](../errorcode-huks.md#12000007-密钥访问失败-密钥已失效) | this credential is already invalidated permanently |
| [12000008](../errorcode-huks.md#12000008-密钥访问失败-密钥认证失败) | verify auth token failed |
| [12000009](../errorcode-huks.md#12000009-密钥访问失败-密钥访问超时) | auth token is already timeout |
| [12000011](../errorcode-huks.md#12000011-目标对象不存在) | queried entity does not exist |
| [12000012](../errorcode-huks.md#12000012-外部错误) | Device environment or input parameter abnormal |
| [12000014](../errorcode-huks.md#12000014-内存不足) | memory is insufficient |
| [12000018](../errorcode-huks.md#12000018-输入参数非法) | the group id specified by the access group tag is invalid<br>**适用版本：** 23+ |
| [12000026](../errorcode-huks.md#12000026-安全元件故障) | the secure element is not available<br>**适用版本：** 26.0.0+ |


## updateSession

```TypeScript
function updateSession(handle: number, options: HuksOptions, token?: Uint8Array): Promise<HuksReturnResult>
```

updateSession操作密钥接口。使用Promise异步回调。

huks.initSession、huks.updateSession、huks.finishSession为三段式接口，需要一起使用。

**起始版本：** 9

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Security.Huks.Extension

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| handle | number | 是 | updateSession操作的uint64类型的handle值。 |
| options | HuksOptions | 是 | updateSession操作的参数集合。 |
| token | Uint8Array | 否 | 密钥[二次认证密钥访问控制](../../../../security/UniversalKeystoreKit/huks-identity-authentication-overview.md#二次认证密钥访问控制)的用户鉴权证明(AuthToken)，不填表示不进行二次认证密钥访问控制。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;HuksReturnResult&gt; | Promise对象，返回调用接口的结果。调用成功时，若使用AES/DES/3DES/SM4密钥加解密时，HuksReturnResult的outData成员将返回加密后的密文或者解密后的明文；否则outData为空。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Mandatory parameters are left unspecified.2. Incorrect parameter types.3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | api is not supported |
| [12000001](../errorcode-huks.md#12000001-该子功能不支持特性) | algorithm mode is not supported |
| [12000002](../errorcode-huks.md#12000002-缺少密钥算法参数) | algorithm param is missing |
| [12000003](../errorcode-huks.md#12000003-无效的密钥算法参数) | algorithm param is invalid |
| [12000004](../errorcode-huks.md#12000004-文件错误) | operating file failed |
| [12000005](../errorcode-huks.md#12000005-进程通信错误) | IPC communication failed |
| [12000006](../errorcode-huks.md#12000006-算法库操作失败) | error occurred in crypto engine or UKey driver |
| [12000007](../errorcode-huks.md#12000007-密钥访问失败-密钥已失效) | this credential is already invalidated permanently |
| [12000008](../errorcode-huks.md#12000008-密钥访问失败-密钥认证失败) | verify auth token failed |
| [12000009](../errorcode-huks.md#12000009-密钥访问失败-密钥访问超时) | auth token is already timeout |
| [12000011](../errorcode-huks.md#12000011-目标对象不存在) | queried entity does not exist |
| [12000012](../errorcode-huks.md#12000012-外部错误) | Device environment or input parameter abnormal |
| [12000014](../errorcode-huks.md#12000014-内存不足) | memory is insufficient |
| [12000020](../errorcode-huks.md#12000020-依赖的模块报错) | the provider operation failed<br>**适用版本：** 22+ |
| [12000021](../errorcode-huks.md#12000021-ukey-pin码被锁定) | the UKey PIN is locked<br>**适用版本：** 22+ |
| [12000023](../errorcode-huks.md#12000023-ukey-pin码未认证) | the UKey PIN not authenticated<br>**适用版本：** 22+ |
| [12000024](../errorcode-huks.md#12000024-设备或资源繁忙) | the provider or UKey is busy<br>**适用版本：** 22+ |
| [12000018](../errorcode-huks.md#12000018-输入参数非法) | the group id specified by the access group tag is invalid<br>**适用版本：** 23+ |
| [12000026](../errorcode-huks.md#12000026-安全元件故障) | the secure element is not available<br>**适用版本：** 26.0.0+ |

