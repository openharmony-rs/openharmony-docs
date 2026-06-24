# setPortRoles（系统接口）

## setPortRoles

```TypeScript
function setPortRoles(portId: number, powerRole: PowerRoleType, dataRole: DataRoleType): Promise<void>
```

����ָ���Ķ˿�֧�ֵĽ�ɫģʽ����������ɫ�����ݴ����ɫ��ʹ��Promise�첽�ص���

**起始版本：** 9

**废弃版本：** 12

**替代接口：** setPortRoleTypes(portId:

**系统能力：** SystemCapability.USB.USBManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| portId | number | 是 | �˿ںš� |
| powerRole | PowerRoleType | 是 | ���Ľ�ɫ�� |
| dataRole | DataRoleType | 是 | ���ݴ���Ľ�ɫ�� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise���� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes:<br/><br/>1.Mandatory parameters are left unspecified.<br/><br/>2.Incorrect parameter types. |

