# addPortAuthorization（系统接口）

## addPortAuthorization

```TypeScript
function addPortAuthorization(tokenId: string, deviceId: string): Promise<void>
```

����Ӧ�÷��ʴ��ڶ˿ڵ�Ȩ��
�����򴮿���Ȩ����ϵͳӦ�ÿ���

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.BusManager.Serial

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| tokenId | string | 是 | ����ȨӦ�õ�tokenId |
| deviceId | string | 是 | �����豸ID<br/><br/>���ڰ��ش��ڣ�ȡֵΪportName������USB���⴮�ڣ�ȡֵΪvid+pid+SNƴ�ӡ� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | - Promise�����޷��ؽ�� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-Permission) | Permission denied. Called by non-system application |
| [35700001](../../errorcode-universal.md#35700001-Service) | Service error. |
| [35700002](../../errorcode-universal.md#35700002-Invalid) | Invalid parameter. |
| [35700008](../../errorcode-universal.md#35700008-Permission) | Permission denied. |

