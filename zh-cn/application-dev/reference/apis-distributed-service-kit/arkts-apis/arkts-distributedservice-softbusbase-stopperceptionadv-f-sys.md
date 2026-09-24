# stopPerceptionAdv（系统接口）

## 导入模块

```TypeScript
```

## stopPerceptionAdv

```TypeScript
function stopPerceptionAdv(type: PerceptionType): Promise<void>
```

停止当前所有者的感知广播。停止广播后，周边设备无法通过扫描发现当前设备。

**起始版本：** 26.0.1

**需要权限：** ohos.permission.ACCESS_SOFTBUS_SYS_HAP and ohos.permission.DISTRIBUTED_DATASYNC

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.SoftBus.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | [PerceptionType](arkts-distributedservice-softbusbase-perceptiontype-e-sys.md) | 是 | 感知业务类型。详细信息请参见[PerceptionType](arkts-distributedservice-softbusbase-perceptiontype-e-sys.md)。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 不返回任何值的Promise。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-api权限校验失败) | Permission denied, need to acquire ohos.permission.ACCESS_SOFTBUS_SYS_HAP and ohos.permission.DISTRIBUTED_DATASYNC. |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | Permission denied, A non-system application calls a system API. |
| [801](../../errorcode-universal.md#801-api功能在部分设备不支持) | Capability not supported. Failed to call the API due to limited device capabilities. |
| [2000001](../errorcode-conversation.md#2000001-内部错误) | Internal error. An unexpected system error occurred. |
| [2000003](../errorcode-softbusBase.md#2000003-临时错误) | Temporary error. The request failed due to a temporary error and can be retried. |
| [2006001](../errorcode-softbusBase.md#2006001-底层模块错误) | Underlying module error. The request failed due to an error in another underlying module and can be retried after a period of time. |
