# peration_ae_init

```c
typedef struct peration_ae_init {...} operation_ae_init
```

## Overview

Defines the AE initialization data.

<!--Device-struct peration_ae_init {...}--><!--Device-struct peration_ae_init {...}-End-->

**System capability**: SystemCapability.Tee.TeeClient

**Since**: 20

**Related module**: [TeeTrusted](capi-tee-kit-teetrusted.md)

**Header file**: [tee_crypto_api.h](capi-tee-crypto-api-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| void *nonce | nonce<br><!--Device-void *nonce--><!--Device-void *nonce-End--> |
| size_t nonce_len | Leng of nonce<br><!--Device-size_t nonce_len--><!--Device-size_t nonce_len-End--> |
| uint32_t tag_len | Length of the tag<br><!--Device-uint32_t tag_len--><!--Device-uint32_t tag_len-End--> |
| size_t aad_len | Length of the additional authenticated data (AAD)<br><!--Device-size_t aad_len--><!--Device-size_t aad_len-End--> |
| size_t payload_len | Length of the payload<br><!--Device-size_t payload_len--><!--Device-size_t payload_len-End--> |


