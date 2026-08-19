# BackForwardList

BackForwardList是ArkWeb框架中用于访问Web组件浏览历史列表的接口，通过 [getBackForwardEntries](arkts-arkweb-webview-webviewcontroller-c.md#getbackforwardentries)方法获取。该接口提供对页面导航历史记录的只读访问能力，开发者可以获取当前历 史列表的基本信息（当前索引和历史条目总数），以及通过索引获取指定历史记录项的详细信息。

**起始版本：** 9

<!--Device-webview-interface BackForwardList--><!--Device-webview-interface BackForwardList-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## 导入模块

```TypeScript
import { webview } from '@kit.ArkWeb';
```

## getItemAtIndex

```TypeScript
getItemAtIndex(index: number): HistoryItem
```

获取历史列表中指定索引的历史记录项信息。需先通过[getBackForwardEntries](arkts-arkweb-webview-webviewcontroller-c.md#getbackforwardentries)方法获取 BackForwardList实例。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-BackForwardList-getItemAtIndex(index: number): HistoryItem--><!--Device-BackForwardList-getItemAtIndex(index: number): HistoryItem-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| index | number | 是 | 指定历史列表中的索引。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [HistoryItem](arkts-arkweb-webview-historyitem-i.md) | 历史记录项。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. <br>2. Incorrect parameter types. 3.Parameter verification failed. |

## currentIndex

```TypeScript
currentIndex: number
```

当前在页面历史列表中的索引。

**类型：** number

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-BackForwardList-currentIndex: number--><!--Device-BackForwardList-currentIndex: number-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## size

```TypeScript
size: number
```

历史列表中历史记录的数量，最多保存50条，超过时起始记录会被覆盖。

**类型：** number

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-BackForwardList-size: number--><!--Device-BackForwardList-size: number-End-->

**系统能力：** SystemCapability.Web.Webview.Core

