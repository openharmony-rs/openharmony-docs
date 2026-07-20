# setCurrentFunctions（系统接口）

## 导入模块

```TypeScript
import { usb } from '@kit.BasicServicesKit';
```

<a id="setcurrentfunctions"></a>
## setCurrentFunctions

```TypeScript
function setCurrentFunctions(funcs: FunctionType): Promise<boolean>
```

在设备模式下，设置当前的USB功能列表。

**起始版本：** 9

**废弃版本：** 9

**替代接口：** [setCurrentFunctions](arkts-basicservices-usbmanager-setcurrentfunctions-f-sys.md#setcurrentfunctions-1)

<!--Device-usb-function setCurrentFunctions(funcs: FunctionType): Promise<boolean>--><!--Device-usb-function setCurrentFunctions(funcs: FunctionType): Promise<boolean>-End-->

**系统能力：** SystemCapability.USB.USBManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| funcs | [FunctionType](arkts-basicservices-usb-functiontype-e-sys.md) | 是 | 功能列表对应的数字掩码。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;boolean&gt; | Promise对象，返回设置成功与否的结果。true表示设置成功，false表示设置失败。 |

**示例：**

```TypeScript
let funcs : number = usb.FunctionType.HDC;
usb.setCurrentFunctions(funcs).then(() => {
    console.info('usb setCurrentFunctions successfully.');
}).catch((err : BusinessError) => {
    console.error('usb setCurrentFunctions failed: ' + err.code + ' message: ' + err.message);
});

```

