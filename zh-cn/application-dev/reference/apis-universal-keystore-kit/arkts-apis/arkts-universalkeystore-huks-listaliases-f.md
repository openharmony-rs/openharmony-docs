# listAliases

## 导入模块

```TypeScript
import { huks } from '@kit.UniversalKeystoreKit';
```

<a id="listaliases"></a>
## listAliases

```TypeScript
function listAliases(options: HuksOptions): Promise<HuksListAliasesReturnResult>
```

查询密钥别名集接口。使用Promise异步回调。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-huks-function listAliases(options: HuksOptions): Promise<HuksListAliasesReturnResult>--><!--Device-huks-function listAliases(options: HuksOptions): Promise<HuksListAliasesReturnResult>-End-->

**系统能力：** SystemCapability.Security.Huks.Extension

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [HuksOptions](arkts-universalkeystore-huks-huksoptions-i.md) | 是 | listAliases操作的参数集合。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;HuksListAliasesReturnResult&gt; | Promise对象，返回调用接口的结果。当调用成功时，HuksListAliasesReturnResult的成员keyAliases为获取的密钥别名集。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes:1. Mandatory parameters are left unspecified.2. Incorrect parameter types.3. Parameter verification failed. |
| [12000004](../errorcode-huks.md#12000004-文件错误) | operating file failed |
| [12000005](../errorcode-huks.md#12000005-进程通信错误) | IPC communication failed |
| [12000012](../errorcode-huks.md#12000012-外部错误) | Device environment or input parameter abnormal |
| [12000014](../errorcode-huks.md#12000014-内存不足) | memory is insufficient |
| [12000018](../errorcode-huks.md#12000018-输入参数非法) | the group id specified by the access group tag is invalid<br>**适用版本：** 23+ |

**示例：**

```TypeScript
/* 以查询DE类密钥的别名集为例 */
import { huks } from '@kit.UniversalKeystoreKit';

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

