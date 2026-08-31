# @ohos.InputMethodSubtype (Input Method Subtype)

<!--Kit: IME Kit-->
<!--Subsystem: MiscServices-->
<!--Owner: @codexu62-->
<!--Designer: @andeszhang-->
<!--Tester: @murphy84-->
<!--Adviser: @zhang_yixin13-->
<!-- md-trans-meta sourceCommit=c9f68a28229d3fb5da602baa0bfb8e542d407a50 translatedAt=2026-08-26T10:47:16.505Z pushedAt=2026-08-29T09:23:10.215Z -->

The **@ohos.InputMethodSubtype** module provides data definitions for input method subtype properties. It supports describing subtype information of an input method for different languages or modes.

This module is the subtype data module of the input method framework. It defines the `InputMethodSubtype` interface, which is used to describe a specific input mode or language of an input method, such as Chinese keyboard, an English keyboard, or uppercase-mode keyboard. Each subtype represents the form of the input method in a specific language or mode.

This module provides capabilities for describing input method subtype properties. You can use `InputMethodSubtype` to obtain subtype identifiers (`id`, `name`), locale and language information (`locale`, `language`), display label (`label`), mode (`mode`: uppercase/lowercase), icon, and other properties. These are used for identification, display, and switching of input‑method subtypes.

Use this module when you need to query, display, or switch between different language‑ or mode‑based subtypes of an input method. Typical scenarios include: the system settings app displays a list of input method subtypes for user selection; an input‑method app switches languages or modes according to subtype information; an app obtains information about the current input method subtype.

> **NOTE**
>
>The initial APIs of this module are supported since API version 9. Newly added APIs will be marked with a superscript to indicate their earliest API version.

`InputMethodSubtype` is a pure data definition module. Its objects are created and returned by the system framework, and cannot be constructed by you. Typical cross‑module usage process:

1. Edit box app side (`@ohos.inputMethod` module): Queries the list of input method subtypes via `InputMethodSetting.listInputMethodSubtype()`, and switches to the specified subtype via `inputMethod.switchCurrentInputMethodSubtype()`.

2. Input method app side (`@ohos.inputMethodEngine` module): Listens for subtype switch events through `InputMethodAbility.on('setSubtype')`. The callback parameter is an `InputMethodSubtype` object, based on which the keyboard layout and language can be adjusted.

Core open capabilities of this module are provided by the key interface below:

| Interface | Description |
|---|---|
| InputMethodSubtype | Interface for input method subtype properties, which describes a specific language or mode form of an input method.<br/>Mandatory properties: `name` (app bundle name), `id` (subtype ID), `locale` (locale), `language` (language).<br/>Optional properties: `label` (label), `labelId` (label resource ID), `mode` (uppercase/lowercase mode), `icon` (icon), `iconId` (icon ID), and `extra` (extra information). |

This module is a pure data definition module. As subtype description data, `InputMethodSubtype` must be used together with APIs from other modules. Typical usage combinations: query and switch subtypes via `@ohos.inputMethod` module using `InputMethodSetting`; listen for subtype switch events via `InputMethodAbility` in the `@ohos.inputMethodEngine` module.

```javascript
// The following is pseudocode for illustrating the calling logic.

// 1. Query the input method subtype list (combined with the @ohos.inputMethod module).
let setting = inputMethod.getSetting();
let subtypes = setting.listInputMethodSubtype(inputMethodProperty);

// 2. Switch to the specified subtype.
inputMethod.switchCurrentInputMethodSubtype(targetSubtype);
```

> **NOTE**
>
> `InputMethodSubtype` objects are created and returned by the system framework. You obtain these objects through query APIs of other modules and cannot construct them directly.

## Modules to Import

```ts
import { InputMethodSubtype } from '@kit.IMEKit';
```

## InputMethodSubtype

Input method subtype attribute. Used to describe a specific language or mode form of an input method. Each subtype represents the form of an input method under a specific language or mode (for example, Chinese keyboard, English keyboard, uppercase‑mode keyboard). `InputMethodSubtype` objects are created and returned by the system framework and cannot be constructed by you.

- Meaning/Function: Describes property information such as the identifier, language, locale, and mode of an input method subtype. Mandatory properties (`name`, `id`, `locale`, and `language`) uniquely identify and describe basic features of the subtype. Optional properties (`label`, `mode`, `icon`, and others) provide additional display and functional information.

- Usage scenarios: Used when the app needs to query, display, or switch between different language‑ or mode‑based input‑method subtypes. Examples include: the system settings app displays a list of input method subtypes for user selection; an input method app switches languages or modes based on subtype information; an app obtains information about the current input method subtype.

- Use effect: After an `InputMethodSubtype` object is obtained, its property values can be read for operations such as subtype identification, list display, and language or mode switching. The `InputMethodSubtype` object itself is read‑only and does not support modification.

**System capability**: SystemCapability.MiscServices.InputMethodFramework

| Name| Type| Read Only| Optional| Description|
| -------- | -------- | -------- | -------- | -------- |
| label | string | Yes | Yes | Label of the input method subtype. Used to display the subtype name in the UI, for example, "English". |
| labelId<sup>10+</sup> | number | Yes | Yes | Label resource ID of the input method subtype. Used to load the label text through the resource ID, supporting internationalized label display in multi-language scenarios. |
| name | string | Yes | No | Bundle name of the app to which the input method subtype belongs. It must stay consistent with the **bundleName** configured in **module.json5** of the input method app, and is used to identify which input method app the subtype belongs to. |
| id | string | Yes | No | ID of the input method subtype. It must stay consistent with the subtype id configured in **module.json5** of the input method app, and is used to uniquely identify a subtype within the same input method app. |
| mode | 'upper' \| 'lower' | Yes | Yes | Mode of the input method subtype, including **upper** (uppercase) and **lower** (lowercase). Used to describe the case state mode of the keyboard. |
| locale | string | Yes | No | Locale of the input method subtype. It follows the ICU locale format (separated by underscores, for example, **'zh_CN'**), and is also compatible with the POSIX style (separated by hyphens, for example, **'zh-CN'**). Used to identify the language and locale of the subtype. |
| language | string | Yes | No | Language of the input method subtype, for example, **'zh'** (Chinese) and **'en'** (English). Used to identify the language of the subtype, and is a subset of **locale**. |
| icon | string | Yes | Yes | Icon of the input method subtype, which can be obtained with **iconId** queried. |
| iconId | number | Yes | Yes | Icon ID of the input method subtype. Used to load the subtype icon through the resource ID. |
| extra | object | No | Yes | Other information about the input method subtype.<br/>NOTE<br/>- Since API version 10, this is an optional parameter.|

### Parameter Usage Suggestions

**name** parameter:

- Meaning/Function: Bundle name of the app to which the input method subtype belongs, used to identify which input method app the subtype belongs to.

- Value range: A string identical to the **bundleName** configured in the **module.json5** file of the input method app.

- Precautions: **name** must strictly match the **bundleName** of the input method app (case‑sensitive). Otherwise, the system cannot correctly match the subtype with the input method app. You can obtain the correct bundle name by checking the **module.json5** configuration file of the input method app.

**id** parameter:

- Meaning/Function: ID of the input method subtype, used to uniquely identify a subtype within the same input method app.

- Value range: A string identical to the **subtype id** configured in the **module.json5** file of the input method app.

- Usage with related parameters: `name` and `id` together uniquely identify an input method subtype. `name` identifies the input method app to which the subtype belongs, and `id` identifies the specific subtype within that app. When switching subtypes (for example, through `switchCurrentInputMethodSubtype`), an `InputMethodSubtype` object with matching `name` and `id` must be provided.

**locale** parameter:

- Meaning/Function: The **locale** identifier of the input method subtype, which follows the ICU Locale format.

- Value range: A string in the ICU Locale format or POSIX format. The ICU standard format is '*language code*_*country code*' (for example, **'zh_CN'**, **'en_US'**, and **'ja_JP'**), and the POSIX style is '*language code*-*country code*' (for example, **'zh-CN'**, **'en-US'**, and **'ja-JP'**). The language code follows the ISO 639 standard (two-letter lowercase code), and the country code follows the ISO 3166 standard (two-letter uppercase code).

- Format examples: **'zh-CN'** (Simplified Chinese, China), **'en-US'** (English, United States), **'zh-TW'** (Traditional Chinese, Taiwan, China), and **'ja-JP'** (Japanese, Japan).

**language** parameter:

- Meaning/Function: The language identifier of the input method subtype, which is the language code part of the locale.

- Value range: A language code string that follows the ISO 639 standard, such as **'zh'** (Chinese), **'en'** (English), and **'ja'** (Japanese).

- Usage with related parameters: `language` is associated with `locale` as `language` is the language code part of `locale`. For example, when **locale** is **'zh-CN'**, **language** is usually **'zh'**. The two should stay consistent, and **language** should not conflict with the language code in **locale**.

**mode** parameter:

- Meaning/Function: The mode of the input method subtype, which describes the uppercase/lowercase state of the keyboard.

- Usage scenarios: This is an optional parameter. If the parameter is not specified, the input method app uses the default mode. Use this parameter to configure the keyboard's uppercase or lowercase mode, for example, to set the **'lower'** mode for password input scenarios.

- Use effect: When **'upper'** is set, the input method app switches the keyboard to uppercase mode accordingly; when **'lower'** is set, it switches to lowercase mode.

- Value range: **'upper'** (uppercase) or **'lower'** (lowercase).

**label** parameter:

- Meaning/Function: The label of the input method subtype, used to display the subtype name in the UI.

- Usage scenarios:  This is an optional parameter. If the parameter is not specified, the system may use the subtype's **language** or **locale** as the default display name. Use this parameter to configure a more readable subtype name that is displayed on the settings page or in the switching list.

- Usage with related parameters: `label` is associated with `labelId` as they are used for subtype label display. `label` is a direct text label, while `labelId` is a resource ID label that supports multilingual globalization. If both are set, the internationalized text loaded by `labelId` takes precedence.

**labelId** parameter:

- Meaning/Function: The label resource ID of the input method subtype, used to load the label text through a resource ID.

- Usage scenarios: This is an optional parameter. Use it when internationalized display of the subtype label is required in multilingual scenarios, which is more suitable for multilingual environments than `label`.

- Value range: A resource ID value of the number type.

**icon** and **iconId** parameters:

- Specification restriction: The subtype icon cannot be obtained or displayed through these two parameters.

**extra** parameter:

- Specification restriction: It is an optional parameter since API version 10.