# isNRSupported

## 导入模块

```TypeScript
import { radio } from '@kit.TelephonyKit';
```

## isNRSupported

```TypeScript
function isNRSupported(): boolean
```

判断当前设备是否支持NR(New Radio)。

**起始版本：** 9

**系统能力：** SystemCapability.Telephony.CoreService

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | true：支持。<br>- false：不支持。 |

**示例**

```TypeScript
let result: boolean = radio.isNRSupported();
console.info("Result: " + result);
```

```TypeScript
let slotId: number = 0;
let result: boolean = radio.isNRSupported(slotId);
console.info("Result: " + result);
```


## isNRSupported

```TypeScript
function isNRSupported(slotId: number): boolean
```

判断当前设备是否支持NR(New Radio)。

**起始版本：** 9

**系统能力：** SystemCapability.Telephony.CoreService

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| slotId | number | 是 | 卡槽ID。<br>- 0：卡槽1。<br>- 1：卡槽2。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | true：支持。<br>- false：不支持。 |

**示例**

参见 [isNRSupported](#isnrsupported)
