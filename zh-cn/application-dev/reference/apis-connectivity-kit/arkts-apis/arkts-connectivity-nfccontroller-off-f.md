# off

## 导入模块

```TypeScript
import { nfcController } from '@kit.ConnectivityKit';
```

## off("nfcStateChange")

```TypeScript
function off(type: "nfcStateChange", callback?: Callback<NfcState>): void
```

取消NFC开关状态事件的注册，取消后NFC状态变化时，就不会再收到Callback的通知。使用callback异步回调。

**起始版本：** 7

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Communication.NFC.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | "nfcStateChange" | 是 | 固定填"nfcStateChange"字符串。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[NfcState](arkts-connectivity-nfccontroller-nfcstate-e.md)&gt; | 否 | NFC状态改变回调函数，可以空缺不填。如果callback不填，将取消注册该事件关联的所有回调函数。 |
