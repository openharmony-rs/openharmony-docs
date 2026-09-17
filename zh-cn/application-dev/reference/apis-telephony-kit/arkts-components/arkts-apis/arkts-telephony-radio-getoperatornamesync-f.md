# getOperatorNameSync

## 导入模块

```TypeScript
import { radio } from '@kit.TelephonyKit';
```

## getOperatorNameSync

```TypeScript
function getOperatorNameSync(slotId: number): string
```

获取运营商名称。

**起始版本：** 10

**系统能力：** SystemCapability.Telephony.CoreService

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| slotId | number | 是 | 卡槽ID。<br>- 0：卡槽1。<br>- 1：卡槽2。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 返回运营商名称。例如：中国移动。 |

**示例**

```TypeScript
// 指定卡槽ID，0表示卡槽1
let slotId: number = 0;
try {
    // 同步获取运营商名称
    let operatorName: string = radio.getOperatorNameSync(slotId);
    console.info(`operator name is:` + operatorName);
} catch (err) {
    console.error(`getOperatorNameSync failed, err->${JSON.stringify(err)}`);
}
```
