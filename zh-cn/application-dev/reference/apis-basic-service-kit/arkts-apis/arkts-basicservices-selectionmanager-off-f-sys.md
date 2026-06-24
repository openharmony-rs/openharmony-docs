# off（系统接口）

## off('selectionCompleted')

```TypeScript
function off(type: 'selectionCompleted', callback?: Callback<SelectionInfo>): void
```

取消订阅划词完成事件。使用callback异步回调。

**起始版本：** 24

**系统能力：** SystemCapability.SelectionInput.Selection

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'selectionCompleted' | 是 | 设置监听类型，固定取值为'selectionCompleted'。 |
| callback | Callback&lt;SelectionInfo&gt; | 否 | 回调函数，返回SelectionInfo。参数不填写时，取消订阅type对应的所有回调事件。 |

**示例：**

```TypeScript
import { selectionManager } from '@kit.BasicServicesKit';

let selectionChangeCallback = (info: selectionManager.SelectionInfo) => {
  console.info(`Enter the callback function.`);
};

selectionManager.on('selectionCompleted', selectionChangeCallback);
try {
  selectionManager.off('selectionCompleted', selectionChangeCallback);
} catch (err) {
  console.error(`Failed to unregister selectionCompleted: ${err.code}, error message: ${err.message}`);
}

```

