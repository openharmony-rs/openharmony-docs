# registerThermalLevelCallback

## 导入模块

```TypeScript
import { thermal } from '@kit.BasicServicesKit';
```

## registerThermalLevelCallback

```TypeScript
function registerThermalLevelCallback(callback: Callback<ThermalLevel>): void
```

订阅热档位变化时的回调提醒。使用callback异步回调。当设备温度跨越档位阈值导致热档位发生变化时，系统自动触发回调通知，通过callback返回变化后的热档位等级。此方法与[thermal.unregisterThermalLevelCallback](arkts-basicservices-thermal-unregisterthermallevelcallback-f.md)配对使用，用于取消先前注册的热档位回调。

- 每个进程仅支持订阅一个回调，重复订阅将覆盖。  
- 回调函数应尽快返回，不可执行耗时操作（如同步文件 I/O），否则可能阻塞系统热档位通知投递。  
- 当热管理服务异常重启后，已注册的回调将自动失效且不会收到通知。开发者需重新调用 registerThermalLevelCallback 恢复订阅。  
- 当热管理服务不可用时，订阅可能静默失败且不抛出异常。开发者无法从返回值判断订阅是否成功。建议在订阅后通过[thermal.getLevel](arkts-basicservices-thermal-getlevel-f.md)验证服务是否可用  
（若[thermal.getLevel](arkts-basicservices-thermal-getlevel-f.md)返回COOL且设备明显发热，则服务可能不可用）。

**起始版本：** 9

<!--Device-thermal-function registerThermalLevelCallback(callback: Callback<ThermalLevel>): void--><!--Device-thermal-function registerThermalLevelCallback(callback: Callback<ThermalLevel>): void-End-->

**系统能力：** SystemCapability.PowerManager.ThermalManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](arkts-basicservices-base-callback-i.md)&lt;[ThermalLevel](arkts-basicservices-thermal-thermallevel-e.md)&gt; | 是 | 回调函数，返回变化后的热档位。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-函数参数数量或参数类型不匹配) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |

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
