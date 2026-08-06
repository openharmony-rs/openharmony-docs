# onSelectionComplete

## onSelectionComplete

```TypeScript
function onSelectionComplete(callback: Callback<SelectionInfo>): void
```

订阅划词完成事件。使用callback异步回调。

**起始版本：** 24

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为24。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-selectionManager-function onSelectionComplete(callback: Callback<SelectionInfo>): void--><!--Device-selectionManager-function onSelectionComplete(callback: Callback<SelectionInfo>): void-End-->

**系统能力：** SystemCapability.SelectionInput.Selection

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;SelectionInfo&gt; | 是 | 回调函数，返回当前划词信息。该回调仅在用户通过鼠标或触控板选中文本（鼠标左键双击/三击/按下滑动）后按下Ctrl键时触发。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [33600003](../../apis-basic-services-kit/errorcode-selection.md#33600003-调用接口的应用与系统设置中选择的应用不匹配) | The application calling the API does not match the application selected in the system settings. |

**示例：**

```TypeScript
import selectionManager from '@ohos.selectionInput.selectionManager';

try {
  // 订阅划词完成事件
  selectionManager.onSelectionComplete((info: selectionManager.SelectionInfo) => {
    console.info(`SelectionInfo: ${JSON.stringify(info)}`);
  });
} catch (err) {
  console.error(`Failed to register selectionCompleted callback. Error code: ${err.code}, error message: ${err.message}`);
}
```

