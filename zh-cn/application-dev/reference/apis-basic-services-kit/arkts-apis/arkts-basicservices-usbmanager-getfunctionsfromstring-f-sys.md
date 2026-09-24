# getFunctionsFromString（系统接口）

## 导入模块

```TypeScript
import { usbManager } from '@kit.BasicServicesKit';
```

## getFunctionsFromString

```TypeScript
function getFunctionsFromString(funcs: string): number
```

在设备模式下，将字符串形式的USB功能列表转换为数字掩码。适用于需要将配置文件或用户输入的字符串形式USB功能列表转换为系统内部使用的数字掩码的场景，以便后续调用setDeviceFunctions等接口设置USB功能。

**起始版本：** 12

**需要权限：** ohos.permission.MANAGE_USB_CONFIG

**系统能力：** SystemCapability.USB.USBManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| funcs | string | 是 | 字符串形式的功能列表。可用值包括：'none'、'acm'、'ecm'、'hdc'、'mtp'、'ptp'、'rndis'、'midi'、'audio_source'、'ncm'，可通过英文逗号分隔多个功能。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 转换后的功能列表对应的数字掩码。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-api权限校验失败) | Permission verification failed. The application does not have the permission required to call the API.<br>**适用版本：** 18+ |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | Permission denied. Normal application do not have permission to use system api. |
| [401](../../errorcode-universal.md#401-函数参数数量或参数类型不匹配) | Parameter error. Possible causes:<br>1.Mandatory parameters are left unspecified.  <br>2.Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-api功能在部分设备不支持) | Capability not supported.<br>**适用版本：** 18+ |
