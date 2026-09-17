# RevocationCheckOptions

Enumerates the options for checking the certificate revocation status.

**Since:** 12

**System capability:** SystemCapability.Security.Cert

## REVOCATION_CHECK_OPTION_PREFER_OCSP

```TypeScript
REVOCATION_CHECK_OPTION_PREFER_OCSP = 0
```

Use OCSP over CRL (default).

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Security.Cert

## REVOCATION_CHECK_OPTION_ACCESS_NETWORK

```TypeScript
REVOCATION_CHECK_OPTION_ACCESS_NETWORK = 1
```

Obtain the CRL/OCSP response over the network. By default, it is disabled. Only the first CRL distribution point address can be obtained from the CDP extension of the certificate to check the certificate revocation status, or the first OCSP server address can be obtained from the AIA extension of the certificate to check the certificate revocation status. Moreover, only HTTP is supported. You must declare the ohos.permission.INTERNET permission.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Security.Cert

## REVOCATION_CHECK_OPTION_FALLBACK_NO_PREFER

```TypeScript
REVOCATION_CHECK_OPTION_FALLBACK_NO_PREFER = 2
```

This parameter is valid when the **ACCESS_NETWORK** option is enabled. It allows the alternative solution to be used to obtain the certificate revocation status if the preferred solution cannot be used due to network problems.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Security.Cert

## REVOCATION_CHECK_OPTION_FALLBACK_LOCAL

```TypeScript
REVOCATION_CHECK_OPTION_FALLBACK_LOCAL = 3
```

This parameter is valid when the **ACCESS_NETWORK** option is enabled. It allows the locally configured CRL/OCSP response to be used to check the certificate revocation status if the online CRL/OCSP response cannot be used due to network problems.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Security.Cert

## REVOCATION_CHECK_OPTION_CHECK_INTERMEDIATE_CA_ONLINE

```TypeScript
REVOCATION_CHECK_OPTION_CHECK_INTERMEDIATE_CA_ONLINE = 4
```

This parameter is valid when the **ACCESS_NETWORK** option is enabled. If this capability is enabled, the system continues to check the revocation status of the intermediate certificate if the OCSP or CRL check of the leaf certificate succeeds. This capability is disabled by default.

> **NOTE:** 
> 
> This capability and **REVOCATION_CHECK_OPTION_LOCAL_CRL_ONLY_CHECK_END_ENTITY_CERT** cannot be enabled at
> the same time.

**Since:** 22

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.Security.Cert

## REVOCATION_CHECK_OPTION_LOCAL_CRL_ONLY_CHECK_END_ENTITY_CERT

```TypeScript
REVOCATION_CHECK_OPTION_LOCAL_CRL_ONLY_CHECK_END_ENTITY_CERT = 5
```

If this capability is enabled, the system checks the revocation status of the leaf certificate based on the local CRL. This capability is disabled by default.

> **NOTE:** 
> 
> This capability and **REVOCATION_CHECK_OPTION_CHECK_INTERMEDIATE_CA_ONLINE** cannot be enabled at the same
> time.

**Since:** 22

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.Security.Cert

## REVOCATION_CHECK_OPTION_IGNORE_NETWORK_ERROR

```TypeScript
REVOCATION_CHECK_OPTION_IGNORE_NETWORK_ERROR = 6
```

If this capability is enabled, the system ignores the network unreachable error when obtaining the CRL or OCSP response over the network for revocation status check. This capability is disabled by default. By default, the network unreachable error may cause certificate chain validation failure.

**Since:** 23

**Atomic service API:** This API can be used in atomic services since API version 23.

**System capability:** SystemCapability.Security.Cert
