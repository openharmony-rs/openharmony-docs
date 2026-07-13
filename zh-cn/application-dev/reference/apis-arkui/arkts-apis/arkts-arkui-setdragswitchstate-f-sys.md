# setDragSwitchState（系统接口）

## setDragSwitchState

```TypeScript
function setDragSwitchState(enabled: boolean): void
```

控制统一拖拽功能总开关。

**起始版本：** 18

**系统能力：** SystemCapability.Msdp.DeviceStatus.Drag

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enabled | boolean | 是 | 设置开关状态。<br>false：关闭，true：开启。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |

