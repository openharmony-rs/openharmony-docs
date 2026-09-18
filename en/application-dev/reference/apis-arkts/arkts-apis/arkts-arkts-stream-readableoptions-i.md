# ReadableOptions

Describes the options used in the **Readable** constructor.

**Since:** 12

**System capability:** SystemCapability.Utils.Lang

## Modules to Import

```TypeScript
import { stream } from '@kit.ArkTS';
```

## encoding

```TypeScript
encoding?: string
```

Encoding format. If an invalid string is input, an exception is thrown in the **Readable** constructor.

The following formats are supported: utf-8, UTF-8, GBK, GB2312, gb2312, GB18030, gb18030, ibm866, iso-8859-2, iso -8859-3, iso-8859-4, iso-8859-5, iso-8859-6, iso-8859-7, iso-8859-8, iso-8859-8-i, iso-8859-10, iso-8859-13, iso- 8859-14, iso-8859-15, koi8-r, koi8-u, macintosh, windows-874, windows-1250, windows-1251, windows-1252, windows-1 253, windows-1254, windows-1255, windows-1256, windows-1257, windows-1258, gbk, big5, euc-jp, iso-2022-jp, shift_jis, euc-kr, x-mac-cyrillic, utf-16be, and utf-16le.

The default value is **'utf-8'**.

**Type:** string

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang
