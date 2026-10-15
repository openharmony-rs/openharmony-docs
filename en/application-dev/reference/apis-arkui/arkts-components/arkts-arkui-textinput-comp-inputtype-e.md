# InputType

```TypeScript
declare enum InputType
```

Type of the single-line text input box.

**Since:** 7

<!--Device-unnamed-declare enum InputType--><!--Device-unnamed-declare enum InputType-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Email

```TypeScript
Email
```

Email address input mode.

Supports digits, letters, underscores, decimal points, !, #, $, %, &, ', ", *, +, -, /, =, ?, ^,`, {, |, }, ~, and @ (only one is supported). The email address format must comply with the basic specification: the part before the @ character is the username, and the part after the @ character is the domain name.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-InputType-Email--><!--Device-InputType-Email-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## NEW_PASSWORD

```TypeScript
NEW_PASSWORD = 11
```

New password input mode.

By default, the entered text is briefly displayed and then becomes dots. Since API version 12, the entered text is directly displayed as dots on PC/2-in-1 devices.

On TV devices, the eye icon is not displayed at the end of the input box by default; on other devices, the eye icon is displayed at the end of the input box by default.

In password input mode, [decoration](arkts-arkui-textinput-comp-attribute.md#decoration), [showUnderline](arkts-arkui-textinput-comp-attribute.md#showunderline), [lineHeight](arkts-arkui-textinput-comp-attribute.md#lineheight), and [fontFeature](arkts-arkui-textinput-comp-attribute.md#fontfeature) do not take effect. When the password vault is enabled, automatic generation of a new password is supported.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-InputType-NEW_PASSWORD = 11--><!--Device-InputType-NEW_PASSWORD = 11-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Normal

```TypeScript
Normal
```

Basic input mode with no special restrictions.

The inline input style supports only the InputType.Normal type.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-InputType-Normal--><!--Device-InputType-Normal-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Number

```TypeScript
Number
```

Pure number input mode.

Negative numbers and decimals are not supported.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-InputType-Number--><!--Device-InputType-Number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## NUMBER_DECIMAL

```TypeScript
NUMBER_DECIMAL = 12
```

Number input mode with a decimal point.

Supports digits and a decimal point (only one decimal point is allowed). Negative numbers (including negative integers and negative decimals) are not supported. To support negative number input, use the [inputFilter](arkts-arkui-textinput-comp-attribute.md#inputfilter) attribute to implement negative number filtering.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-InputType-NUMBER_DECIMAL = 12--><!--Device-InputType-NUMBER_DECIMAL = 12-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## NUMBER_PASSWORD

```TypeScript
NUMBER_PASSWORD = 8
```

Pure number password input mode.

By default, the entered text is briefly displayed and then becomes dots. Since API version 12, the entered text is directly displayed as dots on PC/2-in-1 devices.

On TV devices, the eye icon is not displayed at the end of the input box by default; on other devices, the eye icon is displayed at the end of the input box by default.

In password input mode, [decoration](arkts-arkui-textinput-comp-attribute.md#decoration), [showUnderline](arkts-arkui-textinput-comp-attribute.md#showunderline), [lineHeight](arkts-arkui-textinput-comp-attribute.md#lineheight), and [fontFeature](arkts-arkui-textinput-comp-attribute.md#fontfeature) do not take effect. When the password vault is enabled, auto- save and auto-fill of the username and password are supported.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-InputType-NUMBER_PASSWORD = 8--><!--Device-InputType-NUMBER_PASSWORD = 8-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## ONE_TIME_CODE

```TypeScript
ONE_TIME_CODE = 14
```

Verification code input mode with no special restrictions. In this mode, the system input method is pulled up by default after the component gains focus.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

<!--Device-InputType-ONE_TIME_CODE = 14--><!--Device-InputType-ONE_TIME_CODE = 14-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Password

```TypeScript
Password
```

Password input mode.

By default, the entered text is briefly displayed and then becomes dots. Since API version 12, the entered text is directly displayed as dots on PC/2-in-1 devices.

On TV devices, the eye icon is not displayed at the end of the input box by default; on other devices, the eye icon is displayed at the end of the input box by default.

In password input mode, [decoration](arkts-arkui-textinput-comp-attribute.md#decoration), [showUnderline](arkts-arkui-textinput-comp-attribute.md#showunderline), [lineHeight](arkts-arkui-textinput-comp-attribute.md#lineheight), and [fontFeature](arkts-arkui-textinput-comp-attribute.md#fontfeature) do not take effect.

When the password vault is enabled, auto-save and auto-fill of the username and password are supported.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-InputType-Password--><!--Device-InputType-Password-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## PhoneNumber

```TypeScript
PhoneNumber
```

Phone number input mode.

Supports digits, spaces, +, -, *, #, (, and ), with no length limit.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-InputType-PhoneNumber--><!--Device-InputType-PhoneNumber-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## URL

```TypeScript
URL = 13
```

Input mode with a URL, with no special restrictions.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-InputType-URL = 13--><!--Device-InputType-URL = 13-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## USER_NAME

```TypeScript
USER_NAME = 10
```

Username input mode with no special restrictions.

When the password vault is enabled, auto-save and auto-fill of the username are supported, which are used together with [InputType.Password](arkts-arkui-textinput-comp-inputtype-e.md), [InputType.NUMBER_PASSWORD](arkts-arkui-textinput-comp-inputtype-e.md), and [InputType.NEW_PASSWORD](arkts-arkui-textinput-comp-inputtype-e.md) to complete paired filling of the username and password.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-InputType-USER_NAME = 10--><!--Device-InputType-USER_NAME = 10-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
