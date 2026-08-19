# unsubscribeThermalLevel

## 导入模块

```TypeScript
import { thermal } from '@kit.BasicServicesKit';
```

## unsubscribeThermalLevel

```TypeScript
function unsubscribeThermalLevel(callback?: AsyncCallback<void>): void
```

取消订阅热档位变化时的回调提醒。使用callback异步回调。此方法与thermal.subscribeThermalLevel配对使用，用于取消先前订阅的热档位回调。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [unregisterThermalLevelCallback](arkts-basicservices-thermal-unregisterthermallevelcallback-f.md)

<!--Device-thermal-function unsubscribeThermalLevel(callback?: AsyncCallback<void>): void--><!--Device-thermal-function unsubscribeThermalLevel(callback?: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.PowerManager.ThermalManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](arkts-basicservices-asynccallback-t.md)&lt;void&gt; | 否 | 回调函数，用来执行取消热档位变化回调后的资源回收等操作，无返回值。 |

**示例**

```TypeScript
thermal.unsubscribeThermalLevel(() => {
    console.info('unsubscribe thermal level success.');
});
```

