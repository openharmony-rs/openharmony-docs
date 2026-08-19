# getSelectionContent（系统接口）

## 导入模块

```TypeScript
import { selectionManager } from '@kit.BasicServicesKit';
```

## getSelectionContent

```TypeScript
function getSelectionContent(): Promise<string>
```

获取选中文本的内容。使用Promise异步回调。需在 [on('selectionCompleted')](arkts-basicservices-selectionmanager-onselectioncompleted-f-sys.md#onselectioncompleted) 回调中调用，且仅在划词完成事件触发后有效。

**起始版本：** 24

<!--Device-selectionManager-function getSelectionContent(): Promise<string>--><!--Device-selectionManager-function getSelectionContent(): Promise<string>-End-->

**系统能力：** SystemCapability.SelectionInput.Selection

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;string&gt; | Promise对象，返回当前选中文本的内容。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [33600001](../errorcode-selection.md#33600001-划词服务调用异常) | Selection service invocation exception. |
| [33600004](../errorcode-selection.md#33600004-该接口被调用过于频繁) | The interface is called too frequently. |
| [33600005](../errorcode-selection.md#33600005-接口调用时机错误) | The interface is called at the wrong time. |
| [33600006](../errorcode-selection.md#33600006-当前应用禁止获取内容) | The current application is prohibited from accessing content. |
| [33600007](../errorcode-selection.md#33600007-划词内容长度超出范围) | The length of selected content is out of range. |
| [33600008](../errorcode-selection.md#33600008-获取选中内容超时) | Getting the selected content times out. |

**示例**

ArkTS-Dyn示例：

```TypeScript
import { selectionManager } from '@kit.BasicServicesKit';

// 订阅划词完成事件，在回调中获取选中文本
selectionManager.on('selectionCompleted', async (info: selectionManager.SelectionInfo) => {
  try {
    // 获取选中文本内容
    let content = await selectionManager.getSelectionContent();
    console.info(`Succeeded in getting selection content: ${content}`);
  } catch (err) {
    console.error(`Failed to get selection content. Error code: ${err.code}, error message: ${err.message}`);
  }
});
```

ArkTS-Sta示例：

```TypeScript
import selectionManager from '@ohos.selectionInput.selectionManager';

// 订阅划词完成事件，在回调中获取选中文本
selectionManager.onSelectionComplete((info: selectionManager.SelectionInfo) => {
  try {
    getSelectionContentAsync().catch((err) => {
      console.error(`Failed to get selection content. Error code: ${err.code}, error message: ${err.message}`);
    })
  } catch (err) {
    console.error(`Failed to get selection content. Error code: ${err.code}, error message: ${err.message}`);
  }
});

async function getSelectionContentAsync(): Promise<void> {
  // 获取选中文本内容
  const content = await selectionManager.getSelectionContent();
  console.info(`Succeeded in getting selection content: ${content}`);
}
```

