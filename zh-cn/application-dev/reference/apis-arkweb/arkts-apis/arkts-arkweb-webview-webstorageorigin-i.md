# WebStorageOrigin

提供Web SQL数据库的使用信息。

**起始版本：** 9

<!--Device-webview-interface WebStorageOrigin--><!--Device-webview-interface WebStorageOrigin-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## 导入模块

```TypeScript
import { webview } from '@kit.ArkWeb';
```

## origin

```TypeScript
origin: string
```

指定源的字符串索引。

**类型：** string

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebStorageOrigin-origin: string--><!--Device-WebStorageOrigin-origin: string-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## quota

```TypeScript
quota: number
```

指定源的存储配额。

单位：byte。

**类型：** number

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebStorageOrigin-quota: number--><!--Device-WebStorageOrigin-quota: number-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## usage

```TypeScript
usage: number
```

指定源的存储量。

单位：byte。

**类型：** number

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebStorageOrigin-usage: number--><!--Device-WebStorageOrigin-usage: number-End-->

**系统能力：** SystemCapability.Web.Webview.Core

