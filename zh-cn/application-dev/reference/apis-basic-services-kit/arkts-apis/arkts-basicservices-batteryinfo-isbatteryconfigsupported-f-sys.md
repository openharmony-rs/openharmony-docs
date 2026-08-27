# isBatteryConfigSupported（系统接口）

## 导入模块

```TypeScript
import { batteryInfo } from '@kit.BasicServicesKit';
```

## isBatteryConfigSupported

```TypeScript
function isBatteryConfigSupported(sceneName: string): boolean
```

检查是否按场景名称启用电池配置。调用该接口后，系统将判断当前设备是否支持指定的充电场景配置，并返回检查结果。

**起始版本：** 11

**系统能力：** SystemCapability.PowerManager.BatteryManager.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| sceneName | string | 是 | 电池充电配置的场景名称，用于检查是否支持该充电配置场景。支持的场景名称由系统定义。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 如果设备支持该场景的电池配置，则返回true，否则返回false。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| [5100101](../errorcode-battery-info.md#5100101-连接服务失败) | Failed to connect to the service. |

**示例**

```TypeScript
import { batteryInfo } from '@kit.BasicServicesKit';

let sceneName = 'xxx';
let result = batteryInfo.isBatteryConfigSupported(sceneName);

console.info('The result is: ' + result);
```
