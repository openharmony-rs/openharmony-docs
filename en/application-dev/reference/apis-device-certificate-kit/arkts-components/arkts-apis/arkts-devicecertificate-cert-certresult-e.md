# CertResult

```TypeScript
enum CertResult
```

Enumerates the error codes.

**Since:** 9

<!--Device-cert-enum CertResult--><!--Device-cert-enum CertResult-End-->

**System capability:** SystemCapability.Security.Cert

## INVALID_PARAMS

```TypeScript
INVALID_PARAMS = 401
```

Invalid parameters.

**Since:** 9

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-CertResult-INVALID_PARAMS = 401--><!--Device-CertResult-INVALID_PARAMS = 401-End-->

**System capability:** SystemCapability.Security.Cert

## NOT_SUPPORT

```TypeScript
NOT_SUPPORT = 801
```

This operation is not supported.

**Since:** 9

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-CertResult-NOT_SUPPORT = 801--><!--Device-CertResult-NOT_SUPPORT = 801-End-->

**System capability:** SystemCapability.Security.Cert

## ERR_OUT_OF_MEMORY

```TypeScript
ERR_OUT_OF_MEMORY = 19020001
```

Memory error.

**Since:** 9

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-CertResult-ERR_OUT_OF_MEMORY = 19020001--><!--Device-CertResult-ERR_OUT_OF_MEMORY = 19020001-End-->

**System capability:** SystemCapability.Security.Cert

## ERR_RUNTIME_ERROR

```TypeScript
ERR_RUNTIME_ERROR = 19020002
```

Runtime error.

**Since:** 9

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-CertResult-ERR_RUNTIME_ERROR = 19020002--><!--Device-CertResult-ERR_RUNTIME_ERROR = 19020002-End-->

**System capability:** SystemCapability.Security.Cert

## ERR_PARAMETER_CHECK_FAILED

```TypeScript
ERR_PARAMETER_CHECK_FAILED = 19020003
```

Parameter check failed.

**Since:** 20

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 20.

<!--Device-CertResult-ERR_PARAMETER_CHECK_FAILED = 19020003--><!--Device-CertResult-ERR_PARAMETER_CHECK_FAILED = 19020003-End-->

**System capability:** SystemCapability.Security.Cert

## ERR_CRYPTO_OPERATION

```TypeScript
ERR_CRYPTO_OPERATION = 19030001
```

Crypto operation error.

**Since:** 9

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-CertResult-ERR_CRYPTO_OPERATION = 19030001--><!--Device-CertResult-ERR_CRYPTO_OPERATION = 19030001-End-->

**System capability:** SystemCapability.Security.Cert

## ERR_CERT_SIGNATURE_FAILURE

```TypeScript
ERR_CERT_SIGNATURE_FAILURE = 19030002
```

The certificate signature verification failed.

**Since:** 9

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-CertResult-ERR_CERT_SIGNATURE_FAILURE = 19030002--><!--Device-CertResult-ERR_CERT_SIGNATURE_FAILURE = 19030002-End-->

**System capability:** SystemCapability.Security.Cert

## ERR_CERT_NOT_YET_VALID

```TypeScript
ERR_CERT_NOT_YET_VALID = 19030003
```

The certificate has not taken effect.

**Since:** 9

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-CertResult-ERR_CERT_NOT_YET_VALID = 19030003--><!--Device-CertResult-ERR_CERT_NOT_YET_VALID = 19030003-End-->

**System capability:** SystemCapability.Security.Cert

## ERR_CERT_HAS_EXPIRED

```TypeScript
ERR_CERT_HAS_EXPIRED = 19030004
```

The certificate has expired.

**Since:** 9

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-CertResult-ERR_CERT_HAS_EXPIRED = 19030004--><!--Device-CertResult-ERR_CERT_HAS_EXPIRED = 19030004-End-->

**System capability:** SystemCapability.Security.Cert

## ERR_UNABLE_TO_GET_ISSUER_CERT_LOCALLY

```TypeScript
ERR_UNABLE_TO_GET_ISSUER_CERT_LOCALLY = 19030005
```

Failed to obtain the certificate issuer.

**Since:** 9

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-CertResult-ERR_UNABLE_TO_GET_ISSUER_CERT_LOCALLY = 19030005--><!--Device-CertResult-ERR_UNABLE_TO_GET_ISSUER_CERT_LOCALLY = 19030005-End-->

**System capability:** SystemCapability.Security.Cert

## ERR_KEYUSAGE_NO_CERTSIGN

```TypeScript
ERR_KEYUSAGE_NO_CERTSIGN = 19030006
```

The key cannot be used for signing a certificate.

**Since:** 9

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-CertResult-ERR_KEYUSAGE_NO_CERTSIGN = 19030006--><!--Device-CertResult-ERR_KEYUSAGE_NO_CERTSIGN = 19030006-End-->

**System capability:** SystemCapability.Security.Cert

## ERR_KEYUSAGE_NO_DIGITAL_SIGNATURE

```TypeScript
ERR_KEYUSAGE_NO_DIGITAL_SIGNATURE = 19030007
```

The key cannot be used for a digital signature.

**Since:** 9

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-CertResult-ERR_KEYUSAGE_NO_DIGITAL_SIGNATURE = 19030007--><!--Device-CertResult-ERR_KEYUSAGE_NO_DIGITAL_SIGNATURE = 19030007-End-->

**System capability:** SystemCapability.Security.Cert

## ERR_MAYBE_WRONG_PASSWORD

```TypeScript
ERR_MAYBE_WRONG_PASSWORD = 19030008
```

The password for the private key may be incorrect.

**Since:** 18

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 18.

<!--Device-CertResult-ERR_MAYBE_WRONG_PASSWORD = 19030008--><!--Device-CertResult-ERR_MAYBE_WRONG_PASSWORD = 19030008-End-->

**System capability:** SystemCapability.Security.Cert

## ERR_CERT_UNTRUSTED

```TypeScript
ERR_CERT_UNTRUSTED = 19030009
```

Untrusted certificate.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 26.0.0.

<!--Device-CertResult-ERR_CERT_UNTRUSTED = 19030009--><!--Device-CertResult-ERR_CERT_UNTRUSTED = 19030009-End-->

**System capability:** SystemCapability.Security.Cert

## ERR_CERT_HAS_REVOKED

```TypeScript
ERR_CERT_HAS_REVOKED = 19030010
```

The certificate has been revoked.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 26.0.0.

<!--Device-CertResult-ERR_CERT_HAS_REVOKED = 19030010--><!--Device-CertResult-ERR_CERT_HAS_REVOKED = 19030010-End-->

**System capability:** SystemCapability.Security.Cert

## ERR_UNKNOWN_CRITICAL_EXTENSION

```TypeScript
ERR_UNKNOWN_CRITICAL_EXTENSION = 19030011
```

Unsupported critical extension.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 26.0.0.

<!--Device-CertResult-ERR_UNKNOWN_CRITICAL_EXTENSION = 19030011--><!--Device-CertResult-ERR_UNKNOWN_CRITICAL_EXTENSION = 19030011-End-->

**System capability:** SystemCapability.Security.Cert

## ERR_CERT_HOSTNAME_MISMATCH

```TypeScript
ERR_CERT_HOSTNAME_MISMATCH = 19030012
```

Hostname mismatch in the certificate.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 26.0.0.

<!--Device-CertResult-ERR_CERT_HOSTNAME_MISMATCH = 19030012--><!--Device-CertResult-ERR_CERT_HOSTNAME_MISMATCH = 19030012-End-->

**System capability:** SystemCapability.Security.Cert

## ERR_CERT_EMAIL_ADDRESS_MISMATCH

```TypeScript
ERR_CERT_EMAIL_ADDRESS_MISMATCH = 19030013
```

Email address mismatch in the certificate.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 26.0.0.

<!--Device-CertResult-ERR_CERT_EMAIL_ADDRESS_MISMATCH = 19030013--><!--Device-CertResult-ERR_CERT_EMAIL_ADDRESS_MISMATCH = 19030013-End-->

**System capability:** SystemCapability.Security.Cert

## ERR_CERT_KEYUSAGE_MISMATCH

```TypeScript
ERR_CERT_KEYUSAGE_MISMATCH = 19030014
```

Key usage mismatch in the certificate.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 26.0.0.

<!--Device-CertResult-ERR_CERT_KEYUSAGE_MISMATCH = 19030014--><!--Device-CertResult-ERR_CERT_KEYUSAGE_MISMATCH = 19030014-End-->

**System capability:** SystemCapability.Security.Cert

## ERR_CRL_NOT_FOUND

```TypeScript
ERR_CRL_NOT_FOUND = 19030015
```

Failed to obtain the certificate revocation list.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 26.0.0.

<!--Device-CertResult-ERR_CRL_NOT_FOUND = 19030015--><!--Device-CertResult-ERR_CRL_NOT_FOUND = 19030015-End-->

**System capability:** SystemCapability.Security.Cert

## ERR_CRL_NOT_YET_VALID

```TypeScript
ERR_CRL_NOT_YET_VALID = 19030016
```

The certificate revocation list has not taken effect.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 26.0.0.

<!--Device-CertResult-ERR_CRL_NOT_YET_VALID = 19030016--><!--Device-CertResult-ERR_CRL_NOT_YET_VALID = 19030016-End-->

**System capability:** SystemCapability.Security.Cert

## ERR_CRL_HAS_EXPIRED

```TypeScript
ERR_CRL_HAS_EXPIRED = 19030017
```

The certificate revocation list has expired.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 26.0.0.

<!--Device-CertResult-ERR_CRL_HAS_EXPIRED = 19030017--><!--Device-CertResult-ERR_CRL_HAS_EXPIRED = 19030017-End-->

**System capability:** SystemCapability.Security.Cert

## ERR_CRL_SIGNATURE_FAILURE

```TypeScript
ERR_CRL_SIGNATURE_FAILURE = 19030018
```

Failed to verify the signature of the certificate revocation list.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 26.0.0.

<!--Device-CertResult-ERR_CRL_SIGNATURE_FAILURE = 19030018--><!--Device-CertResult-ERR_CRL_SIGNATURE_FAILURE = 19030018-End-->

**System capability:** SystemCapability.Security.Cert

## ERR_CRL_ISSUER_NOT_FOUND

```TypeScript
ERR_CRL_ISSUER_NOT_FOUND = 19030019
```

Failed to find the issuer of the certificate revocation list.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 26.0.0.

<!--Device-CertResult-ERR_CRL_ISSUER_NOT_FOUND = 19030019--><!--Device-CertResult-ERR_CRL_ISSUER_NOT_FOUND = 19030019-End-->

**System capability:** SystemCapability.Security.Cert

## ERR_OCSP_RESPONSE_NOT_FOUND

```TypeScript
ERR_OCSP_RESPONSE_NOT_FOUND = 19030020
```

Failed to obtain the OCSP response.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 26.0.0.

<!--Device-CertResult-ERR_OCSP_RESPONSE_NOT_FOUND = 19030020--><!--Device-CertResult-ERR_OCSP_RESPONSE_NOT_FOUND = 19030020-End-->

**System capability:** SystemCapability.Security.Cert

## ERR_OCSP_RESPONSE_INVALID

```TypeScript
ERR_OCSP_RESPONSE_INVALID = 19030021
```

Invalid OCSP response.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 26.0.0.

<!--Device-CertResult-ERR_OCSP_RESPONSE_INVALID = 19030021--><!--Device-CertResult-ERR_OCSP_RESPONSE_INVALID = 19030021-End-->

**System capability:** SystemCapability.Security.Cert

## ERR_OCSP_SIGNATURE_FAILURE

```TypeScript
ERR_OCSP_SIGNATURE_FAILURE = 19030022
```

Failed to verify the OCSP signature.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 26.0.0.

<!--Device-CertResult-ERR_OCSP_SIGNATURE_FAILURE = 19030022--><!--Device-CertResult-ERR_OCSP_SIGNATURE_FAILURE = 19030022-End-->

**System capability:** SystemCapability.Security.Cert

## ERR_OCSP_CERT_STATUS_UNKNOWN

```TypeScript
ERR_OCSP_CERT_STATUS_UNKNOWN = 19030023
```

Unknown OCSP certificate status.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 26.0.0.

<!--Device-CertResult-ERR_OCSP_CERT_STATUS_UNKNOWN = 19030023--><!--Device-CertResult-ERR_OCSP_CERT_STATUS_UNKNOWN = 19030023-End-->

**System capability:** SystemCapability.Security.Cert

## ERR_NETWORK_TIMEOUT

```TypeScript
ERR_NETWORK_TIMEOUT = 19030024
```

Network connection timed out.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 26.0.0.

<!--Device-CertResult-ERR_NETWORK_TIMEOUT = 19030024--><!--Device-CertResult-ERR_NETWORK_TIMEOUT = 19030024-End-->

**System capability:** SystemCapability.Security.Cert
