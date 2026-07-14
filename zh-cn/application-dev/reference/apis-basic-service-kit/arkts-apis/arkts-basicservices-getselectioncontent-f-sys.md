# getSelectionContent（系统接口）

## getSelectionContent

```TypeScript
function getSelectionContent(): Promise<string>
```

获取选中文本的内容。使用Promise异步回调。

**起始版本：** 24

**系统能力：** SystemCapability.SelectionInput.Selection

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;string&gt; | Promise对象，返回当前选中文本的内容。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [33600001](../../apis-basic-services-kit/errorcode-selection.md#33600001-划词服务异常) | Selection service exception. |
| [33600004](../../apis-basic-services-kit/errorcode-selection.md#33600004-该接口被调用过于频繁) | The interface is called too frequently. |
| [33600005](../../apis-basic-services-kit/errorcode-selection.md#33600005-接口调用时机错误) | The interface is called at the wrong time. |
| [33600006](../../apis-basic-services-kit/errorcode-selection.md#33600006-当前应用禁止取词) | The current application is prohibited from accessing content. |
| [33600007](../../apis-basic-services-kit/errorcode-selection.md#33600007-划词内容超出范围) | The length of selected content is out of range. |
| [33600008](../../apis-basic-services-kit/errorcode-selection.md#33600008-获取内容超时) | Getting the selected content times out. |

**示例：**

```TypeScript
import { selectionManager } from '@kit.BasicServicesKit';

selectionManager.on('selectionCompleted', async (info: selectionManager.SelectionInfo) => {
  try {
    let content = await selectionManager.getSelectionContent();
  } catch (err) {
    console.error(`Failed to get selection content: ${err.code}, error message: ${err.message}`);
  }
});

```

