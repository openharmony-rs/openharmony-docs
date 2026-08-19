# InputType

单行文本输入框类型。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare enum InputType--><!--Device-unnamed-export declare enum InputType-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## Normal

```TypeScript
Normal = 0
```

基本输入模式，无特殊限制。 内联输入风格只支持InputType.Normal类型。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-InputType-Normal = 0--><!--Device-InputType-Normal = 0-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## NUMBER

```TypeScript
NUMBER = 2
```

纯数字输入模式。 不支持负数、小数。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-InputType-NUMBER = 2--><!--Device-InputType-NUMBER = 2-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## PhoneNumber

```TypeScript
PhoneNumber = 3
```

电话号码输入模式。 支持输入数字、空格、+ 、-、*、#、(、)，长度不限。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-InputType-PhoneNumber = 3--><!--Device-InputType-PhoneNumber = 3-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## Email

```TypeScript
Email = 5
```

邮箱地址输入模式。 支持数字、字母、下划线、小数点、!、#、\$、%、&、'、"、*、+、-、/、=、?、^、`、{、|、}、~，以及@字符（只能存在一个@字符）。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-InputType-Email = 5--><!--Device-InputType-Email = 5-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## Password

```TypeScript
Password = 7
```

密码输入模式。 默认输入文字短暂显示后变成圆点。从API version 12开始，PC/2in1设备上输入文字直接显示为圆点。 TV设备上输入框末尾默认不显示小眼睛图标，其他设备输入框末尾默认显示小眼睛图标。 密码输入模式中，decoration、showUnderline、lineHeight不生效。 在已启用密码保险箱的情况下，支持用户名、密码的自动保存和自动填充。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-InputType-Password = 7--><!--Device-InputType-Password = 7-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## NUMBER_PASSWORD

```TypeScript
NUMBER_PASSWORD = 8
```

纯数字密码输入模式。 默认输入文字短暂显示后变成圆点。从API version 12开始，PC/2in1设备上输入文字直接显示为圆点。 TV设备上输入框末尾默认不显示小眼睛图标，其他设备输入框末尾默认显示小眼睛图标。 密码输入模式不支持下划线样式。在已启用密码保险箱的情况下，支持用户名、密码的自动保存和自动填充。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-InputType-NUMBER_PASSWORD = 8--><!--Device-InputType-NUMBER_PASSWORD = 8-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## USER_NAME

```TypeScript
USER_NAME = 10
```

用户名输入模式，无特殊限制。 在已启用密码保险箱的情况下，支持用户名、密码的自动保存和自动填充。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-InputType-USER_NAME = 10--><!--Device-InputType-USER_NAME = 10-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## NEW_PASSWORD

```TypeScript
NEW_PASSWORD = 11
```

新密码输入模式，无特殊限制。 默认输入文字短暂显示后变成圆点。从API version 12开始，PC/2in1设备上输入文字直接显示为圆点。 TV设备上输入框末尾默认不显示小眼睛图标，其他设备输入框末尾默认显示小眼睛图标。 在已启用密码保险箱的情况下，支持自动生成新密码。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-InputType-NEW_PASSWORD = 11--><!--Device-InputType-NEW_PASSWORD = 11-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## NUMBER_DECIMAL

```TypeScript
NUMBER_DECIMAL = 12
```

带小数点的数字输入模式。 支持数字，小数点（只能存在一个小数点）。不支持负数小数，负数小数的数字输入模式请使用inputFilter实现。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-InputType-NUMBER_DECIMAL = 12--><!--Device-InputType-NUMBER_DECIMAL = 12-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## URL

```TypeScript
URL = 13
```

带URL的输入模式，无特殊限制。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-InputType-URL = 13--><!--Device-InputType-URL = 13-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## ONE_TIME_CODE

```TypeScript
ONE_TIME_CODE = 14
```

验证码输入模式，无特殊限制。

**起始版本：** 24

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为24。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-InputType-ONE_TIME_CODE = 14--><!--Device-InputType-ONE_TIME_CODE = 14-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

