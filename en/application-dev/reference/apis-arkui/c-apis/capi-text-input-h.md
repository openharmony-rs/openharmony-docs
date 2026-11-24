# text_input.h

## Overview

Defines enumerations related to **TextInput**, which supports multiple input type configurations (including text, numbers, passwords, emails, and phone numbers),  style customization of the clear button, auto-filling content type settings, and input box style selection. It is applicable to scenarios requiring user interaction input, such as login and registration, form filling, and search input, helping you quickly implement single-line text input that meets service requirements.

**File to Include**: <arkui/text_input.h>

**Library**: libace_ndk.z.so

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

**Related module**: [ArkUI_NativeModule](capi-arkui-arkui-nativemodule.md)

## Summary

### Enums

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

<!--Device-enum ArkUI_TextInputType--><!--Device-enum ArkUI_TextInputType-End-->

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

| Enum item | Description |
| -- | -- |
| ARKUI_TEXTINPUT_TYPE_NORMAL = 0 | Normal input type with no special restrictions.<br><!--Device-ARKUI_TEXTINPUT_TYPE_NORMAL = 0--><!--Device-ARKUI_TEXTINPUT_TYPE_NORMAL = 0-End--> |
| ARKUI_TEXTINPUT_TYPE_NUMBER = 2 | Numeric input type.<br><!--Device-ARKUI_TEXTINPUT_TYPE_NUMBER = 2--><!--Device-ARKUI_TEXTINPUT_TYPE_NUMBER = 2-End--> |
| ARKUI_TEXTINPUT_TYPE_PHONE_NUMBER = 3 | Phone number input type.<br>It supports input of digits, spaces, +, -, *, #, (, ), with no length limit.<br><!--Device-ARKUI_TEXTINPUT_TYPE_PHONE_NUMBER = 3--><!--Device-ARKUI_TEXTINPUT_TYPE_PHONE_NUMBER = 3-End--> |
| ARKUI_TEXTINPUT_TYPE_EMAIL = 5 | Email address input type.<br>It supports digits, letters, underscores, decimal points, !, #, $, %, &, ', *, +, -, /, =, ?, ^, `, \{, \\|, \}, ~, and @ (only one @ character allowed). The email address format must follow the basic specification: the part before the @ character is the username, and the part after the @ character is the domain name.<br><!--Device-ARKUI_TEXTINPUT_TYPE_EMAIL = 5--><!--Device-ARKUI_TEXTINPUT_TYPE_EMAIL = 5-End--> |
| ARKUI_TEXTINPUT_TYPE_PASSWORD = 7 | Password input type.<br>By default, the input text is briefly displayed and then changed to dots. Since API version 12, on PCs/2-in-1 devices, the input text is directly displayed as dots.<br>On TV devices, the eye icon is hidden by default at the end of the input box. On other devices, the eye icon is shown by default at the end of the input box.<br><!--Device-ARKUI_TEXTINPUT_TYPE_PASSWORD = 7--><!--Device-ARKUI_TEXTINPUT_TYPE_PASSWORD = 7-End--> |
| ARKUI_TEXTINPUT_TYPE_NUMBER_PASSWORD = 8 | Numeric password input type.<br>By default, the input text is briefly displayed and then changed to dots. Since API version 12, on PCs/2-in-1 devices, the input text is directly displayed as dots.<br>On TV devices, the eye icon is hidden by default at the end of the input box. On other devices, the eye icon is shown by default at the end of the input box.<br><!--Device-ARKUI_TEXTINPUT_TYPE_NUMBER_PASSWORD = 8--><!--Device-ARKUI_TEXTINPUT_TYPE_NUMBER_PASSWORD = 8-End--> |
| ARKUI_TEXTINPUT_TYPE_SCREEN_LOCK_PASSWORD = 9 | Lock screen password input type.<br>It supports input of digits, letters, underscores, spaces, and special characters. The eye icon is shown at the end of the input box and the input text changes to dots by default. Since API version 12, on wearables, the input text is directly displayed as dots. The password input type does not support the underline style.<br><!--Device-ARKUI_TEXTINPUT_TYPE_SCREEN_LOCK_PASSWORD = 9--><!--Device-ARKUI_TEXTINPUT_TYPE_SCREEN_LOCK_PASSWORD = 9-End--> |
| ARKUI_TEXTINPUT_TYPE_USER_NAME = 10 | Username input type with no special restrictions.<br>When Password Vault is enabled, usernames can be auto-saved and auto-filled.<br><!--Device-ARKUI_TEXTINPUT_TYPE_USER_NAME = 10--><!--Device-ARKUI_TEXTINPUT_TYPE_USER_NAME = 10-End--> |
| ARKUI_TEXTINPUT_TYPE_NEW_PASSWORD = 11 | New password input type.<br>By default, the input text is briefly displayed and then changed to dots. Since API version 12, on PCs/2-in-1 devices, the input text is directly displayed as dots.<br>On TV devices, the eye icon is hidden by default at the end of the input box. On other devices, the eye icon is shown by default at the end of the input box.<br><!--Device-ARKUI_TEXTINPUT_TYPE_NEW_PASSWORD = 11--><!--Device-ARKUI_TEXTINPUT_TYPE_NEW_PASSWORD = 11-End--> |
| ARKUI_TEXTINPUT_TYPE_NUMBER_DECIMAL = 12 | Number input type with a decimal point.<br>It supports digits and a decimal point (only one decimal point allowed), and does not support negative numbers (including negative integers and negative decimals).<br><!--Device-ARKUI_TEXTINPUT_TYPE_NUMBER_DECIMAL = 12--><!--Device-ARKUI_TEXTINPUT_TYPE_NUMBER_DECIMAL = 12-End--> |
| ARKUI_TEXTINPUT_TYPE_ONE_TIME_CODE = 14 | Verification code input type with no special restrictions. In this type, the system input method is shown by default when the component gains focus.<br>**Since**: 20<br><!--Device-ARKUI_TEXTINPUT_TYPE_ONE_TIME_CODE = 14--><!--Device-ARKUI_TEXTINPUT_TYPE_ONE_TIME_CODE = 14-End--> |

### ArkUI_CancelButtonStyle

```c
enum ArkUI_CancelButtonStyle
```

**Description**

Enumerates the styles of the **Cancel** button.

<!--Device-enum ArkUI_CancelButtonStyle--><!--Device-enum ArkUI_CancelButtonStyle-End-->

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

| Enum item | Description |
| -- | -- |
| ARKUI_CANCELBUTTON_STYLE_CONSTANT = 0 | The Cancel button is always displayed.<br><!--Device-ARKUI_CANCELBUTTON_STYLE_CONSTANT = 0--><!--Device-ARKUI_CANCELBUTTON_STYLE_CONSTANT = 0-End--> |
| ARKUI_CANCELBUTTON_STYLE_INVISIBLE | The Cancel button is always hidden.<br><!--Device-ARKUI_CANCELBUTTON_STYLE_INVISIBLE--><!--Device-ARKUI_CANCELBUTTON_STYLE_INVISIBLE-End--> |
| ARKUI_CANCELBUTTON_STYLE_INPUT | The Cancel button is displayed when there is text input.<br><!--Device-ARKUI_CANCELBUTTON_STYLE_INPUT--><!--Device-ARKUI_CANCELBUTTON_STYLE_INPUT-End--> |

### ArkUI_TextInputContentType

```c
enum ArkUI_TextInputContentType
```

**Description**

Enumerates autofill types.

<!--Device-enum ArkUI_TextInputContentType--><!--Device-enum ArkUI_TextInputContentType-End-->

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

| Enum item | Description |
| -- | -- |
| ARKUI_TEXTINPUT_CONTENT_TYPE_USER_NAME = 0 | Username. Password Vault, when enabled, can automatically save and fill in usernames.<br><!--Device-ARKUI_TEXTINPUT_CONTENT_TYPE_USER_NAME = 0--><!--Device-ARKUI_TEXTINPUT_CONTENT_TYPE_USER_NAME = 0-End--> |
| ARKUI_TEXTINPUT_CONTENT_TYPE_PASSWORD | Password. Password Vault, when enabled, can automatically save and fill in passwords.<br><!--Device-ARKUI_TEXTINPUT_CONTENT_TYPE_PASSWORD--><!--Device-ARKUI_TEXTINPUT_CONTENT_TYPE_PASSWORD-End--> |
| ARKUI_TEXTINPUT_CONTENT_TYPE_NEW_PASSWORD | New password. Password Vault, when enabled, can automatically generate a new password.<br><!--Device-ARKUI_TEXTINPUT_CONTENT_TYPE_NEW_PASSWORD--><!--Device-ARKUI_TEXTINPUT_CONTENT_TYPE_NEW_PASSWORD-End--> |
| ARKUI_TEXTINPUT_CONTENT_TYPE_FULL_STREET_ADDRESS | Full street address. The scenario-based autofill feature, when enabled, can automatically save and fill in full street addresses.<br><!--Device-ARKUI_TEXTINPUT_CONTENT_TYPE_FULL_STREET_ADDRESS--><!--Device-ARKUI_TEXTINPUT_CONTENT_TYPE_FULL_STREET_ADDRESS-End--> |
| ARKUI_TEXTINPUT_CONTENT_TYPE_HOUSE_NUMBER | House number. The scenario-based autofill feature, when enabled, can automatically save and fill in house numbers.<br><!--Device-ARKUI_TEXTINPUT_CONTENT_TYPE_HOUSE_NUMBER--><!--Device-ARKUI_TEXTINPUT_CONTENT_TYPE_HOUSE_NUMBER-End--> |
| ARKUI_TEXTINPUT_CONTENT_TYPE_DISTRICT_ADDRESS | District and county. The scenario-based autofill feature, when enabled, can automatically save and fill in districts and counties.<br><!--Device-ARKUI_TEXTINPUT_CONTENT_TYPE_DISTRICT_ADDRESS--><!--Device-ARKUI_TEXTINPUT_CONTENT_TYPE_DISTRICT_ADDRESS-End--> |
| ARKUI_TEXTINPUT_CONTENT_TYPE_CITY_ADDRESS | City. The scenario-based autofill feature, when enabled, can automatically save and fill in cities.<br><!--Device-ARKUI_TEXTINPUT_CONTENT_TYPE_CITY_ADDRESS--><!--Device-ARKUI_TEXTINPUT_CONTENT_TYPE_CITY_ADDRESS-End--> |
| ARKUI_TEXTINPUT_CONTENT_TYPE_PROVINCE_ADDRESS | Province. The scenario-based autofill feature, when enabled, can automatically save and fill in provinces.<br><!--Device-ARKUI_TEXTINPUT_CONTENT_TYPE_PROVINCE_ADDRESS--><!--Device-ARKUI_TEXTINPUT_CONTENT_TYPE_PROVINCE_ADDRESS-End--> |
| ARKUI_TEXTINPUT_CONTENT_TYPE_COUNTRY_ADDRESS | Country. The scenario-based autofill feature, when enabled, can automatically save and fill in countries.<br><!--Device-ARKUI_TEXTINPUT_CONTENT_TYPE_COUNTRY_ADDRESS--><!--Device-ARKUI_TEXTINPUT_CONTENT_TYPE_COUNTRY_ADDRESS-End--> |
| ARKUI_TEXTINPUT_CONTENT_TYPE_PERSON_FULL_NAME | Full name. The scenario-based autofill feature, when enabled, can automatically save and fill in full names.<br><!--Device-ARKUI_TEXTINPUT_CONTENT_TYPE_PERSON_FULL_NAME--><!--Device-ARKUI_TEXTINPUT_CONTENT_TYPE_PERSON_FULL_NAME-End--> |
| ARKUI_TEXTINPUT_CONTENT_TYPE_PERSON_LAST_NAME | Last name. The scenario-based autofill feature, when enabled, can automatically save and fill in last names.<br><!--Device-ARKUI_TEXTINPUT_CONTENT_TYPE_PERSON_LAST_NAME--><!--Device-ARKUI_TEXTINPUT_CONTENT_TYPE_PERSON_LAST_NAME-End--> |
| ARKUI_TEXTINPUT_CONTENT_TYPE_PERSON_FIRST_NAME | First name. The scenario-based autofill feature, when enabled, can automatically save and fill in first names.<br><!--Device-ARKUI_TEXTINPUT_CONTENT_TYPE_PERSON_FIRST_NAME--><!--Device-ARKUI_TEXTINPUT_CONTENT_TYPE_PERSON_FIRST_NAME-End--> |
| ARKUI_TEXTINPUT_CONTENT_TYPE_PHONE_NUMBER | Phone number. The scenario-based autofill feature, when enabled, can automatically save and fill in phone numbers.<br><!--Device-ARKUI_TEXTINPUT_CONTENT_TYPE_PHONE_NUMBER--><!--Device-ARKUI_TEXTINPUT_CONTENT_TYPE_PHONE_NUMBER-End--> |
| ARKUI_TEXTINPUT_CONTENT_TYPE_PHONE_COUNTRY_CODE | Country code. The scenario-based autofill feature, when enabled, can automatically save and fill in country codes.<br><!--Device-ARKUI_TEXTINPUT_CONTENT_TYPE_PHONE_COUNTRY_CODE--><!--Device-ARKUI_TEXTINPUT_CONTENT_TYPE_PHONE_COUNTRY_CODE-End--> |
| ARKUI_TEXTINPUT_CONTENT_TYPE_FULL_PHONE_NUMBER | Phone number with country code. The scenario-based autofill feature, when enabled, can automatically save and fill in phone numbers with country codes.<br><!--Device-ARKUI_TEXTINPUT_CONTENT_TYPE_FULL_PHONE_NUMBER--><!--Device-ARKUI_TEXTINPUT_CONTENT_TYPE_FULL_PHONE_NUMBER-End--> |
| ARKUI_TEXTINPUT_CONTENT_EMAIL_ADDRESS | Email address. The scenario-based autofill feature, when enabled, can automatically save and fill in email addresses.<br><!--Device-ARKUI_TEXTINPUT_CONTENT_EMAIL_ADDRESS--><!--Device-ARKUI_TEXTINPUT_CONTENT_EMAIL_ADDRESS-End--> |
| ARKUI_TEXTINPUT_CONTENT_TYPE_BANK_CARD_NUMBER | Bank card number. The scenario-based autofill feature, when enabled, can automatically save and fill in bank card numbers.<br><!--Device-ARKUI_TEXTINPUT_CONTENT_TYPE_BANK_CARD_NUMBER--><!--Device-ARKUI_TEXTINPUT_CONTENT_TYPE_BANK_CARD_NUMBER-End--> |
| ARKUI_TEXTINPUT_CONTENT_TYPE_ID_CARD_NUMBER | ID card number. The scenario-based autofill feature, when enabled, can automatically save and fill in ID card numbers.<br><!--Device-ARKUI_TEXTINPUT_CONTENT_TYPE_ID_CARD_NUMBER--><!--Device-ARKUI_TEXTINPUT_CONTENT_TYPE_ID_CARD_NUMBER-End--> |
| ARKUI_TEXTINPUT_CONTENT_TYPE_NICKNAME | Nickname. The scenario-based autofill feature, when enabled, can automatically save and fill in nicknames.<br><!--Device-ARKUI_TEXTINPUT_CONTENT_TYPE_NICKNAME--><!--Device-ARKUI_TEXTINPUT_CONTENT_TYPE_NICKNAME-End--> |
| ARKUI_TEXTINPUT_CONTENT_TYPE_DETAIL_INFO_WITHOUT_STREET | Address information without street address. The scenario-based autofill feature, when enabled, can automatically save and fill in address information without street addresses.<br><!--Device-ARKUI_TEXTINPUT_CONTENT_TYPE_DETAIL_INFO_WITHOUT_STREET--><!--Device-ARKUI_TEXTINPUT_CONTENT_TYPE_DETAIL_INFO_WITHOUT_STREET-End--> |
| ARKUI_TEXTINPUT_CONTENT_TYPE_FORMAT_ADDRESS | Standard address. The scenario-based autofill feature, when enabled, can automatically save and fill in standard addresses.<br><!--Device-ARKUI_TEXTINPUT_CONTENT_TYPE_FORMAT_ADDRESS--><!--Device-ARKUI_TEXTINPUT_CONTENT_TYPE_FORMAT_ADDRESS-End--> |
| ARKUI_TEXTINPUT_CONTENT_TYPE_PASSPORT_NUMBER | Passport number. The scenario-based autofill feature, when enabled, can automatically save and fill in passport numbers.<br>**Since**: 18<br><!--Device-ARKUI_TEXTINPUT_CONTENT_TYPE_PASSPORT_NUMBER--><!--Device-ARKUI_TEXTINPUT_CONTENT_TYPE_PASSPORT_NUMBER-End--> |
| ARKUI_TEXTINPUT_CONTENT_TYPE_VALIDITY | Passport validity period. The scenario-based autofill feature, when enabled, can automatically save and fill in passport validity periods.<br>**Since**: 18<br><!--Device-ARKUI_TEXTINPUT_CONTENT_TYPE_VALIDITY--><!--Device-ARKUI_TEXTINPUT_CONTENT_TYPE_VALIDITY-End--> |
| ARKUI_TEXTINPUT_CONTENT_TYPE_ISSUE_AT | Passport place of issue. The scenario-based autofill feature, when enabled, can automatically save and fill in the place of issue for passports.<br>**Since**: 18<br><!--Device-ARKUI_TEXTINPUT_CONTENT_TYPE_ISSUE_AT--><!--Device-ARKUI_TEXTINPUT_CONTENT_TYPE_ISSUE_AT-End--> |
| ARKUI_TEXTINPUT_CONTENT_TYPE_ORGANIZATION | Invoice title. The scenario-based autofill feature, when enabled, can automatically save and fill in invoice titles.<br>**Since**: 18<br><!--Device-ARKUI_TEXTINPUT_CONTENT_TYPE_ORGANIZATION--><!--Device-ARKUI_TEXTINPUT_CONTENT_TYPE_ORGANIZATION-End--> |
| ARKUI_TEXTINPUT_CONTENT_TYPE_TAX_ID | Tax ID. The scenario-based autofill feature, when enabled, can automatically save and fill in tax IDs.<br>**Since**: 18<br><!--Device-ARKUI_TEXTINPUT_CONTENT_TYPE_TAX_ID--><!--Device-ARKUI_TEXTINPUT_CONTENT_TYPE_TAX_ID-End--> |
| ARKUI_TEXTINPUT_CONTENT_TYPE_ADDRESS_CITY_AND_STATE | Location. The scenario-based autofill feature, when enabled, can automatically save and fill in locations.<br>**Since**: 18<br><!--Device-ARKUI_TEXTINPUT_CONTENT_TYPE_ADDRESS_CITY_AND_STATE--><!--Device-ARKUI_TEXTINPUT_CONTENT_TYPE_ADDRESS_CITY_AND_STATE-End--> |
| ARKUI_TEXTINPUT_CONTENT_TYPE_FLIGHT_NUMBER | Flight number. Currently not supported for automatic saving and auto-filling.<br>**Since**: 18<br><!--Device-ARKUI_TEXTINPUT_CONTENT_TYPE_FLIGHT_NUMBER--><!--Device-ARKUI_TEXTINPUT_CONTENT_TYPE_FLIGHT_NUMBER-End--> |
| ARKUI_TEXTINPUT_CONTENT_TYPE_LICENSE_NUMBER | Driver's license number. Currently not supported for automatic saving and auto-filling.<br>**Since**: 18<br><!--Device-ARKUI_TEXTINPUT_CONTENT_TYPE_LICENSE_NUMBER--><!--Device-ARKUI_TEXTINPUT_CONTENT_TYPE_LICENSE_NUMBER-End--> |
| ARKUI_TEXTINPUT_CONTENT_TYPE_LICENSE_FILE_NUMBER | Driver's license file number. Currently not supported for automatic saving and auto-filling.<br>**Since**: 18<br><!--Device-ARKUI_TEXTINPUT_CONTENT_TYPE_LICENSE_FILE_NUMBER--><!--Device-ARKUI_TEXTINPUT_CONTENT_TYPE_LICENSE_FILE_NUMBER-End--> |
| ARKUI_TEXTINPUT_CONTENT_TYPE_LICENSE_PLATE | License plate number. The scenario-based autofill feature, when enabled, can automatically save and fill in license plate numbers.<br>**Since**: 18<br><!--Device-ARKUI_TEXTINPUT_CONTENT_TYPE_LICENSE_PLATE--><!--Device-ARKUI_TEXTINPUT_CONTENT_TYPE_LICENSE_PLATE-End--> |
| ARKUI_TEXTINPUT_CONTENT_TYPE_ENGINE_NUMBER | Vehicle registration engine number. Currently not supported for automatic saving and auto-filling.<br>**Since**: 18<br><!--Device-ARKUI_TEXTINPUT_CONTENT_TYPE_ENGINE_NUMBER--><!--Device-ARKUI_TEXTINPUT_CONTENT_TYPE_ENGINE_NUMBER-End--> |
| ARKUI_TEXTINPUT_CONTENT_TYPE_LICENSE_CHASSIS_NUMBER | Chassis number. Auto-save and auto-fill are not yet supported.<br>**Since**: 18<br><!--Device-ARKUI_TEXTINPUT_CONTENT_TYPE_LICENSE_CHASSIS_NUMBER--><!--Device-ARKUI_TEXTINPUT_CONTENT_TYPE_LICENSE_CHASSIS_NUMBER-End--> |

### ArkUI_TextInputStyle

```c
enum ArkUI_TextInputStyle
```

**Description**

Enumerates text input styles.

<!--Device-enum ArkUI_TextInputStyle--><!--Device-enum ArkUI_TextInputStyle-End-->

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

| Enum item | Description |
| -- | -- |
| ARKUI_TEXTINPUT_STYLE_DEFAULT = 0 | Default style. The caret width is fixed at 1.5 vp, and the caret height is subject to the background height and font size of the selected text.<br><!--Device-ARKUI_TEXTINPUT_STYLE_DEFAULT = 0--><!--Device-ARKUI_TEXTINPUT_STYLE_DEFAULT = 0-End--> |
| ARKUI_TEXTINPUT_STYLE_INLINE | Inline input style. The background height of the selected text is the same as the height of the text box.<br><!--Device-ARKUI_TEXTINPUT_STYLE_INLINE--><!--Device-ARKUI_TEXTINPUT_STYLE_INLINE-End--> |


