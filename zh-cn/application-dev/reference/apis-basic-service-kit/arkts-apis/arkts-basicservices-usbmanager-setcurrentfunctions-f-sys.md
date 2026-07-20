# setCurrentFunctions（系统接口）

## 导入模块

```TypeScript
import { usbManager } from '@kit.BasicServicesKit';
```

<a id="setcurrentfunctions"></a>
## setCurrentFunctions

```TypeScript
function setCurrentFunctions(funcs: FunctionType): Promise<void>
```

在设备模式下，设置当前的USB功能列表。使用Promise异步回调。

**起始版本：** 9

**废弃版本：** 12

**替代接口：** [setDeviceFunctions(funcs:](arkts-basicservices-usbmanager-setdevicefunctions-f-sys.md#setdevicefunctions-1)

<!--Device-usbManager-function setCurrentFunctions(funcs: FunctionType): Promise<void>--><!--Device-usbManager-function setCurrentFunctions(funcs: FunctionType): Promise<void>-End-->

**系统能力：** SystemCapability.USB.USBManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| funcs | [FunctionType](arkts-basicservices-usb-functiontype-e-sys.md) | 是 | 功能列表对应的数字掩码。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:* <br>1.Mandatory parameters are left unspecified.* <br>2.Incorrect parameter types. |
| [14400002](../../apis-basic-services-kit/errorcode-usb.md#14400002-hdc功能被禁用) | Permission denied. The HDC is disabled by the system. |

