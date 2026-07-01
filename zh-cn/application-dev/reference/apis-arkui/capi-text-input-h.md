# text_input.h
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @Zhang-Dong-hui-->
<!--Designer: @xiangyuan6-->
<!--Tester: @jiaoaozihao-->
<!--Adviser: @Brilliantry_Rui-->

## 概述

定义TextInput相关的枚举和接口。

**引用文件：** <arkui/text_input.h>

**库：** libace_ndk.z.so

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 12

**相关模块：** [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**相关示例：** <!--RP1-->[native_type_sample](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/ArkUISample/NativeType/native_type_sample)<!--RP1End-->

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
| ARKUI_TEXTINPUT_TYPE_ONE_TIME_CODE = 14 | 验证码输入模式。<br>**起始版本：** 20 |

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
| ARKUI_CANCELBUTTON_STYLE_INVISIBLE = 1 | 清除按钮常隐样式。 |
| ARKUI_CANCELBUTTON_STYLE_INPUT = 2 | 清除按钮输入样式。 |

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
| ARKUI_TEXTINPUT_CONTENT_TYPE_PASSWORD = 1 | 【密码】在已启用密码保险箱的情况下，支持密码的自动保存和自动填充。 |
| ARKUI_TEXTINPUT_CONTENT_TYPE_NEW_PASSWORD = 2 | 【新密码】在已启用密码保险箱的情况下，支持自动生成新密码。 |
| ARKUI_TEXTINPUT_CONTENT_TYPE_FULL_STREET_ADDRESS = 3 | 【详细地址】在已启用情景化自动填充的情况下，支持详细地址的自动保存和自动填充。 |
| ARKUI_TEXTINPUT_CONTENT_TYPE_HOUSE_NUMBER = 4 | 【门牌号】在已启用情景化自动填充的情况下，支持门牌号的自动保存和自动填充。 |
| ARKUI_TEXTINPUT_CONTENT_TYPE_DISTRICT_ADDRESS = 5 | 【区/县】在已启用情景化自动填充的情况下，支持区/县的自动保存和自动填充。 |
| ARKUI_TEXTINPUT_CONTENT_TYPE_CITY_ADDRESS = 6 | 【市】在已启用情景化自动填充的情况下，支持市的自动保存和自动填充。 |
| ARKUI_TEXTINPUT_CONTENT_TYPE_PROVINCE_ADDRESS = 7 | 【省】在已启用情景化自动填充的情况下，支持省的自动保存和自动填充。 |
| ARKUI_TEXTINPUT_CONTENT_TYPE_COUNTRY_ADDRESS = 8 | 【国家】在已启用情景化自动填充的情况下，支持国家的自动保存和自动填充。 |
| ARKUI_TEXTINPUT_CONTENT_TYPE_PERSON_FULL_NAME = 9 | 【姓名】在已启用情景化自动填充的情况下，支持姓名的自动保存和自动填充。 |
| ARKUI_TEXTINPUT_CONTENT_TYPE_PERSON_LAST_NAME = 10 | 【姓氏】在已启用情景化自动填充的情况下，支持姓氏的自动保存和自动填充。 |
| ARKUI_TEXTINPUT_CONTENT_TYPE_PERSON_FIRST_NAME = 11 | 【名字】在已启用情景化自动填充的情况下，支持名字的自动保存和自动填充。 |
| ARKUI_TEXTINPUT_CONTENT_TYPE_PHONE_NUMBER = 12 | 【手机号】在已启用情景化自动填充的情况下，支持手机号的自动保存和自动填充。 |
| ARKUI_TEXTINPUT_CONTENT_TYPE_PHONE_COUNTRY_CODE = 13 | 【国家代码】在已启用情景化自动填充的情况下，支持国家代码的自动保存和自动填充。 |
| ARKUI_TEXTINPUT_CONTENT_TYPE_FULL_PHONE_NUMBER = 14 | 【包含国家代码的手机号】在已启用情景化自动填充的情况下，支持包含国家代码的手机号的自动保存和自动填充。 |
| ARKUI_TEXTINPUT_CONTENT_EMAIL_ADDRESS = 15 | 【邮箱地址】在已启用情景化自动填充的情况下，支持邮箱地址的自动保存和自动填充。 |
| ARKUI_TEXTINPUT_CONTENT_TYPE_BANK_CARD_NUMBER = 16 | 【银行卡号】在已启用情景化自动填充的情况下，支持银行卡号的自动保存和自动填充。 |
| ARKUI_TEXTINPUT_CONTENT_TYPE_ID_CARD_NUMBER = 17 | 【身份证号】在已启用情景化自动填充的情况下，支持身份证号的自动保存和自动填充。 |
| ARKUI_TEXTINPUT_CONTENT_TYPE_NICKNAME = 18 | 【昵称】在已启用情景化自动填充的情况下，支持昵称的自动保存和自动填充。 |
| ARKUI_TEXTINPUT_CONTENT_TYPE_DETAIL_INFO_WITHOUT_STREET = 19 | 【无街道地址】在已启用情景化自动填充的情况下，支持无街道地址的自动保存和自动填充。 |
| ARKUI_TEXTINPUT_CONTENT_TYPE_FORMAT_ADDRESS = 20 | 【标准地址】在已启用情景化自动填充的情况下，支持标准地址的自动保存和自动填充。 |
| ARKUI_TEXTINPUT_CONTENT_TYPE_PASSPORT_NUMBER = 21 | 【护照号】在已启用情景化自动填充的情况下，支持护照号的自动保存和自动填充。<br>**起始版本：** 18 |
| ARKUI_TEXTINPUT_CONTENT_TYPE_VALIDITY = 22 | 【护照有效期】在已启用情景化自动填充的情况下，支持护照有效期的自动保存和自动填充。<br>**起始版本：** 18 |
| ARKUI_TEXTINPUT_CONTENT_TYPE_ISSUE_AT = 23 | 【护照签发地】在已启用情景化自动填充的情况下，支持护照签发地的自动保存和自动填充。<br>**起始版本：** 18 |
| ARKUI_TEXTINPUT_CONTENT_TYPE_ORGANIZATION = 24 | 【发票抬头名称】在已启用情景化自动填充的情况下，支持发票抬头名称的自动保存和自动填充。<br>**起始版本：** 18 |
| ARKUI_TEXTINPUT_CONTENT_TYPE_TAX_ID = 25 | 【税号】在已启用情景化自动填充的情况下，支持税号的自动保存和自动填充。<br>**起始版本：** 18 |
| ARKUI_TEXTINPUT_CONTENT_TYPE_ADDRESS_CITY_AND_STATE = 26 | 【所在地区】在已启用情景化自动填充的情况下，支持所在地区的自动保存和自动填充。<br>**起始版本：** 18 |
| ARKUI_TEXTINPUT_CONTENT_TYPE_FLIGHT_NUMBER = 27 | 【航班号】暂不支持自动保存和自动填充。<br>**起始版本：** 18 |
| ARKUI_TEXTINPUT_CONTENT_TYPE_LICENSE_NUMBER = 28 | 【驾驶证号】暂不支持自动保存和自动填充。<br>**起始版本：** 18 |
| ARKUI_TEXTINPUT_CONTENT_TYPE_LICENSE_FILE_NUMBER = 29 | 【驾驶证档案编号】暂不支持自动保存和自动填充。<br>**起始版本：** 18 |
| ARKUI_TEXTINPUT_CONTENT_TYPE_LICENSE_PLATE = 30 | 【车牌号】在已启用情景化自动填充的情况下，支持车牌号的自动保存和自动填充。<br>**起始版本：** 18 |
| ARKUI_TEXTINPUT_CONTENT_TYPE_ENGINE_NUMBER = 31 | 【行驶证发动机号】暂不支持自动保存和自动填充。<br>**起始版本：** 18 |
| ARKUI_TEXTINPUT_CONTENT_TYPE_LICENSE_CHASSIS_NUMBER = 32 | 【车牌识别号】暂不支持自动保存和自动填充。<br>**起始版本：** 18 |

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
| ARKUI_TEXTINPUT_STYLE_INLINE = 1 | 内联输入风格。文本选中底板高度与输入框高度相同。 |


