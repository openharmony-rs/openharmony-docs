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
| [33600001](../../errorcode-universal.md#33600001-Selection) | Selection service exception. |
| [33600004](../../errorcode-universal.md#33600004-The) | The interface is called too frequently. |
| [33600005](../../errorcode-universal.md#33600005-The) | The interface is called at the wrong time. |
| [33600006](../../errorcode-universal.md#33600006-The) | The current application is prohibited from accessing content. |
| [33600007](../../errorcode-universal.md#33600007-The) | The length of selected content is out of range. |
| [33600008](../../errorcode-universal.md#33600008-Getting) | Getting the selected content times out. |

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

