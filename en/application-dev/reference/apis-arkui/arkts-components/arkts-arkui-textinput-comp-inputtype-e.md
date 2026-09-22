# InputType

```TypeScript
declare enum InputType
```

Sets the single-line text box type.

**Since:** 7

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Normal

```TypeScript
Normal
```

Normal input mode. In this mode, there is no special restriction on the input characters.

The inline style supports only the **InputType.Normal** type.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Number

```TypeScript
Number
```

Digit input mode.

Negative numbers and decimals are not supported.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## PhoneNumber

```TypeScript
PhoneNumber
```

Phone number input mode.

In this mode, the following characters are allowed: digits, spaces, plus signs (+), hyphens (-), asterisks (*), and number signs (#), opening parentheses ((), and closing parenthesis ()); the length is not limited.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Email

```TypeScript
Email
```

Email address input mode.

This mode accepts only digits, letters, underscores (_), dots (.), and the following special characters: ! # $ % &' " * + - / = ? ^ ` { | } ~ @. The at sign can appear only once.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Password

```TypeScript
Password
```

Password input mode.

The entered text is briefly displayed before turning to dots by default. Since API version 12, the entered text is directly displayed as dots on PCs and 2-in-1 devices.

The eye icon at the end of the input box is hidden by default on TV devices, and shown by default on other devices.

The [decoration](arkts-arkui-textinput-comp-attribute.md#decoration), [showUnderline](arkts-arkui-textinput-comp-attribute.md#showunderline), and [lineHeight](arkts-arkui-textinput-comp-attribute.md#lineheight) attributes do not take effect in password input mode.

If Password Vault is enabled, autofill is available for the username and password.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## NUMBER_PASSWORD

```TypeScript
NUMBER_PASSWORD = 8
```

Numeric password input mode.

The entered text is briefly displayed before turning to dots by default. Since API version 12, the entered text is directly displayed as dots on PCs and 2-in-1 devices.

The eye icon at the end of the input box is hidden by default on TV devices, and shown by default on other devices.

The password input mode does not support underlines. If Password Vault is enabled, autofill is available for the username and password.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## USER_NAME

```TypeScript
USER_NAME = 10
```

User name input mode with no special restrictions.

If Password Vault is enabled, autofill is available for the username and password.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## NEW_PASSWORD

```TypeScript
NEW_PASSWORD = 11
```

New password input mode with no special restrictions.

The entered text is briefly displayed before turning to dots by default. Since API version 12, the entered text is directly displayed as dots on PCs and 2-in-1 devices.

The eye icon at the end of the input box is hidden by default on TV devices, and shown by default on other devices.

If Password Vault is enabled, a new password can be automatically generated.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## NUMBER_DECIMAL

```TypeScript
NUMBER_DECIMAL = 12
```

Number input mode with a decimal point.

The value can contain digits and only one decimal point. Negative decimals are not supported. For the input mode of negative decimals, use **inputFilter**.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## URL

```TypeScript
URL = 13
```

URL input mode with no special restrictions.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## ONE_TIME_CODE

```TypeScript
ONE_TIME_CODE = 14
```

One-time code (verification code) input mode with no special restrictions.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
