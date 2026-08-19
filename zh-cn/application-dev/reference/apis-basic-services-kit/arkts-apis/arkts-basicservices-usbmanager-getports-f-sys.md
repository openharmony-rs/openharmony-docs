# getPorts（系统接口）

## 导入模块

```TypeScript
import { usbManager } from '@kit.BasicServicesKit';
import { serialManager } from '@kit.BasicServicesKit';
```

## getPorts

```TypeScript
function getPorts(): Array<USBPort>
```

获取所有物理USB端口描述信息。适用于需要枚举USB端口、进行端口管理、设备连接诊断、或查询端口配置信息的场景。开发者模式关闭时，如果没有设备接入，接口返回`undefined`，注意需要对接口返回值做判空处理。

**起始版本：** 9

**废弃版本：** 12

**替代接口：** [getPortList](arkts-basicservices-usbmanager-getportlist-f-sys.md)()

<!--Device-usbManager-function getPorts(): Array<USBPort>--><!--Device-usbManager-function getPorts(): Array<USBPort>-End-->

**系统能力：** SystemCapability.USB.USBManager

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;USBPort&gt; | USB端口描述信息列表。 |

