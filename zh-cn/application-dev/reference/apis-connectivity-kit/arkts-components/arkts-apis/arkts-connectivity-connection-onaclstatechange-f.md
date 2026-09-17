# onAclStateChange

## 导入模块

```TypeScript
import { connection } from '@kit.ConnectivityKit';
```

## onAclStateChange

```TypeScript
function onAclStateChange(callback: Callback<AclStateResult>): void
```

订阅蓝牙ACL链路连接状态变化事件。当触发蓝牙ACL链路连接或断开时，如订阅此事件，则会收到携带对应设备的地址与连接状态的回调函数。

**起始版本：** 26.0.0

**需要权限：** ohos.permission.ACCESS_BLUETOOTH or (ohos.permission.ACCESS_BLUETOOTH and ohos.permission.GET_BLUETOOTH_PEERS_MAC)

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[AclStateResult](arkts-connectivity-connection-aclstateresult-i.md)&gt; | 是 | 回调函数，返回蓝牙ACL链路连接状态 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. Failed to call the API when the short-range chip is not inserted on 2in1 device. |
| [2900099](../errorcode-bluetoothManager.md#2900099-操作失败) | Internal system error. For example, IPC error. Detailed error messages can be used to assist in locating the problem. |

**示例**

```TypeScript
function AclStateChangeEvent(aclStateResult: connection.AclStateResult) {
    console.info('acl state changed:'+ JSON.stringify(aclStateResult));
}
try {
    connection.onAclStateChange(AclStateChangeEvent);
} catch (err) {
    console.error(`errCode: ${err.code}, errMessage: ${err.message}`);
}
```
