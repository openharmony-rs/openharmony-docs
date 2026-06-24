# updateSession

## updateSession

```TypeScript
function updateSession(handle: number, options: HuksOptions, callback: AsyncCallback<HuksReturnResult>): void
```

updateSession������Կ�ӿڡ�ʹ��callback�첽�ص���

huks.initSession��huks.updateSession��huks.finishSessionΪ����ʽ�ӿڣ���Ҫһ��ʹ�á�

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Security.Huks.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| handle | number | 是 | updateSession������uint64���͵�handleֵ�� |
| options | HuksOptions | 是 | updateSession�Ĳ������ϡ� |
| callback | AsyncCallback&lt;HuksReturnResult&gt; | 是 | �ص�����������Կ����update�ɹ�ʱ��errΪundefined��dataΪ��ȡ����HuksReturnResult����<br/>��Ϊ������� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes:<br/>1. Mandatory parameters are left unspecified.<br/>2. Incorrect parameter types.<br/>3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-api) | api is not supported |
| [12000001](../../errorcode-universal.md#12000001-algorithm) | algorithm mode is not supported |
| [12000002](../../errorcode-universal.md#12000002-algorithm) | algorithm param is missing |
| [12000003](../../errorcode-universal.md#12000003-algorithm) | algorithm param is invalid |
| [12000004](../../errorcode-universal.md#12000004-operating) | operating file failed |
| [12000005](../../errorcode-universal.md#12000005-IPC) | IPC communication failed |
| [12000006](../../errorcode-universal.md#12000006-error) | error occurred in crypto engine or UKey driver |
| [12000007](../../errorcode-universal.md#12000007-this) | this credential is already invalidated permanently |
| [12000008](../../errorcode-universal.md#12000008-verify) | verify auth token failed |
| [12000009](../../errorcode-universal.md#12000009-auth) | auth token is already timeout |
| [12000011](../../errorcode-universal.md#12000011-queried) | queried entity does not exist |
| [12000012](../../errorcode-universal.md#12000012-Device) | Device environment or input parameter abnormal |
| [12000014](../../errorcode-universal.md#12000014-memory) | memory is insufficient |
| [12000020](../../errorcode-universal.md#12000020-the) | the provider operation failed&lt;br&gt;**适用版本：** 22+ |
| [12000021](../../errorcode-universal.md#12000021-the) | the UKey PIN is locked&lt;br&gt;**适用版本：** 22+ |
| [12000023](../../errorcode-universal.md#12000023-the) | the UKey PIN not authenticated&lt;br&gt;**适用版本：** 22+ |
| [12000024](../../errorcode-universal.md#12000024-the) | the provider or UKey is busy&lt;br&gt;**适用版本：** 22+ |
| [12000018](../../errorcode-universal.md#12000018-the) | the group id specified by the access group tag is invalid&lt;br&gt;**适用版本：** 23+ |
| [12000026](../../errorcode-universal.md#12000026-the) | the secure element is not available&lt;br&gt;**适用版本：** 26.0.0+ |


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

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Security.Huks.Extension

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| handle | number | 是 | Handle of the **updateSession** operation, which is of the uint64 type. |
| options | HuksOptions | 是 | Parameter set used for the **updateSession** operation. |
| token | Uint8Array | 是 | Authentication token for<br/>[refined key access control](../../../../security/UniversalKeystoreKit/huks-identity-authentication-overview.md#refined-key-access-control)<br/>. |
| callback | AsyncCallback&lt;HuksReturnResult&gt; | 是 | Callback used to return the result. If the operation is<br/>successful, **err** is **undefined**, and **data** is the obtained **HuksReturnResult**. Otherwise, **err** is<br/>an error object. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes:<br/>1. Mandatory parameters are left unspecified.<br/>2. Incorrect parameter types.<br/>3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-api) | api is not supported |
| [12000001](../../errorcode-universal.md#12000001-algorithm) | algorithm mode is not supported |
| [12000002](../../errorcode-universal.md#12000002-algorithm) | algorithm param is missing |
| [12000003](../../errorcode-universal.md#12000003-algorithm) | algorithm param is invalid |
| [12000004](../../errorcode-universal.md#12000004-operating) | operating file failed |
| [12000005](../../errorcode-universal.md#12000005-IPC) | IPC communication failed |
| [12000006](../../errorcode-universal.md#12000006-error) | error occurred in crypto engine |
| [12000007](../../errorcode-universal.md#12000007-this) | this credential is already invalidated permanently |
| [12000008](../../errorcode-universal.md#12000008-verify) | verify auth token failed |
| [12000009](../../errorcode-universal.md#12000009-auth) | auth token is already timeout |
| [12000011](../../errorcode-universal.md#12000011-queried) | queried entity does not exist |
| [12000012](../../errorcode-universal.md#12000012-Device) | Device environment or input parameter abnormal |
| [12000014](../../errorcode-universal.md#12000014-memory) | memory is insufficient |
| [12000018](../../errorcode-universal.md#12000018-the) | the group id specified by the access group tag is invalid&lt;br&gt;**适用版本：** 23+ |
| [12000026](../../errorcode-universal.md#12000026-the) | the secure element is not available&lt;br&gt;**适用版本：** 26.0.0+ |


## updateSession

```TypeScript
function updateSession(handle: number, options: HuksOptions, token?: Uint8Array): Promise<HuksReturnResult>
```

updateSession������Կ�ӿڡ�ʹ��Promise�첽�ص���

huks.initSession��huks.updateSession��huks.finishSessionΪ����ʽ�ӿڣ���Ҫһ��ʹ�á�

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Security.Huks.Extension

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| handle | number | 是 | updateSession������uint64���͵�handleֵ�� |
| options | HuksOptions | 是 | updateSession�����Ĳ������ϡ� |
| token | Uint8Array | 否 | ��Կ<br/>[������֤��Կ���ʿ���](../../../../security/UniversalKeystoreKit/huks-identity-authentication-overview.md#������֤��Կ���ʿ���)���û���Ȩ֤<br/>��(AuthToken)�������ʾ�����ж�����֤��Կ���ʿ��ơ� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;HuksReturnResult&gt; | Promise���󣬷��ص��ýӿڵĽ�������óɹ�ʱ����ʹ��AES/DES/3DES/SM4��Կ�ӽ���ʱ��HuksReturnResult��outData<br/>��Ա�����ؼ��ܺ�����Ļ��߽��ܺ�����ģ�����outDataΪ�ա� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes:<br/>1. Mandatory parameters are left unspecified.<br/>2. Incorrect parameter types.<br/>3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-api) | api is not supported |
| [12000001](../../errorcode-universal.md#12000001-algorithm) | algorithm mode is not supported |
| [12000002](../../errorcode-universal.md#12000002-algorithm) | algorithm param is missing |
| [12000003](../../errorcode-universal.md#12000003-algorithm) | algorithm param is invalid |
| [12000004](../../errorcode-universal.md#12000004-operating) | operating file failed |
| [12000005](../../errorcode-universal.md#12000005-IPC) | IPC communication failed |
| [12000006](../../errorcode-universal.md#12000006-error) | error occurred in crypto engine or UKey driver |
| [12000007](../../errorcode-universal.md#12000007-this) | this credential is already invalidated permanently |
| [12000008](../../errorcode-universal.md#12000008-verify) | verify auth token failed |
| [12000009](../../errorcode-universal.md#12000009-auth) | auth token is already timeout |
| [12000011](../../errorcode-universal.md#12000011-queried) | queried entity does not exist |
| [12000012](../../errorcode-universal.md#12000012-Device) | Device environment or input parameter abnormal |
| [12000014](../../errorcode-universal.md#12000014-memory) | memory is insufficient |
| [12000020](../../errorcode-universal.md#12000020-the) | the provider operation failed&lt;br&gt;**适用版本：** 22+ |
| [12000021](../../errorcode-universal.md#12000021-the) | the UKey PIN is locked&lt;br&gt;**适用版本：** 22+ |
| [12000023](../../errorcode-universal.md#12000023-the) | the UKey PIN not authenticated&lt;br&gt;**适用版本：** 22+ |
| [12000024](../../errorcode-universal.md#12000024-the) | the provider or UKey is busy&lt;br&gt;**适用版本：** 22+ |
| [12000018](../../errorcode-universal.md#12000018-the) | the group id specified by the access group tag is invalid&lt;br&gt;**适用版本：** 23+ |
| [12000026](../../errorcode-universal.md#12000026-the) | the secure element is not available&lt;br&gt;**适用版本：** 26.0.0+ |

