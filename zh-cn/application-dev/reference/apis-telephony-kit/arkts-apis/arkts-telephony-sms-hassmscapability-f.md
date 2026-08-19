# hasSmsCapability

## 导入模块

```TypeScript
import { sms } from '@kit.TelephonyKit';
```

## hasSmsCapability

```TypeScript
function hasSmsCapability(): boolean
```

检查当前设备是否具备短信发送和接收能力，该方法是同步方法。

**起始版本：** 23

<!--Device-sms-function hasSmsCapability(): boolean--><!--Device-sms-function hasSmsCapability(): boolean-End-->

**系统能力：** SystemCapability.Telephony.SmsMms

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | true：设备具备短信发送和接收能力。<br/>- false：设备不具备短信发送和接收能力。 |

**示例**

```TypeScript
import { sms } from '@kit.TelephonyKit';

let result = sms.hasSmsCapability(); 
console.info(`hasSmsCapability: ${JSON.stringify(result)}`);
```

