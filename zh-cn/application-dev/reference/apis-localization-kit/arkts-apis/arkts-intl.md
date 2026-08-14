# @ohos.intl(国际化-Intl)

/*
 Copyright (c) 2026 Huawei Device Co., Ltd.
 Licensed under the Apache License, Version 2.0 (the "License");
 you may not use this file except in compliance with the License.
 You may obtain a copy of the License at
 http://www.apache.org/licenses/LICENSE-2.0
 Unless required by applicable law or agreed to in writing, software
 distributed under the License is distributed on an "AS IS" BASIS,
 WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
 See the License for the specific language governing permissions and
 limitations under the License.
 /


**起始版本：** 6

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为6。

**废弃版本：** -1

<!--Device-unnamed-declare namespace intl--><!--Device-unnamed-declare namespace intl-End-->

**系统能力：** SystemCapability.Global.I18n

## 汇总

### 类

| 名称 | 说明 |
| --- | --- |
| [Collator](arkts-localization-intl-collator-c.md) | 提供字符串排序的能力。 |
| [DateTimeFormat](arkts-localization-intl-datetimeformat-c.md) | 提供日期格式化的能力。 |
| [Locale](arkts-localization-intl-locale-c.md) | 区域信息 |
| [NumberFormat](arkts-localization-intl-numberformat-c.md) | 提供标准的数字格式化的能力。 |
| [PluralRules](arkts-localization-intl-pluralrules-c.md) | 提供获取单复数类型的能力。 |
| [RelativeTimeFormat](arkts-localization-intl-relativetimeformat-c.md) | 提供相对时间格式化的能力。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [CollatorOptions](arkts-localization-intl-collatoroptions-i.md) | 创建排序对象时可设置的配置项。 从API version 9开始，CollatorOptions中的属性改为可选。 |
| [DateTimeOptions](arkts-localization-intl-datetimeoptions-i.md) | 时间日期格式化时可设置的配置项。从API version 9开始，DateTimeOptions的属性由必填改为可选。 |
| [LocaleOptions](arkts-localization-intl-localeoptions-i.md) | > 从API version 6开始支持，从API version 20开始废弃，以calendar为例， > 区域初始化配置项。从API version 9开始，LocaleOptions属性由必填改为可选。 |
| [NumberOptions](arkts-localization-intl-numberoptions-i.md) | 创建数字格式化对象时可设置的配置项。从API version 9开始，NumberOptions的属性由必填改为可选。 |
| [PluralRulesOptions](arkts-localization-intl-pluralrulesoptions-i.md) | 创建单复数对象时可设置的配置项。从API version 9开始，PluralRulesOptions的属性由必填改为可选。 |
| [RelativeTimeFormatInputOptions](arkts-localization-intl-relativetimeformatinputoptions-i.md) | 创建相对时间格式化对象时可设置的配置项。 从API version 9开始，RelativeTimeFormatInputOptions中的属性改为可选。 |
| [RelativeTimeFormatResolvedOptions](arkts-localization-intl-relativetimeformatresolvedoptions-i.md) | 相对时间格式化对象的格式化配置项。 |

