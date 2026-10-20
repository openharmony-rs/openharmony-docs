# @ohos.InputMethodSubtype(Input Method Subtype)

## Modules to Import

```TypeScript
import { InputMethodSubtype } from '@kit.IMEKit';
```

## Summary

### Interfaces

| Name | Description |
| --- | --- |
| [InputMethodSubtype](arkts-ime-inputmethodsubtype-i.md) | The **@ohos.InputMethodSubtype** module provides data definitions for input method subtype properties. It supports describing subtype information of an input method for different languages or modes. <br> <br>This module is the subtype data module of the input method framework. It defines the `InputMethodSubtype` interface, which is used to describe a specific input mode or language of an input method, such as Chinese keyboard, an English keyboard, or uppercase-mode keyboard. Each subtype represents the form of the input method in a specific language or mode. <br> <br>This module provides capabilities for describing input method subtype properties. You can use `InputMethodSubtype` to obtain subtype identifiers (`id`, `name`), locale and language information (`locale`, `language`), display label (`label`), mode (`mode`: uppercase/lowercase), icon, and other properties. These are used for identification, display, and switching of input‑method subtypes. <br> <br>Use this module when you need to query, display, or switch between different language‑ or mode‑based subtypes of an input method. Typical scenarios include: the system settings app displays a list of input method subtypes for user selection; an input‑method app switches languages or modes according to subtype information; an app obtains information about the current input method subtype. <br> <br>`InputMethodSubtype` is a pure data definition module. Its objects are created and returned by the system framework, and cannot be constructed by you. Typical cross‑module usage process: <br> <br>1. Edit box app side (`@ohos.inputMethod` module): Queries the list of input method subtypes via `InputMethodSetting.listInputMethodSubtype()`, and switches to the specified subtype via `inputMethod.switchCurrentInputMethodSubtype()`. 2. Input method app side (`@ohos.inputMethodEngine` module): Listens for subtype switch events through `InputMethodAbility.on('setSubtype')`. The callback parameter is an `InputMethodSubtype` object, based on which the keyboard layout and language can be adjusted. <br> <br>Core open capabilities of this module are provided by the key interface below: <br> |
