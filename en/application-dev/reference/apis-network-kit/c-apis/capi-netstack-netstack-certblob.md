# NetStack_CertBlob

```c
struct NetStack_CertBlob {...}
```

## Overview

Defines the certificate data structure.

<!--Device-struct NetStack_CertBlob {...}--><!--Device-struct NetStack_CertBlob {...}-End-->

**System capability**: SystemCapability.Communication.NetStack

**Since**: 11

**Related module**: [netstack](capi-network-kit-netstack.md)

**Header file**: [net_ssl_c_type.h](capi-net-ssl-c-type-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| enum [NetStack_CertType](capi-net-ssl-c-type-h.md#netstack_certtype) type | Certificate type.<br><!--Device-enum NetStack_CertType type--><!--Device-enum NetStack_CertType type-End--> |
| uint32_t size | Certificate content length.<br><!--Device-uint32_t size--><!--Device-uint32_t size-End--> |
| uint8_t *data | Certificate data.<br><!--Device-uint8_t *data--><!--Device-uint8_t *data-End--> |


