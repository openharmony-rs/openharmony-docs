# text_input.h

## 概述

Defines a set of TextInput enum and interface.

**库：** libace_ndk.z.so

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 12

**相关模块：** [ArkUI_NativeModule](capi-arkui-nativemodule.md)

## 汇总

### 枚举

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [ArkUI_TextInputType](#arkui_textinputtype) | ArkUI_TextInputType | 定义单行文本输入法类型枚举值。 |
| [ArkUI_CancelButtonStyle](#arkui_cancelbuttonstyle) | ArkUI_CancelButtonStyle | 定义清除按钮样式枚举值。 |
| [ArkUI_TextInputContentType](#arkui_textinputcontenttype) | ArkUI_TextInputContentType | 定义自动填充类型。 |
| [ArkUI_TextInputStyle](#arkui_textinputstyle) | ArkUI_TextInputStyle | 定义输入框风格。 |

## 枚举类型说明

### ArkUI_TextInputType

```c
enum ArkUI_TextInputType
```

**描述**

定义单行文本输入法类型枚举值。

**起始版本：** 12

| 枚举项 | 描述 |
| -- | -- |
| ARKUI_TEXTINPUT_TYPE_NORMAL = 0 | 基本输入模式。 |
| ARKUI_TEXTINPUT_TYPE_NUMBER = 2 | 纯数字模式。 |
| ARKUI_TEXTINPUT_TYPE_PHONE_NUMBER = 3 | 电话号码输入模式。 |
| ARKUI_TEXTINPUT_TYPE_EMAIL = 5 | 邮箱地址输入模式。 |
| ARKUI_TEXTINPUT_TYPE_PASSWORD = 7 | 密码输入模式。 |
| ARKUI_TEXTINPUT_TYPE_NUMBER_PASSWORD = 8 | 纯数字密码输入模式。 |
| ARKUI_TEXTINPUT_TYPE_SCREEN_LOCK_PASSWORD = 9 | 锁屏应用密码输入模式。 |
| ARKUI_TEXTINPUT_TYPE_USER_NAME = 10 | 用户名输入模式。 |
| ARKUI_TEXTINPUT_TYPE_NEW_PASSWORD = 11 | 新密码输入模式。 |
| ARKUI_TEXTINPUT_TYPE_NUMBER_DECIMAL = 12 | 带小数点的数字输入模式。 |
| ARKUI_TEXTINPUT_TYPE_ONE_TIME_CODE = 14 |  |

### ArkUI_CancelButtonStyle

```c
enum ArkUI_CancelButtonStyle
```

**描述**

定义清除按钮样式枚举值。

**起始版本：** 12

| 枚举项 | 描述 |
| -- | -- |
| ARKUI_CANCELBUTTON_STYLE_CONSTANT = 0 | 清除按钮常显样式。 |
| ARKUI_CANCELBUTTON_STYLE_INVISIBLE | 清除按钮常隐样式。 |
| ARKUI_CANCELBUTTON_STYLE_INPUT | 清除按钮输入样式。 |

### ArkUI_TextInputContentType

```c
enum ArkUI_TextInputContentType
```

**描述**

定义自动填充类型。

**起始版本：** 12

| 枚举项 | 描述 |
| -- | -- |
| ARKUI_TEXTINPUT_CONTENT_TYPE_USER_NAME = 0 | 【用户名】在已启用密码保险箱的情况下，支持用户名的自动保存和自动填充。 |
| ARKUI_TEXTINPUT_CONTENT_TYPE_PASSWORD | 【密码】在已启用密码保险箱的情况下，支持密码的自动保存和自动填充。 |
| ARKUI_TEXTINPUT_CONTENT_TYPE_NEW_PASSWORD | 【新密码】在已启用密码保险箱的情况下，支持自动生成新密码。 |
| ARKUI_TEXTINPUT_CONTENT_TYPE_FULL_STREET_ADDRESS | 【详细地址】在已启用情景化自动填充的情况下，支持详细地址的自动保存和自动填充。 |
| ARKUI_TEXTINPUT_CONTENT_TYPE_HOUSE_NUMBER | 【门牌号】在已启用情景化自动填充的情况下，支持门牌号的自动保存和自动填充。 |
| ARKUI_TEXTINPUT_CONTENT_TYPE_DISTRICT_ADDRESS | 【区/县】在已启用情景化自动填充的情况下，支持区/县的自动保存和自动填充。 |
| ARKUI_TEXTINPUT_CONTENT_TYPE_CITY_ADDRESS | 【市】在已启用情景化自动填充的情况下，支持市的自动保存和自动填充。 |
| ARKUI_TEXTINPUT_CONTENT_TYPE_PROVINCE_ADDRESS | 【省】在已启用情景化自动填充的情况下，支持省的自动保存和自动填充。 |
| ARKUI_TEXTINPUT_CONTENT_TYPE_COUNTRY_ADDRESS | 【国家】在已启用情景化自动填充的情况下，支持国家的自动保存和自动填充。 |
| ARKUI_TEXTINPUT_CONTENT_TYPE_PERSON_FULL_NAME | 【姓名】在已启用情景化自动填充的情况下，支持姓名的自动保存和自动填充。 |
| ARKUI_TEXTINPUT_CONTENT_TYPE_PERSON_LAST_NAME | 【姓氏】在已启用情景化自动填充的情况下，支持姓氏的自动保存和自动填充。 |
| ARKUI_TEXTINPUT_CONTENT_TYPE_PERSON_FIRST_NAME | 【名字】在已启用情景化自动填充的情况下，支持名字的自动保存和自动填充。 |
| ARKUI_TEXTINPUT_CONTENT_TYPE_PHONE_NUMBER | 【手机号】在已启用情景化自动填充的情况下，支持手机号的自动保存和自动填充。 |
| ARKUI_TEXTINPUT_CONTENT_TYPE_PHONE_COUNTRY_CODE | 【国家代码】在已启用情景化自动填充的情况下，支持国家代码的自动保存和自动填充。 |
| ARKUI_TEXTINPUT_CONTENT_TYPE_FULL_PHONE_NUMBER | 【包含国家代码的手机号】在已启用情景化自动填充的情况下，支持包含国家代码的手机号的自动保存和自动填充。 |
| ARKUI_TEXTINPUT_CONTENT_EMAIL_ADDRESS | 【邮箱地址】在已启用情景化自动填充的情况下，支持邮箱地址的自动保存和自动填充。 |
| ARKUI_TEXTINPUT_CONTENT_TYPE_BANK_CARD_NUMBER | 【银行卡号】在已启用情景化自动填充的情况下，支持银行卡号的自动保存和自动填充。 |
| ARKUI_TEXTINPUT_CONTENT_TYPE_ID_CARD_NUMBER | 【身份证号】在已启用情景化自动填充的情况下，支持身份证号的自动保存和自动填充。 |
| ARKUI_TEXTINPUT_CONTENT_TYPE_NICKNAME | 【昵称】在已启用情景化自动填充的情况下，支持昵称的自动保存和自动填充。 |
| ARKUI_TEXTINPUT_CONTENT_TYPE_DETAIL_INFO_WITHOUT_STREET | 【无街道地址】在已启用情景化自动填充的情况下，支持无街道地址的自动保存和自动填充。 |
| ARKUI_TEXTINPUT_CONTENT_TYPE_FORMAT_ADDRESS | 【标准地址】在已启用情景化自动填充的情况下，支持标准地址的自动保存和自动填充。 |
| ARKUI_TEXTINPUT_CONTENT_TYPE_PASSPORT_NUMBER |  |
| ARKUI_TEXTINPUT_CONTENT_TYPE_VALIDITY |  |
| ARKUI_TEXTINPUT_CONTENT_TYPE_ISSUE_AT |  |
| ARKUI_TEXTINPUT_CONTENT_TYPE_ORGANIZATION |  |
| ARKUI_TEXTINPUT_CONTENT_TYPE_TAX_ID |  |
| ARKUI_TEXTINPUT_CONTENT_TYPE_ADDRESS_CITY_AND_STATE |  |
| ARKUI_TEXTINPUT_CONTENT_TYPE_FLIGHT_NUMBER |  |
| ARKUI_TEXTINPUT_CONTENT_TYPE_LICENSE_NUMBER |  |
| ARKUI_TEXTINPUT_CONTENT_TYPE_LICENSE_FILE_NUMBER |  |
| ARKUI_TEXTINPUT_CONTENT_TYPE_LICENSE_PLATE |  |
| ARKUI_TEXTINPUT_CONTENT_TYPE_ENGINE_NUMBER |  |
| ARKUI_TEXTINPUT_CONTENT_TYPE_LICENSE_CHASSIS_NUMBER |  |

### ArkUI_TextInputStyle

```c
enum ArkUI_TextInputStyle
```

**描述**

定义输入框风格。

**起始版本：** 12

| 枚举项 | 描述 |
| -- | -- |
| ARKUI_TEXTINPUT_STYLE_DEFAULT = 0 | 默认风格，光标宽1.5vp，光标高度与文本选中底板高度和字体大小相关。 |
| ARKUI_TEXTINPUT_STYLE_INLINE | 内联输入风格。文本选中底板高度与输入框高度相同。 |


