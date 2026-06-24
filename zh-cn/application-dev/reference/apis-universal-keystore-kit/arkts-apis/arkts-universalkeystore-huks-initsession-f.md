# initSession

## initSession

```TypeScript
function initSession(keyAlias: string, options: HuksOptions, callback: AsyncCallback<HuksSessionHandle>): void
```

initSession������Կ�ӿڡ�ʹ��callback�첽�ص���

huks.initSession��huks.updateSession��huks.finishSessionΪ����ʽ�ӿڣ���Ҫһ��ʹ�á�

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Security.Huks.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| keyAlias | string | 是 | initSession������Կ�ı����� |
| options | HuksOptions | 是 | initSession�����Ĳ������ϡ� |
| callback | AsyncCallback&lt;HuksSessionHandle&gt; | 是 | �ص�����������Կ����init�ɹ�ʱ��errΪundefined��dataΪ��ȡ����HuksSessionHandle����<br/>��Ϊ�������HuksSessionHandle��handle����initSession���ɵ�handle�� |

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
| [12000010](../../errorcode-universal.md#12000010-the) | the number of sessions has reached limit |
| [12000011](../../errorcode-universal.md#12000011-queried) | queried entity does not exist |
| [12000012](../../errorcode-universal.md#12000012-Device) | Device environment or input parameter abnormal |
| [12000014](../../errorcode-universal.md#12000014-memory) | memory is insufficient |
| [12000018](../../errorcode-universal.md#12000018-the) | the input parameter is invalid. Possible causes:<br/>1. the aead length is invalid.<br/>2. the group id specified by the access group tag is invalid.&lt;br&gt;**适用版本：** 22+ |
| [12000020](../../errorcode-universal.md#12000020-the) | the provider operation failed&lt;br&gt;**适用版本：** 22+ |
| [12000021](../../errorcode-universal.md#12000021-the) | the UKey PIN is locked&lt;br&gt;**适用版本：** 22+ |
| [12000023](../../errorcode-universal.md#12000023-the) | the UKey PIN not authenticated&lt;br&gt;**适用版本：** 22+ |
| [12000024](../../errorcode-universal.md#12000024-the) | the provider or UKey is busy&lt;br&gt;**适用版本：** 22+ |
| [12000026](../../errorcode-universal.md#12000026-the) | the secure element is not available&lt;br&gt;**适用版本：** 26.0.0+ |


## initSession

```TypeScript
function initSession(keyAlias: string, options: HuksOptions): Promise<HuksSessionHandle>
```

initSession������Կ�ӿڡ�ʹ��Promise�첽�ص���

huks.initSession��huks.updateSession��huks.finishSessionΪ����ʽ�ӿڣ���Ҫһ��ʹ�á�

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Security.Huks.Extension

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| keyAlias | string | 是 | initSession������Կ�ı����� |
| options | HuksOptions | 是 | initSession�������ϡ� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;HuksSessionHandle&gt; | Promise���󣬷���HuksSessionHandle��HuksSessionHandle��handle����initSession���ɵ�<br/>handle�� |

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
| [12000010](../../errorcode-universal.md#12000010-the) | the number of sessions has reached limit |
| [12000011](../../errorcode-universal.md#12000011-queried) | queried entity does not exist |
| [12000012](../../errorcode-universal.md#12000012-Device) | Device environment or input parameter abnormal |
| [12000014](../../errorcode-universal.md#12000014-memory) | memory is insufficient |
| [12000018](../../errorcode-universal.md#12000018-the) | the input parameter is invalid. Possible causes:<br/>1. the aead length is invalid.<br/>2. the group id specified by the access group tag is invalid.&lt;br&gt;**适用版本：** 22+ |
| [12000020](../../errorcode-universal.md#12000020-the) | the provider operation failed&lt;br&gt;**适用版本：** 22+ |
| [12000021](../../errorcode-universal.md#12000021-the) | the UKey PIN is locked&lt;br&gt;**适用版本：** 22+ |
| [12000023](../../errorcode-universal.md#12000023-the) | the UKey PIN not authenticated&lt;br&gt;**适用版本：** 22+ |
| [12000024](../../errorcode-universal.md#12000024-the) | the provider or UKey is busy&lt;br&gt;**适用版本：** 22+ |
| [12000026](../../errorcode-universal.md#12000026-the) | the secure element is not available&lt;br&gt;**适用版本：** 26.0.0+ |

