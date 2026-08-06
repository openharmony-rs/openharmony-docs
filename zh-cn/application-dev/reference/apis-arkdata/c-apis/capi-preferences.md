# Preferences

## 概述

用户首选项为应用提供Key-Value键值型的数据处理能力，支持应用持久化轻量级数据，并对其修改和查询。数据存储采用键值对形式，键为字符串类型，值可为数字、字符串、布尔类型、数组、Uint8Array、object或bigint。

**起始版本：** 13
## 文件汇总

| 名称 | 描述 |
| -- | -- |
| [oh_preferences_value.h](capi-oh-preferences-value-h.md) | 提供访问Preferences值（PreferencesValue）对象的接口、枚举类型与数据结构。 |
| [oh_preferences.h](capi-oh-preferences-h.md) | 提供访问Preferences对象的接口与数据结构。 |
| [oh_preferences_err_code.h](capi-oh-preferences-err-code-h.md) | 声明首选项模块统一使用的错误码信息。 |
| [oh_preferences_option.h](capi-oh-preferences-option-h.md) | 提供访问Preferences配置选项（PreferencesOption）的接口与数据结构。 |
