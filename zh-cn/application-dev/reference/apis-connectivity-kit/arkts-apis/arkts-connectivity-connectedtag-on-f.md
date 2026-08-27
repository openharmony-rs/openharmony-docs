# on

## 导入模块

```TypeScript
import { connectedTag } from '@kit.ConnectivityKit';
```

## on("notify")

```TypeScript
function on(type: "notify", callback: Callback<number>): void
```

注册NFC场强状态事件。

**起始版本：** 8

**需要权限：** ohos.permission.NFC_TAG

**系统能力：** SystemCapability.Communication.ConnectedTag

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | "notify" | 是 | 固定填"notify"字符串。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;number&gt; | 是 | 回调函数。注册成功的返回值参见[NfcRfType](arkts-connectivity-connectedtag-nfcrftype-e.md)。 |
