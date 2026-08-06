# subscribe（系统接口）

## subscribe

```TypeScript
function subscribe(events: MechEventType[], callback: Callback<MechEvent>): void
```

订阅具身设备事件回调

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

<!--Device-mechanicManager-function subscribe(events: MechEventType[], callback: Callback<MechEvent>): void--><!--Device-mechanicManager-function subscribe(events: MechEventType[], callback: Callback<MechEvent>): void-End-->

**系统能力：** SystemCapability.Mechanic.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| events | \_\_\_MD\_LINK\_USD\_0\_\_\_[] | 是 | 订阅的事件列表。 |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;MechEvent&gt; | 是 | 事件回调函数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system application. |
| [33300001](../errorcode-mechanic.md#33300001-系统错误) | Service exception. |
| [33300002](../errorcode-mechanic.md#33300002-设备未连接) | Device not connected. |
| [33300003](../errorcode-mechanic.md#33300003-功能不支持) | Feature not supported. |

