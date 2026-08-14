# offStateChange

## offStateChange

```TypeScript
function offStateChange(callback?: Callback<NearlinkState>): void
```

取消订阅状态变更事件。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-manager-function offStateChange(callback?: Callback<NearlinkState>): void--><!--Device-manager-function offStateChange(callback?: Callback<NearlinkState>): void-End-->

**系统能力：** SystemCapability.Communication.NearLink.Base

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[NearlinkState](arkts-connectivity-manager-nearlinkstate-e.md)&gt; | 否 | 用于监听状态改变事件的回调 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported because the chip does not support it. |
| [36100099](../errorcode-nearlink-service.md#36100099-操作失败) | Operation failed. |

