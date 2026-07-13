# unsubscribeThermalLevel

## unsubscribeThermalLevel

```TypeScript
function unsubscribeThermalLevel(callback?: AsyncCallback<void>): void
```

取消订阅热档位变化时的回调提醒。使用callback异步回调。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [unregisterThermalLevelCallback](arkts-basicservices-unregisterthermallevelcallback-f.md#unregisterthermallevelcallback-1)

**系统能力：** SystemCapability.PowerManager.ThermalManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | AsyncCallback&lt;void&gt; | 否 | 回调函数，无返回值。不填该参数则取消所有回调。 |

**示例：**

```TypeScript
thermal.unsubscribeThermalLevel(() => {
    console.info('unsubscribe thermal level success.');
});

```

