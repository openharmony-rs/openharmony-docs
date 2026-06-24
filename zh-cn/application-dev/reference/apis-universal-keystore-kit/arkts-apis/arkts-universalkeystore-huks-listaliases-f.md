# listAliases

## listAliases

```TypeScript
function listAliases(options: HuksOptions): Promise<HuksListAliasesReturnResult>
```

��ѯ��Կ�������ӿڡ�ʹ��Promise�첽�ص���

**起始版本：** 12

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Security.Huks.Extension

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | HuksOptions | 是 | listAliases�����Ĳ������ϡ� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;HuksListAliasesReturnResult&gt; | Promise���󣬷��ص��ýӿڵĽ���������óɹ�ʱ��HuksListAliasesReturnResult�ĳ�Ա<br/>keyAliasesΪ��ȡ����Կ�������� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes:<br/>1. Mandatory parameters are left unspecified.<br/>2. Incorrect parameter types.<br/>3. Parameter verification failed. |
| [12000004](../../errorcode-universal.md#12000004-operating) | operating file failed |
| [12000005](../../errorcode-universal.md#12000005-IPC) | IPC communication failed |
| [12000012](../../errorcode-universal.md#12000012-Device) | Device environment or input parameter abnormal |
| [12000014](../../errorcode-universal.md#12000014-memory) | memory is insufficient |
| [12000018](../../errorcode-universal.md#12000018-the) | the group id specified by the access group tag is invalid&lt;br&gt;**适用版本：** 23+ |

**示例：**

```TypeScript
import { huks } from '@kit.UniversalKeystoreKit'

async function testListAliases() {
  let queryProperties: Array<huks.HuksParam> = [
    {
      tag: huks.HuksTag.HUKS_TAG_AUTH_STORAGE_LEVEL,
      value: huks.HuksAuthStorageLevel.HUKS_AUTH_STORAGE_LEVEL_DE
    }
  ];
  let queryOptions: huks.HuksOptions = {
    properties: queryProperties
  };

  try{
    await huks.listAliases(queryOptions)
      .then((data) => {
      console.info(`promise: listAliases success, data: ` + JSON.stringify(data));
    });
  } catch (error) {
    console.error(`promise: listAliases failed, errCode : ${error.code}, errMsg : ${error.message}`);
  }
}

```

