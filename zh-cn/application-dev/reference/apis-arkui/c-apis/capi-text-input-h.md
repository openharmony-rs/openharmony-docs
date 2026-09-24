# text_input.h

## 概述

定义TextInput相关的枚举。支持多种输入类型配置（包括文本、数字、密码、邮箱、电话号码等）、清除按钮样式定制、自动填充内容类型设置和输入框风格选择，适用于登录注册、表单填写、搜索输入等需要用户交互输入的场景， 帮助开发者快速实现符合业务需求的单行文本输入功能。

**库：** libace_ndk.z.so

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 12

**相关模块：** [ArkUI_NativeModule](capi-arkui-nativemodule.md)

## 汇总

### 枚举

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [ArkUI_TextInputType](#arkui_textinputtype) | ArkUI_TextInputType | 定义单行文本输入类型枚举值。 |
| [ArkUI_CancelButtonStyle](#arkui_cancelbuttonstyle) | ArkUI_CancelButtonStyle | 定义清除按钮样式枚举值。 |
| [ArkUI_TextInputContentType](#arkui_textinputcontenttype) | ArkUI_TextInputContentType | 定义自动填充类型。 |
| [ArkUI_TextInputStyle](#arkui_textinputstyle) | ArkUI_TextInputStyle | 定义输入框风格。 |

## 枚举类型说明

### ArkUI_TextInputType

```c
enum ArkUI_TextInputType
```

**描述：**

定义单行文本输入类型枚举值。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 12

| 枚举项 | 描述 |
| -- | -- |
| ARKUI_TEXTINPUT_TYPE_NORMAL = 0 | 基本输入模式，无特殊限制。 |
| ARKUI_TEXTINPUT_TYPE_NUMBER = 2 | 纯数字输入模式。 |
| ARKUI_TEXTINPUT_TYPE_PHONE_NUMBER = 3 | 电话号码输入模式。<br>支持输入数字、空格、+ 、-、*、#、(、)，长度不限。 |
| ARKUI_TEXTINPUT_TYPE_PASSWORD = 7 | 密码输入模式。<br>默认输入文字短暂显示后变成圆点。从API version 12开始，PC/2in1设备上输入文字直接显示为圆点。<br>TV设备上输入框末尾默认不显示小眼睛图标，其他设备输入框末尾默认显示小眼睛图标。 |
| ARKUI_TEXTINPUT_TYPE_NUMBER_PASSWORD = 8 | 纯数字密码输入模式。<br>默认输入文字短暂显示后变成圆点。从API version 12开始，PC/2in1设备上输入文字直接显示为圆点。<br>TV设备上输入框末尾默认不显示小眼睛图标， 其他设备输入框末尾默认显示小眼睛图标。 |
| ARKUI_TEXTINPUT_TYPE_SCREEN_LOCK_PASSWORD = 9 | 锁屏应用密码输入模式。支持输入数字、字母、下划线、空格、特殊字符。密码显示小眼睛图标并且默认会将文字变成圆点，从API version 12开始，Wearable设备上输入文字直接显示为圆点。密码输入模式不支持下划线样式。 |
| ARKUI_TEXTINPUT_TYPE_USER_NAME = 10 | 用户名输入模式，无特殊限制。<br>在已启用密码保险箱的情况下，支持用户名的自动保存和自动填充。 |
| ARKUI_TEXTINPUT_TYPE_NEW_PASSWORD = 11 | 新密码输入模式。<br>默认输入文字短暂显示后变成圆点。从API version 12开始，PC/2in1设备上输入文字直接显示为圆点。<br>TV设备上输入框末尾默认不显示小眼睛图标，其他设备输入框末尾默认显示小眼睛图标。 |
| ARKUI_TEXTINPUT_TYPE_NUMBER_DECIMAL = 12 | 带小数点的数字输入模式。<br>支持数字，小数点（只能存在一个小数点）。不支持负数（包括负数整数和负数小数）。 |
| ARKUI_TEXTINPUT_TYPE_ONE_TIME_CODE = 14 |  |

### ArkUI_CancelButtonStyle

```c
enum ArkUI_CancelButtonStyle
```

**描述：**

定义清除按钮样式枚举值。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 12

| 枚举项 | 描述 |
| -- | -- |
| ARKUI_CANCELBUTTON_STYLE_CONSTANT = 0 | 清除按钮常显样式。适用于需要始终显示清除按钮的场景，如搜索框等需要频繁清除内容的输入框。 |
| ARKUI_CANCELBUTTON_STYLE_INVISIBLE | 清除按钮常隐样式。适用于不需要显示清除按钮的场景。 |
| ARKUI_CANCELBUTTON_STYLE_INPUT | 清除按钮输入样式。即在有输入内容时显示清除按钮，无输入内容时隐藏清除按钮。适用于按需显示清除按钮的场景，为推荐使用的默认行为。 |

### ArkUI_TextInputContentType

```c
enum ArkUI_TextInputContentType
```

**描述：**

定义自动填充类型。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

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
| ARKUI_TEXTINPUT_CONTENT_TYPE_LICENSE_CHASSIS_NUMBER | 【车架号】暂不支持自动保存和自动填充。 |

### ArkUI_TextInputStyle

```c
enum ArkUI_TextInputStyle
```

**描述：**

定义输入框风格。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 12

| 枚举项 | 描述 |
| -- | -- |
| ARKUI_TEXTINPUT_STYLE_DEFAULT = 0 | 默认风格，光标宽度为1.5vp，选中底板高度与字体大小相关。适用于大多数输入框场景。 |
| ARKUI_TEXTINPUT_STYLE_INLINE | 内联输入风格，文本选中底板高度与输入框高度相同。适用于输入框高度固定且需要文本选中底板高度与输入框高度一致的场景，如紧凑布局或内联编辑的输入框。 |


