# onDeviceFound

## onDeviceFound

```TypeScript
function onDeviceFound(callback: Callback<ScanResults[]>): void
```

订阅NearLink扫描结果。

只有授予了ohos.permission.NEARLINK_ACCESS权限的应用程序才能访问此事件。
如果应用被赋予了ohos.permission.GET_NEARLINK_PEER_MAC权限。
回调返回真实设备地址，否则返回随机设备地址。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.NearLink.Base

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | Callback&lt;ScanResults[]&gt; | 是 | 监听扫描结果事件的回调。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported because the chip does not support it. |

