# getPageContent（系统接口）

## getPageContent

```TypeScript
function getPageContent(options?: ContentOptions): Promise<PageContent>
```

在需要抓取内容的窗口在桌面上时，调用该接口以获取屏上内容。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**需要权限：** ohos.permission.GET_SCREEN_CONTENT

<!--Device-onScreen-function getPageContent(options?: ContentOptions): Promise<PageContent>--><!--Device-onScreen-function getPageContent(options?: ContentOptions): Promise<PageContent>-End-->

**系统能力：** SystemCapability.MultimodalAwareness.OnScreenAwareness

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [ContentOptions](arkts-multimodalawareness-onscreen-contentoptions-i-sys.md) | 否 | 获取屏上内容的选项，默认为不指定window ID，且其余选项均为false。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[PageContent](arkts-multimodalawareness-onscreen-pagecontent-i-sys.md)&gt; | Promise对象，返回获取到的页面内容 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [34000006](../../apis-multimodalawareness-kit/errorcode-onScreen.md#34000006-请求超时) | The request timed out. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. Function can not work correctly due to limited &lt;br&gt; device capabilities. |
| [34000004](../../apis-multimodalawareness-kit/errorcode-onScreen.md#34000004-页面未准备就绪) | The page is not ready. |
| [34000002](../../apis-multimodalawareness-kit/errorcode-onScreen.md#34000002-应用或页面不支持) | The application or page is not supported. |
| [34000003](../../apis-multimodalawareness-kit/errorcode-onScreen.md#34000003-窗口id无效) | The window ID is invalid. Possible causes: 1. window id is not passed &lt;br&gt; when screen is splited. 2. passed window id is not on screen or floating. |
| [34000001](../../apis-multimodalawareness-kit/errorcode-onScreen.md#34000001-服务异常) | Service exception. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. An attempt was made to get page content forbidden by &lt;br&gt; permission: ohos.permission.GET_SCREEN_CONTENT. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission check failed. A non-system application uses the system API. |

