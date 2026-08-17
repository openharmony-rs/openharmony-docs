# offP2pPersistentGroupChange

## offP2pPersistentGroupChange

```TypeScript
function offP2pPersistentGroupChange(callback?: Callback<void>): void
```

取消注册P2P永久组状态改变事件。

**起始版本：** 23

**ArkTS模式：** 起始版本为23。

**废弃版本：** -1

**需要权限：** ohos.permission.GET_WIFI_INFO

<!--Device-wifiManager-function offP2pPersistentGroupChange(callback?: Callback<void>): void--><!--Device-wifiManager-function offP2pPersistentGroupChange(callback?: Callback<void>): void-End-->

**系统能力：** SystemCapability.Communication.WiFi.P2P

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;void&gt; | 否 | 状态改变回调函数。如果未指定callback参数，将取消注册该事件关联的所有回调函数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [2801000](../errorcode-wifi.md#2801000-p2p模块异常) | Operation failed. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |

