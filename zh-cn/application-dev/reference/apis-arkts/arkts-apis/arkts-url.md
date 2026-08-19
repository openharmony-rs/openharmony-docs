# @ohos.url(URL字符串解析)

URL是统一资源定位符，本模块提供了常用的工具函数，实现了解析URL字符串、构造URL对象以及对URL查询参数的解析和操作等功能。 模块主要包含以下核心类： - [URL](arkts-arkts-url-url-c.md)：用于解析和构造完整URL。 - [URLParams](arkts-arkts-url-urlparams-c.md)：用于操作URL查询参数。 - [URLSearchParams](arkts-arkts-url-urlsearchparams-c.md)：从API version 9开始废弃，建议使用[URLParams](arkts-arkts-url-urlparams-c.md)替代。 > **说明：** > > - 本模块同时支持ArkTS-Dyn、ArkTS-Sta。

**起始版本：** 23

<!--Device-unnamed-declare namespace url--><!--Device-unnamed-declare namespace url-End-->

**系统能力：** SystemCapability.Utils.Lang

## 导入模块

```TypeScript
import { url } from '@kit.ArkTS';
```

## 汇总

### 类

| 名称 | 说明 |
| --- | --- |
| [URL(URL字符串解析)](arkts-arkts-url-url-c.md) | 用于解析和构造完整URL。 |
| [URLParams(URL字符串解析)](arkts-arkts-url-urlparams-c.md) | URLParams是一个用于解析、构造和操作URL参数的实用类。该类提供了统一的接口来处理URL查询参数。 |
| [URLSearchParams(URL字符串解析)](arkts-arkts-url-urlsearchparams-c.md) | URLSearchParams接口定义了一些处理URL查询字符串的实用方法，从API version 9开始废弃，建议使用[URLParams](arkts-arkts-url-urlparams-c.md)。 |

### 类型

| 名称 | 说明 |
| --- | --- |
| [UrlCbFn(URL字符串解析)](arkts-arkts-url-urlcbfn-t.md) | [forEach](arkts-arkts-url-urlparams-c.md#foreach)函数所需的回调函数。 |

