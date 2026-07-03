# text_input.h
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @Zhang-Dong-hui-->
<!--Designer: @xiangyuan6-->
<!--Tester: @jiaoaozihao-->
<!--Adviser: @Brilliantry_Rui-->

## Overview

Defines enumerations and APIs related to **TextInput**.

**File to include:** <arkui/node_attributes/text_input.h>

**Library:** libace_ndk.z.so

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Since:** 12

**Related module:** [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**Sample:** <!--RP1-->[native_type_sample](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/ArkUISample/NativeType/native_type_sample)<!--RP1End-->

## Summary

### Enums

| Name| typedef Keyword| Description|
| -- | -- | -- |
| [ArkUI_TextInputType](#arkui_textinputtype) | ArkUI_TextInputType | Enumerates the input method types of a single-line text.|
| [ArkUI_CancelButtonStyle](#arkui_cancelbuttonstyle) | ArkUI_CancelButtonStyle | Enumerates the styles of the **Cancel** button.|
| [ArkUI_TextInputContentType](#arkui_textinputcontenttype) | ArkUI_TextInputContentType | Enumerates autofill types.|
| [ArkUI_TextInputStyle](#arkui_textinputstyle) | ArkUI_TextInputStyle | Enumerates text input styles.|

## Enum Description

### ArkUI_TextInputType

```c
enum ArkUI_TextInputType
```

**Description**

Enumerates the input method types of a single-line text.

**Since:** 12

| Value| Description|
| -- | -- |
| ARKUI_TEXTINPUT_TYPE_NORMAL = 0 | Normal input mode.|
| ARKUI_TEXTINPUT_TYPE_NUMBER = 2 | Number input mode.|
| ARKUI_TEXTINPUT_TYPE_PHONE_NUMBER = 3 | Phone number input mode.|
| ARKUI_TEXTINPUT_TYPE_EMAIL = 5 | Email address input mode.|
| ARKUI_TEXTINPUT_TYPE_PASSWORD = 7 | Password input mode.|
| ARKUI_TEXTINPUT_TYPE_NUMBER_PASSWORD = 8 | Numeric password input mode.|
| ARKUI_TEXTINPUT_TYPE_SCREEN_LOCK_PASSWORD = 9 | Lock screen password input mode.|
| ARKUI_TEXTINPUT_TYPE_USER_NAME = 10 | Username input mode.|
| ARKUI_TEXTINPUT_TYPE_NEW_PASSWORD = 11 | New password input mode.|
| ARKUI_TEXTINPUT_TYPE_NUMBER_DECIMAL = 12 | Number input mode with a decimal point.|
| ARKUI_TEXTINPUT_TYPE_ONE_TIME_CODE = 14 | Verification code input mode.<br>**Since:** 20|

### ArkUI_CancelButtonStyle

```c
enum ArkUI_CancelButtonStyle
```

**Description**

Enumerates the styles of the **Cancel** button.

**Since:** 12

| Value| Description|
| -- | -- |
| ARKUI_CANCELBUTTON_STYLE_CONSTANT = 0 | The **Cancel** button is always displayed.|
| ARKUI_CANCELBUTTON_STYLE_INVISIBLE = 1 | The **Cancel** button is always hidden.|
| ARKUI_CANCELBUTTON_STYLE_INPUT = 2 | The **Cancel** button is displayed when there is text input.|

### ArkUI_TextInputContentType

```c
enum ArkUI_TextInputContentType
```

**Description**

Enumerates autofill types.

**Since:** 12

| Value| Description|
| -- | -- |
| ARKUI_TEXTINPUT_CONTENT_TYPE_USER_NAME = 0 | Username. Password Vault, when enabled, can automatically save and fill in usernames.|
| ARKUI_TEXTINPUT_CONTENT_TYPE_PASSWORD = 1 | Password. Password Vault, when enabled, can automatically save and fill in passwords.|
| ARKUI_TEXTINPUT_CONTENT_TYPE_NEW_PASSWORD = 2 | New password. Password Vault, when enabled, can automatically generate a new password.|
| ARKUI_TEXTINPUT_CONTENT_TYPE_FULL_STREET_ADDRESS = 3 | Full street address. The scenario-based autofill feature, when enabled, can automatically save and fill in full street addresses.|
| ARKUI_TEXTINPUT_CONTENT_TYPE_HOUSE_NUMBER = 4 | House number. The scenario-based autofill feature, when enabled, can automatically save and fill in house numbers.|
| ARKUI_TEXTINPUT_CONTENT_TYPE_DISTRICT_ADDRESS = 5 | District and county. The scenario-based autofill feature, when enabled, can automatically save and fill in districts and counties.|
| ARKUI_TEXTINPUT_CONTENT_TYPE_CITY_ADDRESS = 6 | City. The scenario-based autofill feature, when enabled, can automatically save and fill in cities.|
| ARKUI_TEXTINPUT_CONTENT_TYPE_PROVINCE_ADDRESS = 7 | Province. The scenario-based autofill feature, when enabled, can automatically save and fill in provinces.|
| ARKUI_TEXTINPUT_CONTENT_TYPE_COUNTRY_ADDRESS = 8 | Country. The scenario-based autofill feature, when enabled, can automatically save and fill in countries.|
| ARKUI_TEXTINPUT_CONTENT_TYPE_PERSON_FULL_NAME = 9 | Full name. The scenario-based autofill feature, when enabled, can automatically save and fill in full names.|
| ARKUI_TEXTINPUT_CONTENT_TYPE_PERSON_LAST_NAME = 10 | Last name. The scenario-based autofill feature, when enabled, can automatically save and fill in last names.|
| ARKUI_TEXTINPUT_CONTENT_TYPE_PERSON_FIRST_NAME = 11 | First name. The scenario-based autofill feature, when enabled, can automatically save and fill in first names.|
| ARKUI_TEXTINPUT_CONTENT_TYPE_PHONE_NUMBER = 12 | Phone number. The scenario-based autofill feature, when enabled, can automatically save and fill in phone numbers.|
| ARKUI_TEXTINPUT_CONTENT_TYPE_PHONE_COUNTRY_CODE = 13 | Country code. The scenario-based autofill feature, when enabled, can automatically save and fill in country codes.|
| ARKUI_TEXTINPUT_CONTENT_TYPE_FULL_PHONE_NUMBER = 14 | Phone number with country code. The scenario-based autofill feature, when enabled, can automatically save and fill in phone numbers with country codes.|
| ARKUI_TEXTINPUT_CONTENT_EMAIL_ADDRESS = 15 | Email address. The scenario-based autofill feature, when enabled, can automatically save and fill in email addresses.|
| ARKUI_TEXTINPUT_CONTENT_TYPE_BANK_CARD_NUMBER = 16 | Bank card number. The scenario-based autofill feature, when enabled, can automatically save and fill in bank card numbers.|
| ARKUI_TEXTINPUT_CONTENT_TYPE_ID_CARD_NUMBER = 17 | ID card number. The scenario-based autofill feature, when enabled, can automatically save and fill in ID card numbers.|
| ARKUI_TEXTINPUT_CONTENT_TYPE_NICKNAME = 18 | Nickname. The scenario-based autofill feature, when enabled, can automatically save and fill in nicknames.|
| ARKUI_TEXTINPUT_CONTENT_TYPE_DETAIL_INFO_WITHOUT_STREET = 19 | Address information without street address. The scenario-based autofill feature, when enabled, can automatically save and fill in address information without street addresses.|
| ARKUI_TEXTINPUT_CONTENT_TYPE_FORMAT_ADDRESS = 20 | Standard address. The scenario-based autofill feature, when enabled, can automatically save and fill in standard addresses.|
| ARKUI_TEXTINPUT_CONTENT_TYPE_PASSPORT_NUMBER = 21 | Passport number. The scenario-based autofill feature, when enabled, can automatically save and fill in passport numbers.<br>**Since:** 18|
| ARKUI_TEXTINPUT_CONTENT_TYPE_VALIDITY = 22 | Passport validity period. The scenario-based autofill feature, when enabled, can automatically save and fill in passport validity periods.<br>**Since:** 18|
| ARKUI_TEXTINPUT_CONTENT_TYPE_ISSUE_AT = 23 | Passport place of issue. The scenario-based autofill feature, when enabled, can automatically save and fill in the place of issue for passports.<br>**Since:** 18|
| ARKUI_TEXTINPUT_CONTENT_TYPE_ORGANIZATION = 24 | Invoice title. The scenario-based autofill feature, when enabled, can automatically save and fill in invoice titles.<br>**Since:** 18|
| ARKUI_TEXTINPUT_CONTENT_TYPE_TAX_ID = 25 | Tax ID. The scenario-based autofill feature, when enabled, can automatically save and fill in tax IDs.<br>**Since:** 18|
| ARKUI_TEXTINPUT_CONTENT_TYPE_ADDRESS_CITY_AND_STATE = 26 | Location. The scenario-based autofill feature, when enabled, can automatically save and fill in locations.<br>**Since:** 18|
| ARKUI_TEXTINPUT_CONTENT_TYPE_FLIGHT_NUMBER = 27 | Flight number. Currently not supported for automatic saving and auto-filling.<br>**Since:** 18|
| ARKUI_TEXTINPUT_CONTENT_TYPE_LICENSE_NUMBER = 28 | Driver's license number. Currently not supported for automatic saving and auto-filling.<br>**Since:** 18|
| ARKUI_TEXTINPUT_CONTENT_TYPE_LICENSE_FILE_NUMBER = 29 | Driver's license file number. Currently not supported for automatic saving and auto-filling.<br>**Since:** 18|
| ARKUI_TEXTINPUT_CONTENT_TYPE_LICENSE_PLATE = 30 | License plate number. The scenario-based autofill feature, when enabled, can automatically save and fill in license plate numbers.<br>**Since:** 18|
| ARKUI_TEXTINPUT_CONTENT_TYPE_ENGINE_NUMBER = 31 | Vehicle registration engine number. Currently not supported for automatic saving and auto-filling.<br>**Since:** 18|
| ARKUI_TEXTINPUT_CONTENT_TYPE_LICENSE_CHASSIS_NUMBER = 32 | Chassis number. Currently not supported for automatic saving and auto-filling.<br>**Since:** 18|

### ArkUI_TextInputStyle

```c
enum ArkUI_TextInputStyle
```

**Description**

Enumerates text input styles.

**Since:** 12

| Value| Description|
| -- | -- |
| ARKUI_TEXTINPUT_STYLE_DEFAULT = 0 | Default style. The caret width is fixed at 1.5 vp, and the caret height is subject to the background height and font size of the selected text.|
| ARKUI_TEXTINPUT_STYLE_INLINE = 1 | Inline style. The background height of the selected text is the same as the height of the text box.|
