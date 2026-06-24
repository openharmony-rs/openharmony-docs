# wrapKeyItem

## wrapKeyItem

```TypeScript
function wrapKeyItem(keyAlias: string, params: HuksOptions): Promise<HuksReturnResult>
```

���ܵ�����Կ��ʹ��Promise�첽�ص���

<!--Del-->�ù����ݲ�֧�֡�<!--DelEnd-->

**起始版本：** 20

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Security.Huks.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| keyAlias | string | 是 | ��Կ������Ӧ��������Կ����ʱʹ�õı�����ͬ�� |
| params | HuksOptions | 是 | ����ָ��������Կʱ�ļ������͡� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;HuksReturnResult&gt; | Promise���󣬷��ص��ýӿڵĽ���������óɹ�ʱ��HuksReturnResult��outData��ԱΪ��������Կ���ġ� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-api) | api is not supported |
| [12000004](../../errorcode-universal.md#12000004-operating) | operating file failed |
| [12000005](../../errorcode-universal.md#12000005-IPC) | IPC communication failed |
| [12000011](../../errorcode-universal.md#12000011-queried) | queried entity does not exist |
| [12000012](../../errorcode-universal.md#12000012-Device) | Device environment or input parameter abnormal |
| [12000014](../../errorcode-universal.md#12000014-memory) | memory is insufficient |
| [12000018](../../errorcode-universal.md#12000018-the) | the input parameter is invalid |
| [12000026](../../errorcode-universal.md#12000026-the) | the secure element is not available&lt;br&gt;**适用版本：** 26.0.0+ |

