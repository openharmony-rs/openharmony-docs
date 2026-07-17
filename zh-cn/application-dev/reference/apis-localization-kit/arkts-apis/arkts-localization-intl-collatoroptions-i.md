# CollatorOptions

创建排序对象时可设置的配置项。

从API version 9开始，CollatorOptions中的属性改为可选。

**起始版本：** 8

<!--Device-intl-export interface CollatorOptions--><!--Device-intl-export interface CollatorOptions-End-->

**系统能力：** SystemCapability.Global.I18n

## 导入模块

```TypeScript
import { intl } from '@kit.LocalizationKit';
```

## caseFirst

```TypeScript
caseFirst?: string
```

区域的排序规则是否考虑大小写，取值包括：

"upper"：大写排前面。

"lower"：小写排前面。

"false"：使用区域默认的大小写排序规则。

默认值："false"。

**类型：** string

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-CollatorOptions-caseFirst?: string--><!--Device-CollatorOptions-caseFirst?: string-End-->

**系统能力：** SystemCapability.Global.I18n

## collation

```TypeScript
collation?: string
```

区域的排序规则，取值包括：

"big5han"：拉丁字母使用的拼音排序。

"compat"：兼容性排序，仅用于阿拉伯语。

"dict"：词典风格排序，仅用于僧伽罗语。

"direct"：二进制码点排序。

"ducet"：按Unicode排序元素表排序。

"eor"：按欧洲排序规则排序。

"gb2312"：拼音排序，仅用于中文排序。

"phonebk"：电话本风格排序。

"phonetic"：发音排序。

"pinyin"：拼音排序。

"reformed"：瑞典语排序。

"searchjl"：韩语初始辅音搜索的特殊排序。

"stroke"：汉语的笔画排序。

"trad"：传统风格排序，如西班牙语。

"unihan"：统一汉字排序，用于日语、韩语、中文等汉字排序。

"zhuyin"：注音排序，仅用于中文排序。

默认值："default"。

**类型：** string

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-CollatorOptions-collation?: string--><!--Device-CollatorOptions-collation?: string-End-->

**系统能力：** SystemCapability.Global.I18n

## ignorePunctuation

```TypeScript
ignorePunctuation?: boolean
```

true表示忽略标点符号，false表示考虑标点符号。

默认值：false。

**类型：** boolean

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-CollatorOptions-ignorePunctuation?: boolean--><!--Device-CollatorOptions-ignorePunctuation?: boolean-End-->

**系统能力：** SystemCapability.Global.I18n

## localeMatcher

```TypeScript
localeMatcher?: string
```

区域匹配算法，取值范围：

"lookup"：精确匹配。

"best fit"：最佳匹配。

默认值："best fit"。

**类型：** string

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-CollatorOptions-localeMatcher?: string--><!--Device-CollatorOptions-localeMatcher?: string-End-->

**系统能力：** SystemCapability.Global.I18n

## numeric

```TypeScript
numeric?: boolean
```

数字排序，取值包括：

true：使用数字排序，比如：'1' < '2' < '10' < '11'。

false：不使用数字排序，比如：'1' < '10' < '11' < '2'。

默认值：false。

**类型：** boolean

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-CollatorOptions-numeric?: boolean--><!--Device-CollatorOptions-numeric?: boolean-End-->

**系统能力：** SystemCapability.Global.I18n

## sensitivity

```TypeScript
sensitivity?: string
```

表示字符串中的哪些差异会导致非零结果值，取值范围：

"base"：不同的字母比较不相等，比如：'a' ≠ 'b', 'a' = 'á', 'a' = 'A'。

"accent"：不同的字母或不同读音的相同字母比较不相等，比如'a' ≠ 'b', 'a' ≠ 'á', 'a' = 'A'。

"case"：不同的字母或相同字母大小写比较不相等，比如：'a' ≠ 'b', 'a' = 'á', 'a' ≠ 'A'。

"variant"：不同的字母或读音及其它有区别的标志或大小写都是不相等的，比如：'a' ≠ 'b', 'a' ≠ 'á', 'a' ≠ 'A'。

默认值："variant"。

**类型：** string

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-CollatorOptions-sensitivity?: string--><!--Device-CollatorOptions-sensitivity?: string-End-->

**系统能力：** SystemCapability.Global.I18n

## usage

```TypeScript
usage?: string
```

比较的用途，取值范围：

"sort"：用作排序。

"search"：用作查找匹配的字符串。

默认值："sort"。

**类型：** string

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-CollatorOptions-usage?: string--><!--Device-CollatorOptions-usage?: string-End-->

**系统能力：** SystemCapability.Global.I18n

