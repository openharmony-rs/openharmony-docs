# text_input.h

## Overview

Defines enumerations related to **TextInput**, which supports multiple input type configurations (including text, numbers, passwords, emails, and phone numbers),  style customization of the clear button, auto-filling content type settings, and input box style selection. It is applicable to scenarios requiring user interaction input, such as login and registration, form filling, and search input, helping you quickly implement single-line text input that meets service requirements.

**Library**: libace_ndk.z.so

**Since**: 12

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

## Summary

### Enum

| Name | typedef keyword | Description |
| -- | -- | -- |
| [ArkUI_TextInputType](#arkui_textinputtype) | ArkUI_TextInputType | Enumerates the input types of single-line text. |
| [ArkUI_CancelButtonStyle](#arkui_cancelbuttonstyle) | ArkUI_CancelButtonStyle | Enumerates the styles of the **Cancel** button. |
| [ArkUI_TextInputContentType](#arkui_textinputcontenttype) | ArkUI_TextInputContentType | Enumerates autofill types. |
| [ArkUI_TextInputStyle](#arkui_textinputstyle) | ArkUI_TextInputStyle | Enumerates text input styles. |

## Enum type description

### ArkUI_TextInputType

```c
enum ArkUI_TextInputType
```

**Description**

Enumerates the input types of single-line text.

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

Enumerates the styles of the **Cancel** button.

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

Enumerates autofill types.

**Since**: 12

| Enum item | Description |
| -- | -- |
| ARKUI_TEXTINPUT_CONTENT_TYPE_USER_NAME = 0 | Username. Password Vault, when enabled, can automatically save and fill in usernames. |
| ARKUI_TEXTINPUT_CONTENT_TYPE_PASSWORD | Password. Password Vault, when enabled, can automatically save and fill in passwords. |
| ARKUI_TEXTINPUT_CONTENT_TYPE_NEW_PASSWORD | New password. Password Vault, when enabled, can automatically generate a new password. |
| ARKUI_TEXTINPUT_CONTENT_TYPE_FULL_STREET_ADDRESS | Full street address. The scenario-based autofill feature, when enabled, can automatically save and fill in full street addresses. |
| ARKUI_TEXTINPUT_CONTENT_TYPE_HOUSE_NUMBER | House number. The scenario-based autofill feature, when enabled, can automatically save and fill in house numbers. |
| ARKUI_TEXTINPUT_CONTENT_TYPE_DISTRICT_ADDRESS | District and county. The scenario-based autofill feature, when enabled, can automatically save and fill in districts and counties. |
| ARKUI_TEXTINPUT_CONTENT_TYPE_CITY_ADDRESS | City. The scenario-based autofill feature, when enabled, can automatically save and fill in cities. |
| ARKUI_TEXTINPUT_CONTENT_TYPE_PROVINCE_ADDRESS | Province. The scenario-based autofill feature, when enabled, can automatically save and fill in provinces. |
| ARKUI_TEXTINPUT_CONTENT_TYPE_COUNTRY_ADDRESS | Country. The scenario-based autofill feature, when enabled, can automatically save and fill in countries. |
| ARKUI_TEXTINPUT_CONTENT_TYPE_PERSON_FULL_NAME | Full name. The scenario-based autofill feature, when enabled, can automatically save and fill in full names. |
| ARKUI_TEXTINPUT_CONTENT_TYPE_PERSON_LAST_NAME | Last name. The scenario-based autofill feature, when enabled, can automatically save and fill in last names. |
| ARKUI_TEXTINPUT_CONTENT_TYPE_PERSON_FIRST_NAME | First name. The scenario-based autofill feature, when enabled, can automatically save and fill in first names. |
| ARKUI_TEXTINPUT_CONTENT_TYPE_PHONE_NUMBER | Phone number. The scenario-based autofill feature, when enabled, can automatically save and fill in phone numbers. |
| ARKUI_TEXTINPUT_CONTENT_TYPE_PHONE_COUNTRY_CODE | Country code. The scenario-based autofill feature, when enabled, can automatically save and fill in country codes. |
| ARKUI_TEXTINPUT_CONTENT_TYPE_FULL_PHONE_NUMBER | Phone number with country code. The scenario-based autofill feature, when enabled, can automatically save and fill in phone numbers with country codes. |
| ARKUI_TEXTINPUT_CONTENT_EMAIL_ADDRESS | Email address. The scenario-based autofill feature, when enabled, can automatically save and fill in email addresses. |
| ARKUI_TEXTINPUT_CONTENT_TYPE_BANK_CARD_NUMBER | Bank card number. The scenario-based autofill feature, when enabled, can automatically save and fill in bank card numbers. |
| ARKUI_TEXTINPUT_CONTENT_TYPE_ID_CARD_NUMBER | ID card number. The scenario-based autofill feature, when enabled, can automatically save and fill in ID card numbers. |
| ARKUI_TEXTINPUT_CONTENT_TYPE_NICKNAME | Nickname. The scenario-based autofill feature, when enabled, can automatically save and fill in nicknames. |
| ARKUI_TEXTINPUT_CONTENT_TYPE_DETAIL_INFO_WITHOUT_STREET | Address information without street address. The scenario-based autofill feature, when enabled, can automatically save and fill in address information without street addresses. |
| ARKUI_TEXTINPUT_CONTENT_TYPE_FORMAT_ADDRESS | Standard address. The scenario-based autofill feature, when enabled, can automatically save and fill in standard addresses. |
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
| ARKUI_TEXTINPUT_CONTENT_TYPE_LICENSE_CHASSIS_NUMBER | License chassis number. The scenario-based autofill feature, when enabled, can automatically save and fill in license chassis numbers. @since 18 |

### ArkUI_TextInputStyle

```c
enum ArkUI_TextInputStyle
```

**Description**

Enumerates text input styles.

**Since**: 12

| Enum item | Description |
| -- | -- |
| ARKUI_TEXTINPUT_STYLE_DEFAULT = 0 | Default style. The caret width is fixed at 1.5 vp, and the caret height is subject to the background height and font size of the selected text. |
| ARKUI_TEXTINPUT_STYLE_INLINE | Inline input style. The background height of the selected text is the same as the height of the text box. |


