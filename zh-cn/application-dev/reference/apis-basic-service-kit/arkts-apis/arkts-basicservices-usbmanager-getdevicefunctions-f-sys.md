# getDeviceFunctions（系统接口）

## getDeviceFunctions

```TypeScript
function getDeviceFunctions(): FunctionType
```

���豸ģʽ�£���ȡ��ǰ��USB�����б�������������롣������ģʽ�ر�ʱ�����û���豸���룬�ӿڿ��ܷ���`undefined`��ע����Ҫ�Խӿڷ���ֵ���пմ�����

**起始版本：** 12

**需要权限：** ohos.permission.MANAGE_USB_CONFIG

**系统能力：** SystemCapability.USB.USBManager

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| FunctionType | ��ǰ��USB�����б�������������롣 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-Permission) | Permission verification failed. The application does not have the permission required to<br/>call the API.&lt;br&gt;**适用版本：** 18+ |
| [202](../../errorcode-universal.md#202-Permission) | Permission denied. Normal application do not have permission to use system api. |
| [801](../../errorcode-universal.md#801-Capability) | Capability not supported.&lt;br&gt;**适用版本：** 18+ |

