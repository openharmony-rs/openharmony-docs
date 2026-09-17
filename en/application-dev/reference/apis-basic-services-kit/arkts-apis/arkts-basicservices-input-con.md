# Constants

## ACTIVATED_INPUT_METHOD_SUB_MODE

```TypeScript
const ACTIVATED_INPUT_METHOD_SUB_MODE: string
```

Indicates the default input method keyboard type and its ID.

**Type:** string

**Since:** 7

**System capability:** SystemCapability.Applications.Settings.Core

## ACTIVATED_INPUT_METHODS

```TypeScript
const ACTIVATED_INPUT_METHODS: string
```

Indicates the list of input methods that have been activated.

<p>The list is a string that contains the IDs of activated input methods. The IDs are separated by colons (:), and keyboardTypes of an input method are separated by semicolons (;). An example format is `ima0:keyboardType0;keyboardType1;ima1:ima2:keyboardTypes0`. The type of &lt;b&gt;imaID&lt;/b&gt; is ElementName, and the type of &lt;b&gt;keyboard&lt;/b&gt; is int.

**Type:** string

**Since:** 7

**Deprecated since:** 21

**System capability:** SystemCapability.Applications.Settings.Core

## AUTO_CAPS_TEXT_INPUT

```TypeScript
const AUTO_CAPS_TEXT_INPUT: string
```

Specifies whether automatic capitalization is enabled for the text editor.

<p>If the value is `0`, automatic capitalization is disabled. If the value `1`, automatic capitalization is enabled.

**Type:** string

**Since:** 7

**Deprecated since:** 21

**System capability:** SystemCapability.Applications.Settings.Core

## AUTO_PUNCTUATE_TEXT_INPUT

```TypeScript
const AUTO_PUNCTUATE_TEXT_INPUT: string
```

Specifies whether automatic punctuation is enabled for the text editor. Automatic punctuation enables the text editor to convert two spaces into a period (.) and a space.

<p>If the value is `0`, automatic punctuation is disabled. If the value `1`, automatic punctuation is enabled.

**Type:** string

**Since:** 7

**Deprecated since:** 21

**System capability:** SystemCapability.Applications.Settings.Core

## AUTO_REPLACE_TEXT_INPUT

```TypeScript
const AUTO_REPLACE_TEXT_INPUT: string
```

Specifies whether autocorrect is enabled for the text editor. Autocorrect enables the text editor to correct typos.

<p>If the value is `0`, autocorrect is disabled. If the value `1`, autocorrect is enabled.

**Type:** string

**Since:** 7

**Deprecated since:** 21

**System capability:** SystemCapability.Applications.Settings.Core

## DEFAULT_INPUT_METHOD

```TypeScript
const DEFAULT_INPUT_METHOD: string
```

Indicates the default input method and its ID.

**Type:** string

**Since:** 7

**Deprecated since:** 21

**System capability:** SystemCapability.Applications.Settings.Core

## SELECTOR_VISIBILITY_FOR_INPUT_METHOD

```TypeScript
const SELECTOR_VISIBILITY_FOR_INPUT_METHOD: string
```

Specifies whether the input method selector is visible.

<p>If the value is `1`, the input method selector is visible. If the value is `0`, the input method selector is invisible.

**Type:** string

**Since:** 7

**Deprecated since:** 21

**System capability:** SystemCapability.Applications.Settings.Core

## SHOW_PASSWORD_TEXT_INPUT

```TypeScript
const SHOW_PASSWORD_TEXT_INPUT: string
```

Specifies whether password presentation is enabled in the text editor. Password presentation enables the text editor to show password characters when the user types them.

<p>If the value is `0`, password presentation is disabled. If the value `1`, password presentation is enabled.

**Type:** string

**Since:** 7

**Deprecated since:** 21

**System capability:** SystemCapability.Applications.Settings.Core
