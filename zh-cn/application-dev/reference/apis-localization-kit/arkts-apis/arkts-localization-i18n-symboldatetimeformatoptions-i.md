# SymbolDateTimeFormatOptions

创建自定义符号时间日期格式化对象时的可选配置项。继承自Intl.DateTimeFormatOptions，支持Intl.DateTimeFormatOptions的所有配置项，并且功能与其一致。

**继承/实现关系：** SymbolDateTimeFormatOptions extends [Intl.DateTimeFormatOptions](Intl.DateTimeFormatOptions)

**起始版本：** 26.0.0

<!--Device-i18n-export interface SymbolDateTimeFormatOptions extends Intl.DateTimeFormatOptions--><!--Device-i18n-export interface SymbolDateTimeFormatOptions extends Intl.DateTimeFormatOptions-End-->

**系统能力：** SystemCapability.Global.I18n

## 导入模块

```TypeScript
import { i18n } from '@kit.LocalizationKit';
```

## amPMSymbol

```TypeScript
amPMSymbol?: string[] | undefined
```

指定的上午和下午符号，要求数组长度不小于2，其中第一个元素为上午符号，第二个元素为下午符号。默认值：区域默认的符号。

**类型：** string[] | undefined

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-SymbolDateTimeFormatOptions-amPMSymbol?: string[] | undefined--><!--Device-SymbolDateTimeFormatOptions-amPMSymbol?: string[] | undefined-End-->

**系统能力：** SystemCapability.Global.I18n

