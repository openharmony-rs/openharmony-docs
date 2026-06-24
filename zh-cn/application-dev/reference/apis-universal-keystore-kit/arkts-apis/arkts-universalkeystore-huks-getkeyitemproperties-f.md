# getKeyItemProperties

## getKeyItemProperties

```TypeScript
function getKeyItemProperties(
    keyAlias: string,
    options: HuksOptions,
    callback: AsyncCallback<HuksReturnResult>
  ): void
```

Obtains key properties. This API uses an asynchronous callback to return the result.

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Security.Huks.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| keyAlias | string | 是 | Key alias, which must be the same as the alias used when the key was generated. |
| options | HuksOptions | 是 | Empty object (leave this parameter empty). |
| callback | AsyncCallback&lt;HuksReturnResult&gt; | 是 | Callback used to return the result. If the operation is<br/>successful, **err** is **undefined**, and **data** is the obtained **HuksReturnResult**. Otherwise, **err** is<br/>an error object. **properties** of **HuksReturnResult** are the parameters required for generating a key. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes:<br/>1. Mandatory parameters are left unspecified.<br/>2. Incorrect parameter types.<br/>3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-api) | api is not supported |
| [12000001](../../errorcode-universal.md#12000001-algorithm) | algorithm mode is not supported |
| [12000002](../../errorcode-universal.md#12000002-algorithm) | algorithm param is missing&lt;br&gt;**适用版本：** 9 - 11 |
| [12000003](../../errorcode-universal.md#12000003-algorithm) | algorithm param is invalid&lt;br&gt;**适用版本：** 9 - 11 |
| [12000004](../../errorcode-universal.md#12000004-operating) | operating file failed |
| [12000005](../../errorcode-universal.md#12000005-IPC) | IPC communication failed |
| [12000006](../../errorcode-universal.md#12000006-error) | error occurred in crypto engine |
| [12000011](../../errorcode-universal.md#12000011-queried) | queried entity does not exist |
| [12000012](../../errorcode-universal.md#12000012-Device) | Device environment or input parameter abnormal |
| [12000014](../../errorcode-universal.md#12000014-memory) | memory is insufficient |
| [12000018](../../errorcode-universal.md#12000018-the) | the group id specified by the access group tag is invalid&lt;br&gt;**适用版本：** 23+ |
| [12000026](../../errorcode-universal.md#12000026-the) | the secure element is not available&lt;br&gt;**适用版本：** 26.0.0+ |

**示例：**

```TypeScript
import { huks } from '@kit.UniversalKeystoreKit';

/* 此处options选择emptyOptions来传空 */
let keyAlias = 'keyAlias';
let emptyOptions: huks.HuksOptions = {
  properties: []
};

huks.getKeyItemProperties(keyAlias, emptyOptions, (error, data) => {
  if (error) {
    console.error(`callback: getKeyItemProperties failed`);
  } else {
    console.info(`callback: getKeyItemProperties success, data = ${JSON.stringify(data)}`);
  }
});

```


## getKeyItemProperties

```TypeScript
function getKeyItemProperties(keyAlias: string, options: HuksOptions): Promise<HuksReturnResult>
```

��ȡ��Կ���ԡ�ʹ��Promise�첽�ص���

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Security.Huks.Extension

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| keyAlias | string | 是 | ��Կ������Ӧ��������Կ����ʱʹ�õı�����ͬ�� |
| options | HuksOptions | 是 | �ն��󣨴˴����ռ��ɣ��� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;HuksReturnResult&gt; | Promise���󣬷��ص��ýӿڵĽ���������óɹ�ʱ��HuksReturnResult��properties��ԱΪ��ȡ����Կ������Ϣ�� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes:<br/>1. Mandatory parameters are left unspecified.<br/>2. Incorrect parameter types.<br/>3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-api) | api is not supported |
| [12000001](../../errorcode-universal.md#12000001-algorithm) | algorithm mode is not supported |
| [12000002](../../errorcode-universal.md#12000002-algorithm) | algorithm param is missing&lt;br&gt;**适用版本：** 9 - 11 |
| [12000003](../../errorcode-universal.md#12000003-algorithm) | algorithm param is invalid&lt;br&gt;**适用版本：** 9 - 11 |
| [12000004](../../errorcode-universal.md#12000004-operating) | operating file failed |
| [12000005](../../errorcode-universal.md#12000005-IPC) | IPC communication failed |
| [12000006](../../errorcode-universal.md#12000006-error) | error occurred in crypto engine |
| [12000011](../../errorcode-universal.md#12000011-queried) | queried entity does not exist |
| [12000012](../../errorcode-universal.md#12000012-Device) | Device environment or input parameter abnormal |
| [12000014](../../errorcode-universal.md#12000014-memory) | memory is insufficient |
| [12000018](../../errorcode-universal.md#12000018-the) | the group id specified by the access group tag is invalid&lt;br&gt;**适用版本：** 23+ |
| [12000026](../../errorcode-universal.md#12000026-the) | the secure element is not available&lt;br&gt;**适用版本：** 26.0.0+ |

**示例：**

```TypeScript
import { huks } from '@kit.UniversalKeystoreKit';

/* 此处options选择emptyOptions来传空 */
let keyAlias = 'keyAlias';
let emptyOptions: huks.HuksOptions = {
  properties: []
};

huks.getKeyItemProperties(keyAlias, emptyOptions)
  .then((data) => {
    console.info(`promise: getKeyItemProperties success, data = ${JSON.stringify(data)}`);
  });

```

