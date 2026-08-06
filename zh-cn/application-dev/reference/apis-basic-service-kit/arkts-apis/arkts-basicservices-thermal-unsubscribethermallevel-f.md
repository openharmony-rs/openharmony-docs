# unsubscribeThermalLevel

## unsubscribeThermalLevel

```TypeScript
function unsubscribeThermalLevel(callback?: AsyncCallback<void>): void
```

取消订阅热档位变化时的回调提醒。使用callback异步回调。

**起始版本：** 8

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为8。

**废弃版本：** 9

**替代接口：** [thermal.unregisterThermalLevelCallback](arkts-basicservices-thermal-unregisterthermallevelcallback-f.md#unregisterthermallevelcallback)

<!--Device-thermal-function unsubscribeThermalLevel(callback?: AsyncCallback<void>): void--><!--Device-thermal-function unsubscribeThermalLevel(callback?: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.PowerManager.ThermalManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;void&gt; | 否 | 回调函数，无返回值。不填该参数则取消所有回调。 |

**示例：**

```TypeScript
thermal.unsubscribeThermalLevel(() => {
    console.info('unsubscribe thermal level success.');
});
```

