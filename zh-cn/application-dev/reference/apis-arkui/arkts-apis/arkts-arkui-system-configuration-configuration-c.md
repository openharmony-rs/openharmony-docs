# Configuration

**起始版本：** 12

<!--Device-unnamed-export default class Configuration--><!--Device-unnamed-export default class Configuration-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Lite

## 导入模块

```TypeScript
import { Configuration, LocaleResponse } from '@kit.ArkUI';
```

## getLocale

```TypeScript
static getLocale(): LocaleResponse
```

获取应用当前的语言和地区。默认与系统的语言和地区同步。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Configuration-static getLocale(): LocaleResponse--><!--Device-Configuration-static getLocale(): LocaleResponse-End-->

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [LocaleResponse](arkts-arkui-system-configuration-localeresponse-i.md) | 应用当前Locale相关信息。 |

