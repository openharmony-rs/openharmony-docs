# getStringFromFunctions（系统接口）

## 导入模块

```TypeScript
import { usbManager } from '@kit.BasicServicesKit';
import { serialManager } from '@kit.BasicServicesKit';
```

## getStringFromFunctions

```TypeScript
function getStringFromFunctions(funcs: FunctionType): string
```

在设备模式下，将数字掩码形式的USB功能列表转换为字符串。适用于需要将当前USB功能状态以字符串形式显示或保存的场景，如在日志中记录当前功能配置、在UI界面展示当前功能等。

**起始版本：** 12

**需要权限：** ohos.permission.MANAGE_USB_CONFIG

<!--Device-usbManager-function getStringFromFunctions(funcs: FunctionType): string--><!--Device-usbManager-function getStringFromFunctions(funcs: FunctionType): string-End-->

**系统能力：** SystemCapability.USB.USBManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| funcs | FunctionType | 是 | 功能列表对应的数字掩码，可通过位运算组合多个功能。部分功能值当前暂不支持，具体参见 [FunctionType](arkts-basicservices-usbmanager-functiontype-e-sys.md)。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 转换后的字符串形式的功能列表。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes:  <br>1.Mandatory parameters are left unspecified.  <br>2.Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported.<br>**适用版本：** 18+ |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. The application does not have the permission required to call the API.<br>**适用版本：** 18+ |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission denied. Normal application do not have permission to use system api. |


## getStringFromFunctions

```TypeScript
function getStringFromFunctions(funcs: int): string
```

Converts the numeric mask combination of a given USB function list to a string descriptor.

**起始版本：** 23

**需要权限：** ohos.permission.MANAGE_USB_CONFIG

<!--Device-usbManager-function getStringFromFunctions(funcs: int): string--><!--Device-usbManager-function getStringFromFunctions(funcs: int): string-End-->

**系统能力：** SystemCapability.USB.USBManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| funcs | int | 是 | numeric mask combination of the function list. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | descriptor of the supported function list. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [201](../../errorcode-universal.md#201-权限校验失败) |  |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission denied. Normal application do not have permission to use system api. |

