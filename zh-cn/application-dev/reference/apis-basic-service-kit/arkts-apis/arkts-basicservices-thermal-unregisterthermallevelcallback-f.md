# unregisterThermalLevelCallback

## unregisterThermalLevelCallback

```TypeScript
function unregisterThermalLevelCallback(callback?: Callback<void>): void
```

取消订阅热档位变化时的回调提醒。使用callback异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-thermal-function unregisterThermalLevelCallback(callback?: Callback<void>): void--><!--Device-thermal-function unregisterThermalLevelCallback(callback?: Callback<void>): void-End-->

**系统能力：** SystemCapability.PowerManager.ThermalManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](arkts-basicservices-callback-t.md)&lt;void&gt; | 否 | 可选参数，回调函数，无返回值。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Incorrect parameter types; |

## 示例

```TypeScript
try {
    thermal.unregisterThermalLevelCallback(() => {
        console.info('unsubscribe thermal level success.');
    });
    console.info('unregister thermal level callback success.');
} catch(err) {
    console.error('unregister thermal level callback failed, err: ' + err);
}
```

