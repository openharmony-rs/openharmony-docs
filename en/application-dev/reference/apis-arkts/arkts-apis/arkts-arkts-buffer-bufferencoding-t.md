# BufferEncoding

```TypeScript
type BufferEncoding = 'ascii' | 'utf8' | 'utf-8' | 'utf16le' | 'ucs2' | 'ucs-2' | 'base64' | 'base64url' | 'latin1' | 'binary' | 'hex'
```

Enumerates the supported encoding formats.

**Since:** 9

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 11.

<!--Device-buffer-type BufferEncoding = 'ascii' | 'utf8' | 'utf-8' | 'utf16le' | 'ucs2' | 'ucs-2' | 'base64' | 'base64url' | 'latin1' | 'binary' | 'hex'--><!--Device-buffer-type BufferEncoding = 'ascii' | 'utf8' | 'utf-8' | 'utf16le' | 'ucs2' | 'ucs-2' | 'base64' | 'base64url' | 'latin1' | 'binary' | 'hex'-End-->

**System capability:** SystemCapability.Utils.Lang

| Type | Description |
| --- | --- |
| 'ascii' | ASCII format. |
| 'utf8' | UTF-8 format. |
| 'utf-8' | UTF-8 format. |
| 'utf16le' | UTF-16LE format. |
| 'ucs2' | Alias of UTF-16LE. |
| 'ucs-2' | Alias of UTF-16LE. |
| 'base64' | Base64 format. |
| 'base64url' | Base64URL format. |
| 'latin1' | Alias of iso-8859-1, which is backward compatible with the ASCII format. |
| 'binary' | Binary format. |
| 'hex' | Hexadecimal format. |
