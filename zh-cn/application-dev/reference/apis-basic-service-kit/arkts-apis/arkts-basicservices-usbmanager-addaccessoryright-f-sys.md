# addAccessoryRight（系统接口）

## addAccessoryRight

```TypeScript
function addAccessoryRight(tokenId: number, accessory: USBAccessory): void
```

ΪӦ�ó������ӷ���USB��requestAccessoryRight��Ȩ�ޡ�
[usbManager.]{(@link usbManager.requestAccessoryRight)}�ᴥ�����������û���Ȩ��addAccessoryRight���ᴥ������������ֱ������Ӧ�ó�������豸��Ȩ�ޡ�

**起始版本：** 14

**需要权限：** ohos.permission.MANAGE_USB_CONFIG

**系统能力：** SystemCapability.USB.USBManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| tokenId | number | 是 | Ӧ�ó���tokenId�� |
| accessory | USBAccessory | 是 | USB����� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-The) | The permission check failed. |
| [202](../../errorcode-universal.md#202-Permission) | Permission denied. Normal application do not have permission to use system api. |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes:<br/><br/>1. Mandatory parameters are left unspecified.<br/><br/>2. Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-Capability) | Capability not supported.&lt;br&gt;**适用版本：** 18+ |
| [14400004](../../errorcode-universal.md#14400004-Service) | Service exception. Possible causes:<br/><br/>1. No accessory is plugged in. |
| [14400005](../../errorcode-universal.md#14400005-Database) | Database operation exception. |

