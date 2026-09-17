# text_input.h

## Overview

Defines a set of TextInput enum and interface.

**Library**: libace_ndk.z.so

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

## Summary

### Enum

| Name | typedef keyword | Description |
| -- | -- | -- |
| [ArkUI_TextInputType](#arkui_textinputtype) | ArkUI_TextInputType | Enumerates the text input types. |
| [ArkUI_CancelButtonStyle](#arkui_cancelbuttonstyle) | ArkUI_CancelButtonStyle | Enumerates the styles of the Cancel button. |
| [ArkUI_TextInputContentType](#arkui_textinputcontenttype) | ArkUI_TextInputContentType | Enumerates the autofill types. |
| [ArkUI_TextInputStyle](#arkui_textinputstyle) | ArkUI_TextInputStyle | Defines the text input style. |

## Enum type description

### ArkUI_TextInputType

```c
enum ArkUI_TextInputType
```

**Description**

Enumerates the text input types.

**Since**: 12

| Enum item | Description |
| -- | -- |
| ARKUI_TEXTINPUT_TYPE_NORMAL = 0 | Normal input mode. |
| ARKUI_TEXTINPUT_TYPE_NUMBER = 2 | Number input mode. |
| ARKUI_TEXTINPUT_TYPE_PHONE_NUMBER = 3 | Phone number input mode. |
| ARKUI_TEXTINPUT_TYPE_EMAIL = 5 | Email address input mode. |
| ARKUI_TEXTINPUT_TYPE_PASSWORD = 7 | Password input mode. |
| ARKUI_TEXTINPUT_TYPE_NUMBER_PASSWORD = 8 | Numeric password input mode. |
| ARKUI_TEXTINPUT_TYPE_SCREEN_LOCK_PASSWORD = 9 | Lock screen password input mode. |
| ARKUI_TEXTINPUT_TYPE_USER_NAME = 10 | Username input mode. |
| ARKUI_TEXTINPUT_TYPE_NEW_PASSWORD = 11 | New password input mode. |
| ARKUI_TEXTINPUT_TYPE_NUMBER_DECIMAL = 12 | Number input mode with a decimal point. |
| ARKUI_TEXTINPUT_TYPE_ONE_TIME_CODE = 14 |  |

### ArkUI_CancelButtonStyle

```c
enum ArkUI_CancelButtonStyle
```

**Description**

Enumerates the styles of the Cancel button.

**Since**: 12

| Enum item | Description |
| -- | -- |
| ARKUI_CANCELBUTTON_STYLE_CONSTANT = 0 | The Cancel button is always displayed. |
| ARKUI_CANCELBUTTON_STYLE_INVISIBLE | The Cancel button is always hidden. |
| ARKUI_CANCELBUTTON_STYLE_INPUT | The Cancel button is displayed when there is text input. |

### ArkUI_TextInputContentType

```c
enum ArkUI_TextInputContentType
```

**Description**

Enumerates the autofill types.

**Since**: 12

| Enum item | Description |
| -- | -- |
| ARKUI_TEXTINPUT_CONTENT_TYPE_USER_NAME = 0 | Username. Password Vault, when enabled, can automatically save and fill in usernames. |
| ARKUI_TEXTINPUT_CONTENT_TYPE_PASSWORD | Password. Password Vault, when enabled, can automatically save and fill in passwords. |
| ARKUI_TEXTINPUT_CONTENT_TYPE_NEW_PASSWORD | New password. Password Vault, when enabled, can automatically generate a new password. |
| ARKUI_TEXTINPUT_CONTENT_TYPE_FULL_STREET_ADDRESS | Full street address. The scenario-based autofill feature, when enabled, can automatically save and fill in full |
| ARKUI_TEXTINPUT_CONTENT_TYPE_HOUSE_NUMBER | House number. The scenario-based autofill feature, when enabled, can automatically save and fill in house |
| ARKUI_TEXTINPUT_CONTENT_TYPE_DISTRICT_ADDRESS | District and county. The scenario-based autofill feature, when enabled, can automatically save and fill in |
| ARKUI_TEXTINPUT_CONTENT_TYPE_CITY_ADDRESS | City. The scenario-based autofill feature, when enabled, can automatically save and fill in cities. |
| ARKUI_TEXTINPUT_CONTENT_TYPE_PROVINCE_ADDRESS | Province. The scenario-based autofill feature, when enabled, can automatically save and fill in provinces. |
| ARKUI_TEXTINPUT_CONTENT_TYPE_COUNTRY_ADDRESS | Country. The scenario-based autofill feature, when enabled, can automatically save and fill in countries. |
| ARKUI_TEXTINPUT_CONTENT_TYPE_PERSON_FULL_NAME | Full name. The scenario-based autofill feature, when enabled, can automatically save and fill in full names. |
| ARKUI_TEXTINPUT_CONTENT_TYPE_PERSON_LAST_NAME | Last name. The scenario-based autofill feature, when enabled, can automatically save and fill in last names. |
| ARKUI_TEXTINPUT_CONTENT_TYPE_PERSON_FIRST_NAME | First name. The scenario-based autofill feature, when enabled, can automatically save and fill in first names. |
| ARKUI_TEXTINPUT_CONTENT_TYPE_PHONE_NUMBER | Phone number. The scenario-based autofill feature, when enabled, can automatically save and fill in phone |
| ARKUI_TEXTINPUT_CONTENT_TYPE_PHONE_COUNTRY_CODE | Country code. The scenario-based autofill feature, when enabled, can automatically save and fill in country |
| ARKUI_TEXTINPUT_CONTENT_TYPE_FULL_PHONE_NUMBER | Phone number with country code. The scenario-based autofill feature, when enabled, can automatically save and |
| ARKUI_TEXTINPUT_CONTENT_EMAIL_ADDRESS | Email address. The scenario-based autofill feature, when enabled, can automatically save and fill in email |
| ARKUI_TEXTINPUT_CONTENT_TYPE_BANK_CARD_NUMBER | Bank card number. The scenario-based autofill feature, when enabled, can automatically save and fill in bank |
| ARKUI_TEXTINPUT_CONTENT_TYPE_ID_CARD_NUMBER | ID card number. The scenario-based autofill feature, when enabled, can automatically save and fill in ID card |
| ARKUI_TEXTINPUT_CONTENT_TYPE_NICKNAME | Nickname. The scenario-based autofill feature, when enabled, can automatically save and fill in nicknames. |
| ARKUI_TEXTINPUT_CONTENT_TYPE_DETAIL_INFO_WITHOUT_STREET | Address information without street address. The scenario-based autofill feature, when enabled, can automatically |
| ARKUI_TEXTINPUT_CONTENT_TYPE_FORMAT_ADDRESS | Standard address. The scenario-based autofill feature, when enabled, can automatically save and fill in standard |
| ARKUI_TEXTINPUT_CONTENT_TYPE_PASSPORT_NUMBER |  |
| ARKUI_TEXTINPUT_CONTENT_TYPE_VALIDITY | Passport validity. The scenario-based autofill feature, when enabled, can automatically save and fill in passport validities. @since 18 |
| ARKUI_TEXTINPUT_CONTENT_TYPE_ISSUE_AT | Place of issue. The scenario-based autofill feature, when enabled, can automatically save and fill in place of issues. @since 18 |
| ARKUI_TEXTINPUT_CONTENT_TYPE_ORGANIZATION | Tax organization. The scenario-based autofill feature, when enabled, can automatically save and fill in tax organizations. @since 18 |
| ARKUI_TEXTINPUT_CONTENT_TYPE_TAX_ID | Tax id. The scenario-based autofill feature, when enabled, can automatically save and fill in standard Tax ids. @since 18 |
| ARKUI_TEXTINPUT_CONTENT_TYPE_ADDRESS_CITY_AND_STATE | City name and state name or state code. The scenario-based autofill feature, when enabled, can automatically save and fill in city names and state names or state codes. @since 18 |
| ARKUI_TEXTINPUT_CONTENT_TYPE_FLIGHT_NUMBER | Flight number. The scenario-based autofill feature, when enabled, can automatically save and fill in flight numbers. @since 18 |
| ARKUI_TEXTINPUT_CONTENT_TYPE_LICENSE_NUMBER | License number. The scenario-based autofill feature, when enabled, can automatically save and fill in license numbers. @since 18 |
| ARKUI_TEXTINPUT_CONTENT_TYPE_LICENSE_FILE_NUMBER | License file number. The scenario-based autofill feature, when enabled, can automatically save and fill in license file numbers. @since 18 |
| ARKUI_TEXTINPUT_CONTENT_TYPE_LICENSE_PLATE | License plate number. The scenario-based autofill feature, when enabled, can automatically save and fill in license plate numbers. @since 18 |
| ARKUI_TEXTINPUT_CONTENT_TYPE_ENGINE_NUMBER | Engine number. The scenario-based autofill feature, when enabled, can automatically save and fill in engine numbers. @since 18 |
| ARKUI_TEXTINPUT_CONTENT_TYPE_LICENSE_CHASSIS_NUMBER | License chassis number. The scenario-based autofill feature, when enabled, can automatically save and fill in license chassis numbers. @since 18 |

### ArkUI_TextInputStyle

```c
enum ArkUI_TextInputStyle
```

**Description**

Defines the text input style.

**Since**: 12

| Enum item | Description |
| -- | -- |
| ARKUI_TEXTINPUT_STYLE_DEFAULT = 0 | Default style. The caret width is fixed at 1.5 vp, and the caret height is subject to the background height and |
| ARKUI_TEXTINPUT_STYLE_INLINE | Inline input style. The background height of the selected text is the same as the height of the text box. |


