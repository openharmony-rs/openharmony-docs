# unregisterThermalLevelCallback

## 导入模块

```TypeScript
import { thermal } from '@kit.BasicServicesKit';
```

<a id="unregisterthermallevelcallback"></a>
## unregisterThermalLevelCallback

```TypeScript
function unregisterThermalLevelCallback(callback?: Callback<void>): void
```

取消订阅热档位变化时的回调提醒。使用callback异步回调。

**起始版本：** 9

<!--Device-thermal-function unregisterThermalLevelCallback(callback?: Callback<void>): void--><!--Device-thermal-function unregisterThermalLevelCallback(callback?: Callback<void>): void-End-->

**系统能力：** SystemCapability.PowerManager.ThermalManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-arkui/arkts-components/arkts-arkui-callback-i.md)&lt;void&gt; | 否 | 可选参数，回调函数，无返回值。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Incorrect parameter types; |

**示例：**

```TypeScript
try {
    thermal.unregisterThermalLevelCallback(() => {
        console.info('unsubscribe thermal level success.');
    });
    console.info('unregister thermal level callback success.');
} catch (err) {
    console.error(`Failed to unregister thermal level callback. Code: ${err.code}, message: ${err.message}`);
}

```

