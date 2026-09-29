# IDeliveryShortMessageCallback

```TypeScript
export interface IDeliveryShortMessageCallback
```

回调实例，返回短信送达报告。

**起始版本：** 6

<!--Device-sms-export interface IDeliveryShortMessageCallback--><!--Device-sms-export interface IDeliveryShortMessageCallback-End-->

**系统能力：** SystemCapability.Telephony.SmsMms

## 导入模块

```TypeScript
import { sms } from '@kit.TelephonyKit';
```

## pdu

```TypeScript
pdu: Array<number>
```

短信送达报告。

**类型：** Array&lt;number&gt;

**起始版本：** 6

<!--Device-IDeliveryShortMessageCallback-pdu: Array<int>--><!--Device-IDeliveryShortMessageCallback-pdu: Array<int>-End-->

**系统能力：** SystemCapability.Telephony.SmsMms
