# InputMethodSubtype

```TypeScript
export default interface InputMethodSubtype
```

The **@ohos.InputMethodSubtype** module provides data definitions for input method subtype properties. It supports describing subtype information of an input method for different languages or modes. <br> <br>This module is the subtype data module of the input method framework. It defines the `InputMethodSubtype` interface, which is used to describe a specific input mode or language of an input method, such as Chinese keyboard, an English keyboard, or uppercase-mode keyboard. Each subtype represents the form of the input method in a specific language or mode. <br> <br>This module provides capabilities for describing input method subtype properties. You can use `InputMethodSubtype` to obtain subtype identifiers (`id`, `name`), locale and language information (`locale`, `language`), display label (`label`), mode (`mode`: uppercase/lowercase), icon, and other properties. These are used for identification, display, and switching of input‑method subtypes. <br> <br>Use this module when you need to query, display, or switch between different language‑ or mode‑based subtypes of an input method. Typical scenarios include: the system settings app displays a list of input method subtypes for user selection; an input‑method app switches languages or modes according to subtype information; an app obtains information about the current input method subtype. <br> <br>`InputMethodSubtype` is a pure data definition module. Its objects are created and returned by the system framework, and cannot be constructed by you. Typical cross‑module usage process: <br> <br>1. Edit box app side (`@ohos.inputMethod` module): Queries the list of input method subtypes via `InputMethodSetting.listInputMethodSubtype()`, and switches to the specified subtype via `inputMethod.switchCurrentInputMethodSubtype()`.
2. Input method app side (`@ohos.inputMethodEngine` module): Listens for subtype switch events through `InputMethodAbility.on('setSubtype')`.
The callback parameter is an `InputMethodSubtype` object, based on which the keyboard layout and language can be adjusted. <br> <br>Core open capabilities of this module are provided by the key interface below: <br>

| Name | Description |  
|---|---|  
| InputMethodSubtype | Interface for input method subtype properties, which describes a specific language or mode form of an input method.Mandatory properties: `name` (app bundle name), `id` (subtype ID), `locale` (locale), `language` (language). Optional properties: `label` (label), `labelId` (label resource ID), `mode` (uppercase/lowercase mode), `icon` (icon), `iconId` (icon ID), and `extra` (extra information). | <br> <br>This module is a pure data definition module. As subtype description data, `InputMethodSubtype` must be used together with APIs from other modules. Typical usage combinations: query and switch subtypes via `@ohos.inputMethod` module using `InputMethodSetting`; listen for subtype switch events via `InputMethodAbility` in the `@ohos.inputMethodEngine` module. <br> <br>  
> **NOTE:** <br>
> <br>
> `InputMethodSubtype` objects are created and returned by the system framework. You obtain these objects through <br>
> query APIs of other modules and cannot construct them directly.

**Since:** 9

<!--Device-unnamed-export default interface InputMethodSubtype--><!--Device-unnamed-export default interface InputMethodSubtype-End-->

**System capability:** SystemCapability.MiscServices.InputMethodFramework

## Modules to Import

```TypeScript
import { InputMethodSubtype } from '@kit.IMEKit';
```

## extra

```TypeScript
extra?: object
```

Other information about the input method subtype. <br> <br>Description: <br> <br>- This parameter is optional since API version 10.

**Type:** object

**Since:** 9

<!--Device-InputMethodSubtype-extra?: object--><!--Device-InputMethodSubtype-extra?: object-End-->

**System capability:** SystemCapability.MiscServices.InputMethodFramework

## icon

```TypeScript
readonly icon?: string
```

Icon of the input method subtype, which can be obtained by querying iconId.

**Type:** string

**Since:** 9

<!--Device-InputMethodSubtype-readonly icon?: string--><!--Device-InputMethodSubtype-readonly icon?: string-End-->

**System capability:** SystemCapability.MiscServices.InputMethodFramework

## iconId

```TypeScript
readonly iconId?: number
```

Icon ID of the input method subtype. Used to load the subtype icon through the resource ID.

**Type:** number

**Since:** 9

<!--Device-InputMethodSubtype-readonly iconId?: double--><!--Device-InputMethodSubtype-readonly iconId?: double-End-->

**System capability:** SystemCapability.MiscServices.InputMethodFramework

## id

```TypeScript
readonly id: string
```

ID of the input method subtype. It must be consistent with the subtype ID configured in **module.json5** of the input method app, and is used to uniquely identify a subtype within the same input method app.

**Type:** string

**Since:** 9

<!--Device-InputMethodSubtype-readonly id: string--><!--Device-InputMethodSubtype-readonly id: string-End-->

**System capability:** SystemCapability.MiscServices.InputMethodFramework

## label

```TypeScript
readonly label?: string
```

Label of the input method subtype. Used to display the subtype name in the UI, such as "Chinese (Simplified)" and "English".

**Type:** string

**Since:** 9

<!--Device-InputMethodSubtype-readonly label?: string--><!--Device-InputMethodSubtype-readonly label?: string-End-->

**System capability:** SystemCapability.MiscServices.InputMethodFramework

## labelId

```TypeScript
readonly labelId?: number
```

Label resource ID of the input method subtype. Used to load the label text through the resource ID, supporting internationalized label display in multi-language scenarios.

**Type:** number

**Since:** 10

<!--Device-InputMethodSubtype-readonly labelId?: double--><!--Device-InputMethodSubtype-readonly labelId?: double-End-->

**System capability:** SystemCapability.MiscServices.InputMethodFramework

## language

```TypeScript
readonly language: string
```

Language of the input method subtype, such as 'zh' (Chinese) and 'en' (English). Used to identify the language of the subtype, and is a subset of locale.

**Type:** string

**Since:** 9

<!--Device-InputMethodSubtype-readonly language: string--><!--Device-InputMethodSubtype-readonly language: string-End-->

**System capability:** SystemCapability.MiscServices.InputMethodFramework

## locale

```TypeScript
readonly locale: string
```

Locale of the input method subtype. It follows the ICU Locale format (underscore-separated, such as 'zh_CN') and is also compatible with the POSIX style (hyphen-separated, such as 'zh-CN'). Used to identify the language and region of the subtype.

**Type:** string

**Since:** 9

<!--Device-InputMethodSubtype-readonly locale: string--><!--Device-InputMethodSubtype-readonly locale: string-End-->

**System capability:** SystemCapability.MiscServices.InputMethodFramework

## mode

```TypeScript
readonly mode?: 'upper' | 'lower'
```

Mode of the input method subtype, including upper (uppercase) and lower (lowercase). Used to describe the uppercase /lowercase state mode of the keyboard.

**Type:** 'upper' &#124; 'lower'

**Since:** 9

<!--Device-InputMethodSubtype-readonly mode?: 'upper' | 'lower'--><!--Device-InputMethodSubtype-readonly mode?: 'upper' | 'lower'-End-->

**System capability:** SystemCapability.MiscServices.InputMethodFramework

## name

```TypeScript
readonly name: string
```

Bundle name of the app to which the input method subtype belongs. It must be consistent with the **bundleName** configured in **module.json5** of the input method app, and is used to identify which input method app the subtype belongs to.

**Type:** string

**Since:** 9

<!--Device-InputMethodSubtype-readonly name: string--><!--Device-InputMethodSubtype-readonly name: string-End-->

**System capability:** SystemCapability.MiscServices.InputMethodFramework
