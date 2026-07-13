# on（系统接口）

## on('selectionCompleted')

```TypeScript
function on(type: 'selectionCompleted', callback: Callback<SelectionInfo>): void
```

订阅划词完成事件。使用callback异步回调。

**起始版本：** 24

**系统能力：** SystemCapability.SelectionInput.Selection

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'selectionCompleted' | 是 | 设置监听类型，固定取值为'selectionCompleted'。 |
| callback | Callback&lt;SelectionInfo&gt; | 是 | 回调函数，返回当前划词信息。该回调仅在用户通过鼠标或触控板选中文本（鼠标左键双击/三击/按下滑动）后按下Ctrl键时触发。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [33600003](../../apis-basic-services-kit/errorcode-selection.md#33600003-调用api的应用程序与系统设置中选择的应用程序不匹配) | The application calling the API does not match the applicationselected in the system settings. |

**示例：**

```TypeScript
import { selectionManager } from '@kit.BasicServicesKit';

try {
  selectionManager.on('selectionCompleted', (info: selectionManager.SelectionInfo) => {
    console.info(`Enter the callback function.`);
  });
} catch (err) {
  console.error(`Failed to register selectionCompleted callback: ${err.code}, error message: ${err.message}`);
}

```

