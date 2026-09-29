# Normalizer

```TypeScript
export class Normalizer
```

Provides the text normalization capabilities.

**Since:** 10

<!--Device-i18n-export class Normalizer--><!--Device-i18n-export class Normalizer-End-->

**System capability:** SystemCapability.Global.I18n

## Modules to Import

```TypeScript
import { i18n } from '@kit.LocalizationKit';
```

## getInstance

```TypeScript
static getInstance(mode: NormalizerMode): Normalizer
```

Obtains a **Normalizer** object.

**Since:** 10

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-Normalizer-static getInstance(mode: NormalizerMode): Normalizer--><!--Device-Normalizer-static getInstance(mode: NormalizerMode): Normalizer-End-->

**System capability:** SystemCapability.Global.I18n

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| mode | [NormalizerMode](arkts-localization-i18n-normalizermode-e.md) | Yes | Text normalization mode. |

**Return value:**

| Type | Description |
| --- | --- |
| [Normalizer](arkts-localization-i18n-normalizer-c.md) | **Normalizer** object for text normalization. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { i18n } from '@kit.LocalizationKit';

try {
  let normalizer: i18n.Normalizer = i18n.Normalizer.getInstance(i18n.NormalizerMode.NFC);
} catch (error) {
  let err: BusinessError = error as BusinessError;
  console.error(`call Normalizer.getInstance failed, error code: ${err.code}, message: ${err.message}.`);
}
```

## normalize

```TypeScript
normalize(text: string): string
```

Normalizes input strings.

**Since:** 10

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-Normalizer-normalize(text: string): string--><!--Device-Normalizer-normalize(text: string): string-End-->

**System capability:** SystemCapability.Global.I18n

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| text | string | Yes | Input text. |

**Return value:**

| Type | Description |
| --- | --- |
| string | Normalized strings. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { i18n } from '@kit.LocalizationKit';

try {
  let normalizer: i18n.Normalizer = i18n.Normalizer.getInstance(i18n.NormalizerMode.NFC);
  let normalizedText: string = normalizer.normalize('\u1E9B\u0323'); // normalizedText = 'ẛ̣'
} catch (error) {
  let err: BusinessError = error as BusinessError;
  console.error(`call Normalizer.getInstance failed, error code: ${err.code}, message: ${err.message}.`);
}
```
