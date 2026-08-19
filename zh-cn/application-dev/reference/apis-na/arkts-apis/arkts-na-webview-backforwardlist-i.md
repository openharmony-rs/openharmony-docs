# BackForwardList

Provides back and forward history list information method. related to [HistoryItem](../../apis-arkweb/arkts-apis/arkts-arkweb-webview-historyitem-i.md).

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-webview-interface BackForwardList--><!--Device-webview-interface BackForwardList-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## 导入模块

```TypeScript
```

## getItemAtIndex

```TypeScript
getItemAtIndex(index: int): HistoryItem
```

Get history entry at given index.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-BackForwardList-getItemAtIndex(index: int): HistoryItem--><!--Device-BackForwardList-getItemAtIndex(index: int): HistoryItem-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| index | int | 是 | Index of back forward list entry. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [HistoryItem](../../apis-arkweb/arkts-apis/arkts-arkweb-webview-historyitem-i.md) | HistoryItem at given index in back forward list. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. <br>2. Incorrect parameter types. 3.Parameter verification failed. |

## currentIndex

```TypeScript
currentIndex: int
```

Current index in BackForwardList.

**类型：** int

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-BackForwardList-currentIndex: int--><!--Device-BackForwardList-currentIndex: int-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## size

```TypeScript
size: int
```

Size of in BackForwardList.

**类型：** int

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-BackForwardList-size: int--><!--Device-BackForwardList-size: int-End-->

**系统能力：** SystemCapability.Web.Webview.Core

