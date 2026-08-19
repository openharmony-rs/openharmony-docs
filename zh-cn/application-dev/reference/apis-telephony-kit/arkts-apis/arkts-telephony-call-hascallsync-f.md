# hasCallSync

## 导入模块

```TypeScript
import { call } from '@kit.TelephonyKit';
```

## hasCallSync

```TypeScript
function hasCallSync(): boolean
```

判断是否存在通话。

**起始版本：** 23

<!--Device-call-function hasCallSync(): boolean--><!--Device-call-function hasCallSync(): boolean-End-->

**系统能力：** SystemCapability.Telephony.CallManager

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 返回判断是否存在通话。返回true表示当前存在通话，false表示当前不存在通话。 |

**示例**

```TypeScript
let hasCall: boolean = call.hasCallSync();
console.info(`hasCallSync success, has call is ` + hasCall);
```

