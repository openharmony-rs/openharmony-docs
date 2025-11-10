# Globalization Subsystem Changelog

## cl.global.1 Change in the Default Calendar of Thailand, Saudi Arabia, Afghanistan, and Iran

**Access Level**

Public API

**Reason for the Change**

The default calendar of Thailand, Saudi Arabia, Afghanistan, and Iran is incorrect.

**Impact of the Change**

This change does not require application adaptation.

Before change: The default calendar of Thailand is Buddhist calendar, that of Saudi Arabia is Islamic calendar, and that of Afghanistan and Iran is Persian calendar. For example, if Thailand is specified as the country/region when [intl.DateTimeFormat](../../../application-dev/reference/apis-localization-kit/js-apis-intl.md#datetimeformat) is called, the Buddhist calendar will be used to display the date when [format](../../../application-dev/reference/apis-localization-kit/js-apis-intl.md#formatdeprecated) is called.
  
After change: The default calendar of Thailand, Saudi Arabia, Afghanistan, and Iran is the Gregorian calendar. For example, if Thailand is specified as the country/region when [intl.DateTimeFormat](../../../application-dev/reference/apis-localization-kit/js-apis-intl.md#datetimeformat) is called, the Gregorian calendar will be used to display the date when [format](../../../application-dev/reference/apis-localization-kit/js-apis-intl.md#formatdeprecated) is called.
  
**Start API Level**

API 8

**Change Since**

OpenHarmony SDK 6.0.0.40

**Key API/Component Changes**

| File| API|
| ---- | --- |
| @ohos.intl.d.ts | [intl.DateTimeFormat.prototype.format](../../../application-dev/reference/apis-localization-kit/js-apis-intl.md#formatdeprecated) |
| @ohos.intl.d.ts | [intl.DateTimeFormat.prototype.formatRange](../../../application-dev/reference/apis-localization-kit/js-apis-intl.md#formatrangedeprecated) |
| @ohos.i18n.d.ts | [i18n.Calendar.prototype.getDisplayName](../../../application-dev/reference/apis-localization-kit/js-apis-i18n.md#getdisplayname8) |
| @ohos.i18n.d.ts | [i18n.Calendar.prototype.get](../../../application-dev/reference/apis-localization-kit/js-apis-i18n.md#get8) |

**Adaptation Guide**

Only the calendar internally used by the API is changed. Adaptation is not needed.
