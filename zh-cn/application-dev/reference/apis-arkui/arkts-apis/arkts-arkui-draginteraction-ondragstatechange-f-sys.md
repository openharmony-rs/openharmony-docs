# onDragStateChange（系统接口）

## onDragStateChange

```TypeScript
function onDragStateChange(callback: Callback<DragState>): void
```

Listens for dragging state change events.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-dragInteraction-function onDragStateChange(callback: Callback<DragState>): void--><!--Device-dragInteraction-function onDragStateChange(callback: Callback<DragState>): void-End-->

**系统能力：** SystemCapability.Msdp.DeviceStatus.Drag

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;DragState&gt; | 是 | Indicates the callback to receive the changed dragging state. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |

