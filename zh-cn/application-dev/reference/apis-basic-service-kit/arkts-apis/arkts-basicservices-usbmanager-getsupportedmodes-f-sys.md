# getSupportedModes（系统接口）

## getSupportedModes

```TypeScript
function getSupportedModes(portId: number): PortModeType
```

��ȡָ���Ķ˿�֧�ֵ�ģʽ�б���������롣

**起始版本：** 9

**废弃版本：** 12

**替代接口：** getPortSupportModes(portId:

**系统能力：** SystemCapability.USB.USBManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| portId | number | 是 | �˿ںš� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| PortModeType | ֧�ֵ�ģʽ�б���������롣 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes:<br/><br/>1.Mandatory parameters are left unspecified.<br/><br/>2.Incorrect parameter types. |

