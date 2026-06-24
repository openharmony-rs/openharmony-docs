# encapsulate

## encapsulate

```TypeScript
function encapsulate(keyAlias: string, params: HuksParam[],
      sharedKeyAlias?: string, sharedKeyParams?: HuksParam[]): Promise<HuksReturnResult>
```

�����Ӽ�����Կ��װ������֧��HUKS��Կ����
����Ӧ�ó��������������Ӧ�ó���ѡ�������Կ��
�Գ���ԿЯ����HuksReturnResult��outData�ֶ��С�

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Security.Huks.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| keyAlias | string | 是 | �����Ӽ����㷨����Կ���� |
| params | HuksParam[] | 是 | ��ʾ��װ���� |
| sharedKeyAlias | string | 否 | ��װ��Կ����Կ������<br/>���ʹ��HUKS������Կ�����������ָ���ò�����<br/>���Ӧ�ó����Լ�������Կ������Դ˲��� |
| sharedKeyParams | HuksParam[] | 否 | ��ʾ��װ����Կ�����ԡ�<br/>���ʹ��HUKS������Կ�����������ָ���ò�����<br/>���Ӧ�ó����Լ�������Կ������Դ˲��� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;HuksReturnResult&gt; | �������ص�promise�� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-API) | API is not supported. |
| [12000001](../../errorcode-universal.md#12000001-Algorithm) | Algorithm mode is not supported |
| [12000002](../../errorcode-universal.md#12000002-Algorithm) | Algorithm parameters are missing, please check the algorithm parameters. |
| [12000003](../../errorcode-universal.md#12000003-The) | The algorithm parameters are invalid, please check the algorithm parameters. |
| [12000004](../../errorcode-universal.md#12000004-File) | File operation failed. |
| [12000005](../../errorcode-universal.md#12000005-IPC) | IPC communication failed. |
| [12000006](../../errorcode-universal.md#12000006-The) | The algorithm engine reported an error, please check the input parameters. |
| [12000011](../../errorcode-universal.md#12000011-The) | The queried key does not exist, please check the key-related parameters. |
| [12000012](../../errorcode-universal.md#12000012-Device) | Device environment or input parameters are abnormal. |
| [12000013](../../errorcode-universal.md#12000013-Queried) | Queried credential does not exist |
| [12000014](../../errorcode-universal.md#12000014-Memory) | Memory is insufficient. |
| [12000015](../../errorcode-universal.md#12000015-Failed) | Failed to obtain the security information via UserIAM. |
| [12000016](../../errorcode-universal.md#12000016-The) | The screen lock password is not set. |
| [12000017](../../errorcode-universal.md#12000017-The) | The key with the same alias already exists. |
| [12000018](../../errorcode-universal.md#12000018-The) | The input parameter is invalid. |

