# TEE_DH_OtherInfo

```c
typedef struct TEE_DH_OtherInfo {...} TEE_DH_OtherInfo
```

## Overview

Defines a struct for TEE_DH_OtherInfo.

**Since**: 20

**Related module**: [TeeTrusted](capi-teetrusted.md)

**Header file**: [tee_crypto_api.h](capi-tee-crypto-api-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| uint8_t algorithm_id[TEE_DH_MAX_SIZE_OF_OTHER_INFO] | object ID(OID) |
| uint32_t size_of_algorithm_id | length of AlgorithmID |
| uint8_t party_u_info[TEE_DH_MAX_SIZE_OF_OTHER_INFO] | public info of sender |
| uint32_t size_of_party_u_info | length of PartyUInfo |
| uint8_t party_v_info[TEE_DH_MAX_SIZE_OF_OTHER_INFO] | public info of receiver |
| uint32_t size_of_party_v_info | length of PartyVInfo |
| uint8_t supp_priv_info[TEE_DH_MAX_SIZE_OF_OTHER_INFO] | shared private info |
| uint32_t size_of_supp_priv_info | length of SuppPrivInfo |
| uint8_t supp_pub_info[TEE_DH_MAX_SIZE_OF_OTHER_INFO] | shared public info |
| uint32_t size_of_supp_pub_info | length of SuppPubInfo |


