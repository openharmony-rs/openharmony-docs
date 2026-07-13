# subscribeThermalLevel

## subscribeThermalLevel

```TypeScript
function subscribeThermalLevel(callback: AsyncCallback<ThermalLevel>): void
```

订阅热档位变化时的回调提醒。使用callback异步回调。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [registerThermalLevelCallback](arkts-basicservices-registerthermallevelcallback-f.md#registerthermallevelcallback-1)

**系统能力：** SystemCapability.PowerManager.ThermalManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | AsyncCallback&lt;ThermalLevel&gt; | 是 | 回调函数，返回变化后的热档位；该参数是一个函数类型。 |

**示例：**

```TypeScript
thermal.subscribeThermalLevel((err: Error, level: thermal.ThermalLevel) => {
    console.info('thermal level is: ' + level);
});

```

