# OnMessageCallback

```TypeScript
type OnMessageCallback = (msgId: string, msgParam?: ArrayBuffer) => void
```

当输入法框架需要显示预览文本时触发的回调。

**起始版本：** 23

<!--Device-inputMethodEngine-type OnMessageCallback = (msgId: string, msgParam?: ArrayBuffer) => void--><!--Device-inputMethodEngine-type OnMessageCallback = (msgId: string, msgParam?: ArrayBuffer) => void-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| msgId | string | 是 | 接收到的自定义通信数据的标识符。 |
| msgParam | ArrayBuffer | 否 | 接收到的自定义通信数据的消息体。 |

