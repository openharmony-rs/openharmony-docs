# addDeviceAccessRight（系统接口）

## addDeviceAccessRight

```TypeScript
function addDeviceAccessRight(tokenId: string, deviceName: string): boolean
```

���������������豸��Ȩ�ޡ�ϵͳӦ��Ĭ��ӵ�з����豸Ȩ�ޣ����ô˽ӿڲ������Ӱ�졣
[usbManager.requestRight]{(@link usbManager.requestRight)}�ᴥ�����������û���Ȩ��addDeviceAccessRight���ᴥ�����򣬶���ֱ�����������������豸��Ȩ�ޡ�

**起始版本：** 12

**需要权限：** ohos.permission.MANAGE_USB_CONFIG

**系统能力：** SystemCapability.USB.USBManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| tokenId | string | 是 | ������tokenId�� |
| deviceName | string | 是 | �豸���ơ� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | ����Ȩ�����ӽ��������true��ʾȨ�����ӳɹ�������false���ʾȨ������ʧ�ܡ� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-Permission) | Permission verification failed. The application does not have the permission required to<br/>call the API.&lt;br&gt;**适用版本：** 18+ |
| [202](../../errorcode-universal.md#202-Permission) | Permission denied. Normal application do not have permission to use system api. |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes:<br/><br/>1.Mandatory parameters are left unspecified.<br/><br/>2.Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-Capability) | Capability not supported.&lt;br&gt;**适用版本：** 18+ |

