# hasKeyItem

## hasKeyItem

```TypeScript
function hasKeyItem(keyAlias: string, options: HuksOptions, callback: AsyncCallback<boolean>): void
```

�ж���Կ�Ƿ���ڡ�ʹ��callback�첽�ص���

����Կ�����ڣ���ͨ��callback����false��

**起始版本：** 11

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Security.Huks.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| keyAlias | string | 是 | ������ҵ���Կ�ı����� |
| options | HuksOptions | 是 | ���ڲ�ѯʱָ����Կ������TAG����ʹ��[HuksAuthStorageLevel](arkts-universalkeystore-huks-huksauthstoragelevel-e.md#HuksAuthStorageLevel)ָ�����ѯ��Կ��<br/>��ȫ����<br/>�ɴ��գ���API version �� 12ʱ������Ĭ��ΪCE����API version �� 12ʱ������Ĭ��ΪDE�� |
| callback | AsyncCallback&lt;boolean&gt; | 是 | �ص�����������Կ���ڣ�dataΪtrue������Կ�����ڣ�dataΪfalse�� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes:<br/>1. Mandatory parameters are left unspecified.<br/>2. Incorrect parameter types.<br/>3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-api) | api is not supported |
| [12000004](../../errorcode-universal.md#12000004-operating) | operating file failed |
| [12000005](../../errorcode-universal.md#12000005-IPC) | IPC communication failed |
| [12000006](../../errorcode-universal.md#12000006-error) | error occurred in crypto engine |
| [12000012](../../errorcode-universal.md#12000012-Device) | Device environment or input parameter abnormal |
| [12000014](../../errorcode-universal.md#12000014-memory) | memory is insufficient |
| [12000018](../../errorcode-universal.md#12000018-the) | the group id specified by the access group tag is invalid&lt;br&gt;**适用版本：** 23+ |

**示例：**

```TypeScript
import { huks } from '@kit.UniversalKeystoreKit';

/* 此处options选择emptyOptions来传空 */
let keyAlias = 'keyAlias';
let emptyOptions: huks.HuksOptions = {
  properties: []
};

huks.hasKeyItem(keyAlias, emptyOptions, (error, data) => {
  if (error) {
    console.error(`callback: hasKeyItem failed`);
  } else {
    if (data) {
      console.info(`keyAlias:${keyAlias} is existed!`);
    } else {
      console.error(`find key failed`);
    }
  }
});

```


## hasKeyItem

```TypeScript
function hasKeyItem(keyAlias: string, options: HuksOptions): Promise<boolean>
```

�ж���Կ�Ƿ���ڡ�ʹ��Promise�첽�ص���

����Կ�����ڣ���ͨ��Promise����false��

**起始版本：** 11

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Security.Huks.Extension

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| keyAlias | string | 是 | ������ҵ���Կ�ı����� |
| options | HuksOptions | 是 | ���ڲ�ѯʱָ����Կ������TAG����ʹ��[HuksAuthStorageLevel](arkts-universalkeystore-huks-huksauthstoragelevel-e.md#HuksAuthStorageLevel)ָ�����ѯ��Կ��<br/>��ȫ����<br/>�ɴ��գ���API version �� 12ʱ������Ĭ��ΪCE����API version �� 12ʱ������Ĭ��ΪDE�� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;boolean&gt; | Promise��������Կ���ڣ�����ֵΪtrue������Կ�����ڣ�����ֵΪfalse�� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes:<br/>1. Mandatory parameters are left unspecified.<br/>2. Incorrect parameter types.<br/>3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-api) | api is not supported |
| [12000004](../../errorcode-universal.md#12000004-operating) | operating file failed |
| [12000005](../../errorcode-universal.md#12000005-IPC) | IPC communication failed |
| [12000006](../../errorcode-universal.md#12000006-error) | error occurred in crypto engine |
| [12000012](../../errorcode-universal.md#12000012-Device) | Device environment or input parameter abnormal |
| [12000014](../../errorcode-universal.md#12000014-memory) | memory is insufficient |
| [12000018](../../errorcode-universal.md#12000018-the) | the group id specified by the access group tag is invalid&lt;br&gt;**适用版本：** 23+ |

**示例：**

```TypeScript
import { huks } from '@kit.UniversalKeystoreKit';

/* 此处options选择emptyOptions来传空 */
let keyAlias = 'keyAlias';
let emptyOptions: huks.HuksOptions = {
  properties: []
};

huks.hasKeyItem(keyAlias, emptyOptions).then((data) => {
  if (data) {
    console.info(`keyAlias:${keyAlias} is existed!`);
  } else {
    console.info(`find key failed!`);
  }
});

```

