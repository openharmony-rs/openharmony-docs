# exportKeyItem

## exportKeyItem

```TypeScript
function exportKeyItem(keyAlias: string, options: HuksOptions, callback: AsyncCallback<HuksReturnResult>): void
```

������Կ��ʹ��callback�첽�ص���

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Security.Huks.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| keyAlias | string | 是 | ��Կ������Ӧ��������Կ����ʱʹ�õı�����ͬ�� |
| options | HuksOptions | 是 | ���ڵ�����Կʱָ����Կ�����ԣ���ʹ��[HuksAuthStorageLevel](arkts-universalkeystore-huks-huksauthstoragelevel-e.md#HuksAuthStorageLevel)ָ���赼����Կ�İ�<br/>ȫ����<br/>�ɴ��գ���API version �� 12ʱ������Ĭ��ΪCE����API version �� 12ʱ������Ĭ��ΪDE�� |
| callback | AsyncCallback&lt;HuksReturnResult&gt; | 是 | �ص���������������Կ�ɹ�ʱ��errΪundefined��dataΪ��ȡ����HuksReturnResult������Ϊ�������<br/>��HuksReturnResult�е�outData���ش�HUKS�е����Ĺ�Կ�� |

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
| [12000020](../../errorcode-universal.md#12000020-the) | the provider operation failed&lt;br&gt;**适用版本：** 26.0.0+ |
| [12000024](../../errorcode-universal.md#12000024-the) | the provider or UKey is busy&lt;br&gt;**适用版本：** 26.0.0+ |
| [12000026](../../errorcode-universal.md#12000026-the) | the secure element is not available&lt;br&gt;**适用版本：** 26.0.0+ |

**示例：**

```TypeScript
import { huks } from '@kit.UniversalKeystoreKit';

/* 此处options选择emptyOptions来传空 */
let keyAlias = 'keyAlias';
let emptyOptions: huks.HuksOptions = {
  properties: []
};

huks.exportKeyItem(keyAlias, emptyOptions, (error, data) => {
  if (error) {
    console.error(`callback: exportKeyItem failed`);
  } else {
    console.info(`callback: exportKeyItem success, data = ${JSON.stringify(data)}`);
  }
});

```


## exportKeyItem

```TypeScript
function exportKeyItem(keyAlias: string, options: HuksOptions): Promise<HuksReturnResult>
```

������Կ��ʹ��Promise�첽�ص���

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
| Promise&lt;HuksReturnResult&gt; | Promise���󣬷��ص��ýӿڵĽ���������óɹ�ʱ��HuksReturnResult��outData��ԱΪ����Կ�е����Ĺ�Կ�� |

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
| [12000020](../../errorcode-universal.md#12000020-the) | the provider operation failed&lt;br&gt;**适用版本：** 26.0.0+ |
| [12000024](../../errorcode-universal.md#12000024-the) | the provider or UKey is busy&lt;br&gt;**适用版本：** 26.0.0+ |
| [12000026](../../errorcode-universal.md#12000026-the) | the secure element is not available&lt;br&gt;**适用版本：** 26.0.0+ |

**示例：**

```TypeScript
import { huks } from '@kit.UniversalKeystoreKit';

/* 此处options选择emptyOptions来传空 */
let keyAlias = 'keyAlias';
let emptyOptions: huks.HuksOptions = {
  properties: []
};

huks.exportKeyItem(keyAlias, emptyOptions)
  .then((data) => {
    console.info(`promise: exportKeyItem success, data = ${JSON.stringify(data)}`);
  });

```

