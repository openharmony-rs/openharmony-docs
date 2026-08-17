# on_p2pConnectionChange

## on_p2pConnectionChange

```TypeScript
function on(type: 'p2pConnectionChange', callback: Callback<WifiP2pLinkedInfo>): void
```

订阅P2P连接改变事件。

**起始版本：** 8

**ArkTS模式：** 起始版本为8。

**废弃版本：** 9

**替代接口：** p2pConnectionChange

**需要权限：** ohos.permission.GET_WIFI_INFO

<!--Device-wifi-function on(type: 'p2pConnectionChange', callback: Callback<WifiP2pLinkedInfo>): void--><!--Device-wifi-function on(type: 'p2pConnectionChange', callback: Callback<WifiP2pLinkedInfo>): void-End-->

**系统能力：** SystemCapability.Communication.WiFi.P2P

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'p2pConnectionChange' | 是 | 事件名称。 |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;WifiP2pLinkedInfo&gt; | 是 | 状态改变回调函数 |

