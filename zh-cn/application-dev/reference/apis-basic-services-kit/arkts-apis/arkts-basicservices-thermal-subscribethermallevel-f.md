# subscribeThermalLevel

## 导入模块

```TypeScript
import { thermal } from '@kit.BasicServicesKit';
```

## subscribeThermalLevel

```TypeScript
function subscribeThermalLevel(callback: AsyncCallback<ThermalLevel>): void
```

订阅热档位变化时的回调提醒。使用callback异步回调。此方法需与thermal.unsubscribeThermalLevel配对使用，在不再需要监听时取消订阅。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [registerThermalLevelCallback](arkts-basicservices-thermal-registerthermallevelcallback-f.md)

**系统能力：** SystemCapability.PowerManager.ThermalManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;[ThermalLevel](arkts-basicservices-thermal-thermallevel-e.md)&gt; | 是 | 回调函数，返回变化后的热档位。 |

**示例**

```TypeScript
thermal.subscribeThermalLevel((err: Error, level: thermal.ThermalLevel) => {
    if (err) {
        console.error('subscribe thermal level failed, err: ' + err);
        return;
    }
    console.info('thermal level is: ' + level);
});
```
