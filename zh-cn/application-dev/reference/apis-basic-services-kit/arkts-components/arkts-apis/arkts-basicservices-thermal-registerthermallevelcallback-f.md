# registerThermalLevelCallback

## 导入模块

```TypeScript
import { thermal } from '@kit.BasicServicesKit';
```

## registerThermalLevelCallback

```TypeScript
function registerThermalLevelCallback(callback: Callback<ThermalLevel>): void
```

订阅热档位变化时的回调提醒。当设备温度跨越档位阈值导致热档位发生变化时，系统自动触发回调通知，通过callback返回变化后的热档位等级。使用callback异步回调。此方法与thermal.unregisterThermalLevelCallback配对使用，用于取消先前注册的热档位回调。

**起始版本：** 9

**系统能力：** SystemCapability.PowerManager.ThermalManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](arkts-basicservices-base-callback-i.md)&lt;[ThermalLevel](arkts-basicservices-thermal-thermallevel-e.md)&gt; | 是 | 回调函数，返回变化后的热档位。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |

**示例**

```TypeScript
try {
    thermal.registerThermalLevelCallback((level: thermal.ThermalLevel) => {
        console.info('thermal level is: ' + level);
    });
    console.info('register thermal level callback success.');
} catch (err) {
    console.error(`Failed to register thermal level callback. Code: ${err.code}, message: ${err.message}`);
}
```
