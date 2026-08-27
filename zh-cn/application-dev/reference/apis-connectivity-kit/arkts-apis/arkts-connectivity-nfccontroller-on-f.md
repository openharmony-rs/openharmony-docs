# on

## 导入模块

```TypeScript
import { nfcController } from '@kit.ConnectivityKit';
```

## on("nfcStateChange")

```TypeScript
function on(type: "nfcStateChange", callback: Callback<NfcState>): void
```

注册NFC开关状态事件，获取NFC状态的变化通知。使用callback异步回调。

**起始版本：** 7

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Communication.NFC.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | "nfcStateChange" | 是 | 固定填"nfcStateChange"字符串。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[NfcState](arkts-connectivity-nfccontroller-nfcstate-e.md)&gt; | 是 | 回调函数，返回NFC状态的枚举值。 |
