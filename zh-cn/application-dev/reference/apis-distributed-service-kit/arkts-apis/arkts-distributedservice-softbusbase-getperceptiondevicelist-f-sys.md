# getPerceptionDeviceList（系统接口）

## 导入模块

```TypeScript
```

## getPerceptionDeviceList

```TypeScript
function getPerceptionDeviceList(type: PerceptionType): Promise<PerceptionDeviceInfo[]>
```

获取感知扫描发现的设备列表。在调用该接口之前，请先调用[startPerceptionScan](arkts-distributedservice-softbusbase-startperceptionscan-f-sys.md)开始扫描。停止扫描后调用[stopPerceptionScan](arkts-distributedservice-softbusbase-stopperceptionscan-f-sys.md)，清除已发现设备列表。

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
| Promise&lt;[PerceptionDeviceInfo](arkts-distributedservice-softbusbase-perceptiondeviceinfo-i-sys.md)[]&gt; | Promise用于返回感知发现的设备列表扫描。如果未发现任何设备，或在调用之前，返回空数组[startPerceptionScan](arkts-distributedservice-softbusbase-startperceptionscan-f-sys.md)。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied, need to acquire ohos.permission.ACCESS_SOFTBUS_SYS_HAP and ohos.permission.DISTRIBUTED_DATASYNC. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission denied, A non-system application calls a system API. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. Failed to call the API due to limited device capabilities. |
| [2000001](../errorcode-conversation.md#2000001-内部错误) | Internal error. An unexpected system error occurred. |
| 2000002 | Caller error. The caller did not call the API in the specified order. |
| 2000003 | Temporary error. The request failed due to a temporary error and can be retried. |
| 2006001 | Underlying module error. The request failed due to an error in another underlying module and can be retried after a period of time. |
