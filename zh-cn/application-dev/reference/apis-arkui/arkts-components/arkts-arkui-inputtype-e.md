# InputType

单行文本输入框类型。

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

<!--Device-unnamed-declare enum InputType--><!--Device-unnamed-declare enum InputType-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## Normal

```TypeScript
Normal
```

基本输入模式，无特殊限制。 内联输入风格只支持InputType.Normal类型。

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-InputType-Normal--><!--Device-InputType-Normal-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## Number

```TypeScript
Number
```

纯数字输入模式。 不支持负数、小数。

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-InputType-Number--><!--Device-InputType-Number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## PhoneNumber

```TypeScript
PhoneNumber
```

电话号码输入模式。 支持输入数字、空格、+ 、-、*、#、(、)，长度不限。

**起始版本：** 9

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为9。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-InputType-PhoneNumber--><!--Device-InputType-PhoneNumber-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## Email

```TypeScript
Email
```

邮箱地址输入模式。 支持数字、字母、下划线、小数点、!、#、\$、%、&、'、"、*、+、-、/、=、?、^、`、{、|、}、~，以及@字符（只能存在一个@字符）。

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-InputType-Email--><!--Device-InputType-Email-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## Password

```TypeScript
Password
```

密码输入模式。 默认输入文字短暂显示后变成圆点。从API version 12开始，PC/2in1设备上输入文字直接显示为圆点。 TV设备上输入框末尾默认不显示小眼睛图标，其他设备输入框末尾默认显示小眼睛图标。 密码输入模式中，[decoration]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_、[showUnderline]\_\_\_JSDOC\_LINK\_DESC\_USD\_1\_\_\_、 [lineHeight]\_\_\_JSDOC\_LINK\_DESC\_USD\_2\_\_\_不生效。 在已启用密码保险箱的情况下，支持用户名、密码的自动保存和自动填充。

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-InputType-Password--><!--Device-InputType-Password-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## NUMBER_PASSWORD

```TypeScript
NUMBER_PASSWORD = 8
```

纯数字密码输入模式。 默认输入文字短暂显示后变成圆点。从API version 12开始，PC/2in1设备上输入文字直接显示为圆点。 TV设备上输入框末尾默认不显示小眼睛图标，其他设备输入框末尾默认显示小眼睛图标。 密码输入模式中，[decoration]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_、[showUnderline]\_\_\_JSDOC\_LINK\_DESC\_USD\_1\_\_\_、 [lineHeight]\_\_\_JSDOC\_LINK\_DESC\_USD\_2\_\_\_、[fontFeature]\_\_\_JSDOC\_LINK\_DESC\_USD\_3\_\_\_不生效。在已启用密码保险箱的 情况下，支持用户名、密码的自动保存和自动填充。

**起始版本：** 11

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为11。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-InputType-NUMBER_PASSWORD = 8--><!--Device-InputType-NUMBER_PASSWORD = 8-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## USER_NAME

```TypeScript
USER_NAME = 10
```

用户名输入模式，无特殊限制。 在已启用密码保险箱的情况下，支持用户名的自动保存和自动填充，用于配合[InputType.Password]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_、 [InputType.NUMBER\_PASSWORD]\_\_\_JSDOC\_LINK\_DESC\_USD\_1\_\_\_、[InputType.NEW\_PASSWORD]\_\_\_JSDOC\_LINK\_DESC\_USD\_2\_\_\_完成用户名密码配对填充。

**起始版本：** 11

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为11。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-InputType-USER_NAME = 10--><!--Device-InputType-USER_NAME = 10-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## NEW_PASSWORD

```TypeScript
NEW_PASSWORD = 11
```

新密码输入模式。 默认输入文字短暂显示后变成圆点。从API version 12开始，PC/2in1设备上输入文字直接显示为圆点。 TV设备上输入框末尾默认不显示小眼睛图标，其他设备输入框末尾默认显示小眼睛图标。 密码输入模式中，[decoration]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_、[showUnderline]\_\_\_JSDOC\_LINK\_DESC\_USD\_1\_\_\_、 [lineHeight]\_\_\_JSDOC\_LINK\_DESC\_USD\_2\_\_\_、[fontFeature]\_\_\_JSDOC\_LINK\_DESC\_USD\_3\_\_\_不生效。在已启用密码保险箱的 情况下，支持自动生成新密码。

**起始版本：** 11

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为11。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-InputType-NEW_PASSWORD = 11--><!--Device-InputType-NEW_PASSWORD = 11-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## NUMBER_DECIMAL

```TypeScript
NUMBER_DECIMAL = 12
```

带小数点的数字输入模式。 支持数字，小数点（只能存在一个小数点）。不支持负数（包括负数整数和负数小数）。若需支持负数输入，请使用[inputFilter]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_属性实现负数过滤。

**起始版本：** 11

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为11。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-InputType-NUMBER_DECIMAL = 12--><!--Device-InputType-NUMBER_DECIMAL = 12-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## URL

```TypeScript
URL = 13
```

带URL的输入模式，无特殊限制。

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-InputType-URL = 13--><!--Device-InputType-URL = 13-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## ONE_TIME_CODE

```TypeScript
ONE_TIME_CODE = 14
```

验证码输入模式，无特殊限制。

**起始版本：** 20

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为20。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-InputType-ONE_TIME_CODE = 14--><!--Device-InputType-ONE_TIME_CODE = 14-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

