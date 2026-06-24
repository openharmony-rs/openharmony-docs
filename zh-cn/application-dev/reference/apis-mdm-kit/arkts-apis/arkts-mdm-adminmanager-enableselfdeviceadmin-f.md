# enableSelfDeviceAdmin

## enableSelfDeviceAdmin

```TypeScript
function enableSelfDeviceAdmin(admin: Want, credential: string): Promise<void>
```

����ҵ�豸�У�MDMӦ��û��Ԥ�ü���ĳ����£�MDMӦ�ÿ���ͨ���ýӿ�ʵ���Լ���ýӿڽ�֧�ּ���MDMӦ����������֧�ּ�������MDMӦ�ã�֧�ֵļ������Ͱ��������豸����Ӧ�ú���ͨ�豸����Ӧ�á�

<!--RP1--><!--RP1End-->

**起始版本：** 26.0.0

**需要权限：** ohos.permission.ENTERPRISE_ACTIVATE_DEVICE_ADMIN

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| admin | Want | 是 | ��ҵ�豸������չ�����Want�б��������ҵ�豸������չ������abilityName������Ӧ�õ�bundleName�� |
| credential | string | 是 | ����ƾ֤�� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | the promise returned by the enableSelfDeviceAdmin. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [9200003](../../errorcode-universal.md#9200003-The) | The administrator ability component is invalid. |
| [9200004](../../errorcode-universal.md#9200004-Failed) | Failed to activate the administrator application of the device. |
| [9200012](../../errorcode-universal.md#9200012-Parameter) | Parameter verification failed. |
| [9200017](../../errorcode-universal.md#9200017-The) | The self-activation credential of the enterprise device administrator<br/>is invalid. |
| [9200018](../../errorcode-universal.md#9200018-This) | This device is not an enterprise device. |
| [201](../../errorcode-universal.md#201-Permission) | Permission verification failed.<br/>The application does not have the permission required to call the API. |
| [801](../../errorcode-universal.md#801-Capability) | Capability not supported.<br/>Failed to call the API due to limited device capabilities. |

