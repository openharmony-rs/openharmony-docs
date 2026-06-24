# decapsulate

## decapsulate

```TypeScript
function decapsulate(keyAlias: string, params: HuksParam[], encapData: Uint8Array,
      sharedKeyAlias?: string, sharedKeyParams?:  HuksParam[]): Promise<HuksReturnResult>
```

Post-Quantum Cryptography��Կ���װ������֧��HUKS��Կ����
����Ӧ�ó��������������Ӧ�ó���ѡ�������Կ��
�Գ���Կ������HuksReturnResult��outData�ֶ��С�

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Security.Huks.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| keyAlias | string | 是 | �����Ӽ����㷨����Կ���ơ� |
| params | HuksParam[] | 是 | ��ʾ���װ���ԡ� |
| encapData | Uint8Array | 是 | ��ʾ��װ��Ĺ�����Կ�� |
| sharedKeyAlias | string | 否 | ��ʾ���װ��Կ����Կ������<br/>���ʹ��HUKS������Կ�����������ָ���ò�����<br/>���Ӧ�ó����Լ�������Կ������Դ˲����� |
| sharedKeyParams | HuksParam[] | 否 | ��ʾ���װ���key�����ԡ�<br/>���ʹ��HUKS������Կ�����������ָ���ò�����<br/>���Ӧ�ó����Լ�������Կ������Դ˲����� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;HuksReturnResult&gt; | ����ֵ |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-API) | API is not supported. |
| [12000001](../../errorcode-universal.md#12000001-Algorithm) | Algorithm mode is not supported |
| [12000002](../../errorcode-universal.md#12000002-The) | The algorithm parameter is missing. Check the algorithm parameter. |
| [12000003](../../errorcode-universal.md#12000003-The) | The algorithm parameter is invalid. Check the algorithm parameter. |
| [12000004](../../errorcode-universal.md#12000004-The) | The file operation failed. |
| [12000005](../../errorcode-universal.md#12000005-IPC) | IPC communication failed. |
| [12000006](../../errorcode-universal.md#12000006-The) | The algorithm engine reports an error. Check the input parameters. |
| [12000011](../../errorcode-universal.md#12000011-The) | The queried key does not exist. Check the key-related parameters. |
| [12000012](../../errorcode-universal.md#12000012-The) | The device environment or input parameter is abnormal. |
| [12000013](../../errorcode-universal.md#12000013-Queried) | Queried credential does not exist |
| [12000014](../../errorcode-universal.md#12000014-Insufficient) | Insufficient memory. |
| [12000015](../../errorcode-universal.md#12000015-Failed) | Failed to obtain the security information using UserIAM. |
| [12000016](../../errorcode-universal.md#12000016-The) | The lock screen password is not set. |
| [12000017](../../errorcode-universal.md#12000017-A) | A key with the same alias already exists. |
| [12000018](../../errorcode-universal.md#12000018-Invalid) | Invalid input parameter. |

