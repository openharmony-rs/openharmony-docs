# setPortRoles（系统接口）

## 导入模块

```TypeScript
import { usb } from '@kit.BasicServicesKit';
```

<a id="setportroles"></a>
## setPortRoles

```TypeScript
function setPortRoles(portId: number, powerRole: PowerRoleType, dataRole: DataRoleType): Promise<boolean>
```

设置指定的端口支持的角色模式，包含充电角色、数据传输角色。

**起始版本：** 9

**废弃版本：** 9

**替代接口：** [setPortRoles](arkts-basicservices-usbmanager-setportroles-f-sys.md#setportroles-1)

<!--Device-usb-function setPortRoles(portId: number, powerRole: PowerRoleType, dataRole: DataRoleType): Promise<boolean>--><!--Device-usb-function setPortRoles(portId: number, powerRole: PowerRoleType, dataRole: DataRoleType): Promise<boolean>-End-->

**系统能力：** SystemCapability.USB.USBManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| portId | number | 是 | 端口号。 |
| powerRole | [PowerRoleType](arkts-basicservices-usbmanager-powerroletype-e-sys.md) | 是 | 充电的角色。 |
| dataRole | [DataRoleType](arkts-basicservices-usbmanager-dataroletype-e-sys.md) | 是 | 数据传输的角色。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;boolean&gt; | Promise对象，返回设置成功与否的结果。true表示设置成功，false表示设置失败。 |

**示例：**

```TypeScript
let portId = 1;
usb.setPortRoles(portId, usb.PowerRoleType.SOURCE, usb.DataRoleType.HOST).then(() => {
    console.info('usb setPortRoles successfully.');
}).catch((err : BusinessError) => {
    console.error('usb setPortRoles failed: ' + err.code + ' message: ' + err.message);
});

```

