# text_area.h
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @Zhang-Dong-hui-->
<!--Designer: @xiangyuan6-->
<!--Tester: @jiaoaozihao-->
<!--Adviser: @Brilliantry_Rui-->

## 概述

定义TextArea相关的枚举和接口。

**引用文件：** <arkui/node_attributes/text_area.h>

**库：** libace_ndk.z.so

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 12

**相关模块：** [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**相关示例：** <!--RP1-->[native_type_sample](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/ArkUISample/NativeType/native_type_sample)<!--RP1End-->

## 汇总

### 枚举

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [ArkUI_TextAreaType](#arkui_textareatype) | ArkUI_TextAreaType | 定义多行文本输入法类型枚举值。 |

## 枚举类型说明

### ArkUI_TextAreaType

```c
enum ArkUI_TextAreaType
```

**描述**

定义多行文本输入法类型枚举值。

**起始版本：** 12

| 枚举项 | 描述 |
| -- | -- |
| ARKUI_TEXTAREA_TYPE_NORMAL = 0 | 基本输入模式。 |
| ARKUI_TEXTAREA_TYPE_NUMBER = 2 | 纯数字模式。 |
| ARKUI_TEXTAREA_TYPE_PHONE_NUMBER = 3 | 电话号码输入模式。 |
| ARKUI_TEXTAREA_TYPE_EMAIL = 5 | 邮箱地址输入模式。 |
| ARKUI_TEXTAREA_TYPE_ONE_TIME_CODE = 14 | 验证码输入模式。<br>**起始版本：** 20 |


