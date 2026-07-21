# finishSession

## 导入模块

```TypeScript
import { huks } from '@kit.UniversalKeystoreKit';
```

<a id="finishsession"></a>
## finishSession

```TypeScript
function finishSession(handle: number, options: HuksOptions, callback: AsyncCallback<HuksReturnResult>): void
```

finishSession操作密钥接口。使用callback异步回调。

huks.initSession、huks.updateSession、huks.finishSession为三段式接口，需要一起使用。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-huks-function finishSession(handle: number, options: HuksOptions, callback: AsyncCallback<HuksReturnResult>): void--><!--Device-huks-function finishSession(handle: number, options: HuksOptions, callback: AsyncCallback<HuksReturnResult>): void-End-->

**系统能力：** SystemCapability.Security.Huks.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| handle | number | 是 | finishSession操作的uint64类型的handle值。 |
| options | [HuksOptions](arkts-universalkeystore-huks-huksoptions-i.md) | 是 | finishSession的参数集合。 |
| callback | AsyncCallback&lt;HuksReturnResult&gt; | 是 | 回调函数。当密钥操作finish成功时，err为undefined，data为获取到的HuksReturnResult；否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes:1. Mandatory parameters are left unspecified.2. Incorrect parameter types.3. Parameter verification failed. |
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
| [12000017](../errorcode-huks.md#12000017-同名密钥已存在) | The key with the same alias already exists<br>**适用版本：** 20+ |
| [12000020](../errorcode-huks.md#12000020-依赖的模块报错) | the provider operation failed<br>**适用版本：** 22+ |
| [12000021](../errorcode-huks.md#12000021-ukey-pin码被锁定) | the UKey PIN is locked<br>**适用版本：** 22+ |
| [12000023](../errorcode-huks.md#12000023-ukey-pin码未认证) | the UKey PIN not authenticated<br>**适用版本：** 22+ |
| [12000024](../errorcode-huks.md#12000024-设备或资源繁忙) | the provider or UKey is busy<br>**适用版本：** 22+ |
| [12000018](../errorcode-huks.md#12000018-输入参数非法) | the group id specified by the access group tag is invalid<br>**适用版本：** 23+ |
| [12000026](../errorcode-huks.md#12000026-安全元件故障) | the secure element is not available<br>**适用版本：** 26.0.0+ |


<a id="finishsession-1"></a>
## finishSession

```TypeScript
function finishSession(
    handle: number,
    options: HuksOptions,
    token: Uint8Array,
    callback: AsyncCallback<HuksReturnResult>
  ): void
```

Finishes the key operation. This API uses an asynchronous callback to return the result.huks.initSession, huks.updateSession, and huks.finishSession must be used together.

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-huks-function finishSession(handle: number,options: HuksOptions,token: Uint8Array,callback: AsyncCallback<HuksReturnResult>): void--><!--Device-huks-function finishSession(handle: number,options: HuksOptions,token: Uint8Array,callback: AsyncCallback<HuksReturnResult>): void-End-->

**系统能力：** SystemCapability.Security.Huks.Extension

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| handle | number | 是 | Handle for the finishSession operation.<br>取值限定为整数。 |
| options | [HuksOptions](arkts-universalkeystore-huks-huksoptions-i.md) | 是 | Parameter set used for the **finishSession** operation. |
| token | Uint8Array | 是 | Authentication token for [refined key access control]. |
| callback | AsyncCallback&lt;HuksReturnResult&gt; | 是 | Callback used to return the result. If the operation is successful, **err** is **undefined**, and **data** is the obtained **HuksReturnResult**. Otherwise, **err** is an error object. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes:1. Mandatory parameters are left unspecified.2. Incorrect parameter types.3. Parameter verification failed. |
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
| [12000017](../errorcode-huks.md#12000017-同名密钥已存在) | The key with the same alias already exists<br>**适用版本：** 20+ |
| [12000018](../errorcode-huks.md#12000018-输入参数非法) | the group id specified by the access group tag is invalid<br>**适用版本：** 23+ |
| [12000026](../errorcode-huks.md#12000026-安全元件故障) | the secure element is not available<br>**适用版本：** 26.0.0+ |


<a id="finishsession-2"></a>
## finishSession

```TypeScript
function finishSession(handle: number, options: HuksOptions, token?: Uint8Array): Promise<HuksReturnResult>
```

finishSession操作密钥接口。使用Promise异步回调。

huks.initSession、huks.updateSession、huks.finishSession为三段式接口，需要一起使用。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-huks-function finishSession(handle: number, options: HuksOptions, token?: Uint8Array): Promise<HuksReturnResult>--><!--Device-huks-function finishSession(handle: number, options: HuksOptions, token?: Uint8Array): Promise<HuksReturnResult>-End-->

**系统能力：** SystemCapability.Security.Huks.Extension

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| handle | number | 是 | finishSession操作的uint64类型的handle值。 |
| options | [HuksOptions](arkts-universalkeystore-huks-huksoptions-i.md) | 是 | finishSession操作的参数集合。 |
| token | Uint8Array | 否 | 密钥[二次认证密钥访问控制](../../../security/UniversalKeystoreKit/huks-identity-authentication-overview.md#二次认证密钥访问控制)的用户鉴权证明(AuthToken)，不填表示不进行二次认证密钥访问控制。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;HuksReturnResult&gt; | Promise对象，返回调用接口的结果。当调用成功时，HuksReturnResult的outData成员为对应操作返回的数据。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes:1. Mandatory parameters are left unspecified.2. Incorrect parameter types.3. Parameter verification failed. |
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
| [12000017](../errorcode-huks.md#12000017-同名密钥已存在) | The key with the same alias already exists<br>**适用版本：** 20+ |
| [12000020](../errorcode-huks.md#12000020-依赖的模块报错) | the provider operation failed<br>**适用版本：** 22+ |
| [12000021](../errorcode-huks.md#12000021-ukey-pin码被锁定) | the UKey PIN is locked<br>**适用版本：** 22+ |
| [12000023](../errorcode-huks.md#12000023-ukey-pin码未认证) | the UKey PIN not authenticated<br>**适用版本：** 22+ |
| [12000024](../errorcode-huks.md#12000024-设备或资源繁忙) | the provider or UKey is busy<br>**适用版本：** 22+ |
| [12000018](../errorcode-huks.md#12000018-输入参数非法) | the group id specified by the access group tag is invalid<br>**适用版本：** 23+ |
| [12000026](../errorcode-huks.md#12000026-安全元件故障) | the secure element is not available<br>**适用版本：** 26.0.0+ |

