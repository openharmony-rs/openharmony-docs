# SortOptions（系统接口）

语言或国家地区排序选项。

**起始版本：** 10

<!--Device-i18n-export interface SortOptions--><!--Device-i18n-export interface SortOptions-End-->

**系统能力：** SystemCapability.Global.I18n

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { i18n } from '@kit.LocalizationKit';
```

## isSuggestedFirst

```TypeScript
isSuggestedFirst?: boolean
```

true表示将推荐语言或国家地区在排序结果中置顶，false表示不将推荐语言或国家地区在排序结果中置顶。默认值：true。

**类型：** boolean

**起始版本：** 10

<!--Device-SortOptions-isSuggestedFirst?: boolean--><!--Device-SortOptions-isSuggestedFirst?: boolean-End-->

**系统能力：** SystemCapability.Global.I18n

**系统接口：** 此接口为系统接口。

## isUseLocalName

```TypeScript
isUseLocalName?: boolean
```

true表示使用本地名称进行排序，false表示不使用本地名称进行排序。若调用方法为getLanguageInfoArray，isUseLocalName属性默认值为true。若调用方法为getRegionInfoArray，isUseLocalName属性默认值为false。

**类型：** boolean

**起始版本：** 10

<!--Device-SortOptions-isUseLocalName?: boolean--><!--Device-SortOptions-isUseLocalName?: boolean-End-->

**系统能力：** SystemCapability.Global.I18n

**系统接口：** 此接口为系统接口。

## locale

```TypeScript
locale?: string
```

表示区域ID的字符串，由语言、脚本、国家或地区组成，如"zh-Hans-CN"。默认值：系统当前区域ID。

**类型：** string

**起始版本：** 10

<!--Device-SortOptions-locale?: string--><!--Device-SortOptions-locale?: string-End-->

**系统能力：** SystemCapability.Global.I18n

**系统接口：** 此接口为系统接口。

