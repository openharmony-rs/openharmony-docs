# setDeviceFunctions（系统接口）

## 导入模块

```TypeScript
import { usbManager } from '@kit.BasicServicesKit';
```

## setDeviceFunctions

```TypeScript
function setDeviceFunctions(funcs: FunctionType): Promise<void>
```

在设备模式下，设置当前的USB功能列表。使用Promise异步回调。调用成功后，设备的USB功能将切换为指定的功能列表。部分USB功能可能不被当前设备支持，设置前建议先查询设备支持的功能列表。开发者模式关闭时，如果没有设备接入，操 作可能会失败，调用失败时抛出异常。功能切换会触发USB设备的重新枚举，已连接的主机可能需要重新识别设备。多个功能可通过位运算组合设置，但某些功能可能互斥或存在优先级，具体约束请参考设备规格。功能设置失败可能由于设备不支持、权限不足 或系统限制，详见错误码说明。

**起始版本：** 12

**需要权限：** ohos.permission.MANAGE_USB_CONFIG

**系统能力：** SystemCapability.USB.USBManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| funcs | FunctionType | 是 | 功能列表对应的数字掩码，可通过位运算组合多个功能。部分功能可能不被当前设备支持，具体参见 [FunctionType](arkts-basicservices-usbmanager-functiontype-e-sys.md)。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;void & gt; | Promise对象。调用成功时无返回值，调用失败时抛出异常。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. The application does not have the permission required to call the API.<br>**适用版本：** 18+ |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission denied. Normal application do not have permission to use system api. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes:  1.Mandatory parameters are left unspecified.  2.Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported.<br>**适用版本：** 18+ |
| [14400002](../errorcode-usb.md#14400002-hdc功能被禁用) | Permission denied. The HDC is disabled by the system. |
| [14400006](../errorcode-usb.md#14400006-不支持的usb设备侧功能) | Unsupported operation. The function is not supported. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
// 设置USB功能类型为HDC
let funcs: usbManager.FunctionType = usbManager.FunctionType.HDC;
// 异步设置设备功能
usbManager.setDeviceFunctions(funcs).then(() => {
    console.info('usb setDeviceFunctions successfully.');
}).catch((err : BusinessError) => {
    console.error(`usb setDeviceFunctions failed. Code: ${err.code}, message: ${err.message}`);
});
```
