# onSelectionComplete

## onSelectionComplete

```TypeScript
function onSelectionComplete(callback: Callback<SelectionInfo>): void
```

订阅划词完成事件，与[offSelectionComplete](arkts-basicservices-selectionmanager-offselectioncomplete-f.md#offSelectionComplete)搭配 使用取消订阅。

**起始版本：** 24

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为24。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-selectionManager-function onSelectionComplete(callback: Callback<SelectionInfo>): void--><!--Device-selectionManager-function onSelectionComplete(callback: Callback<SelectionInfo>): void-End-->

**系统能力：** SystemCapability.SelectionInput.Selection

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](arkts-basicservices-callback-t.md)&lt;[SelectionInfo](arkts-basicservices-selectionmanager-selectioninfo-i-sys.md)&gt; | 是 | 回调函数，返回划词事件信息[SelectionInfo](arkts-basicservices-selectionmanager-selectioninfo-i-sys.md#SelectionInfo（系统接口）)。该回 调仅在用户通过鼠标或触控板选中文本（双击/三击/滑动）后按下Ctrl键时触发。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [33600003](../../apis-basic-services-kit/errorcode-selection.md#33600003-调用接口的应用与系统设置中选择的应用不匹配) | The application calling the API does not match the application selected in the system settings. |

## 示例

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

