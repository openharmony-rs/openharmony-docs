# off

## off('selectionCompleted')

```TypeScript
function off(type: 'selectionCompleted', callback?: Callback<SelectionInfo>): void
```

取消订阅划词完成事件。使用callback异步回调。

**起始版本：** 24

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为20。

<!--Device-selectionManager-function off(type: 'selectionCompleted', callback?: Callback<SelectionInfo>): void--><!--Device-selectionManager-function off(type: 'selectionCompleted', callback?: Callback<SelectionInfo>): void-End-->

**系统能力：** SystemCapability.SelectionInput.Selection

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'selectionCompleted' | 是 | 设置监听类型，固定取值为'selectionCompleted'。 |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;SelectionInfo&gt; | 否 | 回调函数，返回SelectionInfo。参数不填写时，取消订阅type对应的所有回调事件。 |

**示例：**

```TypeScript
import { selectionManager } from '@kit.BasicServicesKit';

// 定义划词完成事件回调函数，用于订阅和取消订阅
let selectionChangeCallback = (info: selectionManager.SelectionInfo) => {
  console.info('Enter the callback function.');
};

// 先订阅划词完成事件回调，为后续取消订阅做准备
selectionManager.on('selectionCompleted', selectionChangeCallback);
try {
  // 取消订阅划词完成事件
  selectionManager.off('selectionCompleted', selectionChangeCallback);
} catch (err) {
  console.error(`Failed to unregister selectionCompleted. Error code: ${err.code}, error message: ${err.message}`);
}
```

