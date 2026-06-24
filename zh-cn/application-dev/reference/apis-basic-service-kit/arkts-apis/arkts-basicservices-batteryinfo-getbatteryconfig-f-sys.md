# getBatteryConfig（系统接口）

## getBatteryConfig

```TypeScript
function getBatteryConfig(sceneName: string): string
```

按场景名称查询电池配置。

**起始版本：** 11

**系统能力：** SystemCapability.PowerManager.BatteryManager.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| sceneName | string | 是 | 设置场景名称；该参数必须为字符串类型。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 返回电池充电配置，否则返回""。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-Permission) | Permission verification failed. A non-system application calls a system API. |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1. Incorrect parameter types; |
| [5100101](../../errorcode-universal.md#5100101-Failed) | Failed to connect to the service. |

**示例：**

```TypeScript
import {batteryInfo} from '@kit.BasicServicesKit';

let sceneName = 'xxx';
let result = batteryInfo.getBatteryConfig(sceneName);

console.info("The result is: " + result);

```

