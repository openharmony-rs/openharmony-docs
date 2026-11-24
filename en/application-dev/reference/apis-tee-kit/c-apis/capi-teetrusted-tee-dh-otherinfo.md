# TEE_DH_OtherInfo

```c
typedef struct TEE_DH_OtherInfo {...} TEE_DH_OtherInfo
```

## Overview

Defines a struct for TEE_DH_OtherInfo.

<!--Device-typedef struct TEE_DH_OtherInfo {...} TEE_DH_OtherInfo--><!--Device-typedef struct TEE_DH_OtherInfo {...} TEE_DH_OtherInfo-End-->

**System capability**: SystemCapability.Tee.TeeClient

**Since**: 20

**Related module**: [TeeTrusted](capi-tee-kit-teetrusted.md)

**Header file**: [tee_crypto_api.h](capi-tee-crypto-api-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| uint8_t algorithm_id[TEE_DH_MAX_SIZE_OF_OTHER_INFO] | object ID(OID)<br><!--Device-uint8_t algorithm_id[TEE_DH_MAX_SIZE_OF_OTHER_INFO]--><!--Device-uint8_t algorithm_id[TEE_DH_MAX_SIZE_OF_OTHER_INFO]-End--> |
| uint32_t size_of_algorithm_id | length of AlgorithmID<br><!--Device-uint32_t size_of_algorithm_id--><!--Device-uint32_t size_of_algorithm_id-End--> |
| uint8_t party_u_info[TEE_DH_MAX_SIZE_OF_OTHER_INFO] | public info of sender<br><!--Device-uint8_t party_u_info[TEE_DH_MAX_SIZE_OF_OTHER_INFO]--><!--Device-uint8_t party_u_info[TEE_DH_MAX_SIZE_OF_OTHER_INFO]-End--> |
| uint32_t size_of_party_u_info | length of PartyUInfo<br><!--Device-uint32_t size_of_party_u_info--><!--Device-uint32_t size_of_party_u_info-End--> |
| uint8_t party_v_info[TEE_DH_MAX_SIZE_OF_OTHER_INFO] | public info of receiver<br><!--Device-uint8_t party_v_info[TEE_DH_MAX_SIZE_OF_OTHER_INFO]--><!--Device-uint8_t party_v_info[TEE_DH_MAX_SIZE_OF_OTHER_INFO]-End--> |
| uint32_t size_of_party_v_info | length of PartyVInfo<br><!--Device-uint32_t size_of_party_v_info--><!--Device-uint32_t size_of_party_v_info-End--> |
| uint8_t supp_priv_info[TEE_DH_MAX_SIZE_OF_OTHER_INFO] | shared private info<br><!--Device-uint8_t supp_priv_info[TEE_DH_MAX_SIZE_OF_OTHER_INFO]--><!--Device-uint8_t supp_priv_info[TEE_DH_MAX_SIZE_OF_OTHER_INFO]-End--> |
| uint32_t size_of_supp_priv_info | length of SuppPrivInfo<br><!--Device-uint32_t size_of_supp_priv_info--><!--Device-uint32_t size_of_supp_priv_info-End--> |
| uint8_t supp_pub_info[TEE_DH_MAX_SIZE_OF_OTHER_INFO] | shared public info<br><!--Device-uint8_t supp_pub_info[TEE_DH_MAX_SIZE_OF_OTHER_INFO]--><!--Device-uint8_t supp_pub_info[TEE_DH_MAX_SIZE_OF_OTHER_INFO]-End--> |
| uint32_t size_of_supp_pub_info | length of SuppPubInfo<br><!--Device-uint32_t size_of_supp_pub_info--><!--Device-uint32_t size_of_supp_pub_info-End--> |


