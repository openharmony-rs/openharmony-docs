# onDragStateChange（系统接口）

## 导入模块

```TypeScript
import { dragInteraction } from '@kit.ArkUI';
```

## onDragStateChange

```TypeScript
function onDragStateChange(callback: Callback<DragState>): void
```

Listens for dragging state change events.

**起始版本：** 23

<!--Device-dragInteraction-function onDragStateChange(callback: Callback<DragState>): void--><!--Device-dragInteraction-function onDragStateChange(callback: Callback<DragState>): void-End-->

**系统能力：** SystemCapability.Msdp.DeviceStatus.Drag

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[DragState](arkts-arkui-draginteraction-dragstate-e-sys.md)&gt; | 是 | Indicates the callback to receive the changed dragging state. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |

