# Crypto_DataBlob

<!--Kit: Crypto Architecture Kit-->
<!--Subsystem: Security-->
<!--Owner: @zxz--3-->
<!--Designer: @lanming-->
<!--Tester: @PAFT-->
<!--Adviser: @zengyawen-->
<!-- md-trans-meta sourceCommit=4a27fe9fcb9698d710b4ee8875dc73cdcfac03c3 translatedAt=2026-09-14T01:56:25.420Z pushedAt=2026-09-14T11:58:47.877Z -->

```c
typedef struct Crypto_DataBlob {...} Crypto_DataBlob
```

## Overview

Defines the data used for encryption and decryption.

**Since**: 12

**Related module**: [CryptoCommonApi](capi-cryptocommonapi.md)

**Header file**: [crypto_common.h](capi-crypto-common-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| uint8_t *data | Data buffer. |
| size_t len | Data length. |


