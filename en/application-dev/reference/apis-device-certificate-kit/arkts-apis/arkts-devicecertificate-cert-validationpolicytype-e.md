# ValidationPolicyType

```TypeScript
enum ValidationPolicyType
```

Enumerates the types of the online certificate chain validation policy.

**Since:** 12

<!--Device-cert-enum ValidationPolicyType--><!--Device-cert-enum ValidationPolicyType-End-->

**System capability:** SystemCapability.Security.Cert

## VALIDATION_POLICY_TYPE_X509

```TypeScript
VALIDATION_POLICY_TYPE_X509 = 0
```

Do not verify **sslHostname** or **dNSName** in the certificate. It is the default value.

**Since:** 12

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-ValidationPolicyType-VALIDATION_POLICY_TYPE_X509 = 0--><!--Device-ValidationPolicyType-VALIDATION_POLICY_TYPE_X509 = 0-End-->

**System capability:** SystemCapability.Security.Cert

## VALIDATION_POLICY_TYPE_SSL

```TypeScript
VALIDATION_POLICY_TYPE_SSL = 1
```

Verify **sslHostname** or **dNSName** in the certificate.

**Since:** 12

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-ValidationPolicyType-VALIDATION_POLICY_TYPE_SSL = 1--><!--Device-ValidationPolicyType-VALIDATION_POLICY_TYPE_SSL = 1-End-->

**System capability:** SystemCapability.Security.Cert
