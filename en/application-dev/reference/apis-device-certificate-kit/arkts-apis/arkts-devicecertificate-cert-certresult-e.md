# CertResult

```TypeScript
enum CertResult
```

Enumerates the error codes.

**Since:** 9

<!--Device-cert-enum CertResult--><!--Device-cert-enum CertResult-End-->

**System capability:** SystemCapability.Security.Cert

## ERR_CERT_EMAIL_ADDRESS_MISMATCH

```TypeScript
ERR_CERT_EMAIL_ADDRESS_MISMATCH = 19030013
```

The email address in the certificate is not matched.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-CertResult-ERR_CERT_EMAIL_ADDRESS_MISMATCH = 19030013--><!--Device-CertResult-ERR_CERT_EMAIL_ADDRESS_MISMATCH = 19030013-End-->

**System capability:** SystemCapability.Security.Cert

## ERR_CERT_HAS_EXPIRED

```TypeScript
ERR_CERT_HAS_EXPIRED = 19030004
```

The certificate has expired.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-CertResult-ERR_CERT_HAS_EXPIRED = 19030004--><!--Device-CertResult-ERR_CERT_HAS_EXPIRED = 19030004-End-->

**System capability:** SystemCapability.Security.Cert

## ERR_CERT_HAS_REVOKED

```TypeScript
ERR_CERT_HAS_REVOKED = 19030010
```

This error code is reported if the certificate has been revoked.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-CertResult-ERR_CERT_HAS_REVOKED = 19030010--><!--Device-CertResult-ERR_CERT_HAS_REVOKED = 19030010-End-->

**System capability:** SystemCapability.Security.Cert

## ERR_CERT_HOSTNAME_MISMATCH

```TypeScript
ERR_CERT_HOSTNAME_MISMATCH = 19030012
```

This error code is reported if the hostname is not matched.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-CertResult-ERR_CERT_HOSTNAME_MISMATCH = 19030012--><!--Device-CertResult-ERR_CERT_HOSTNAME_MISMATCH = 19030012-End-->

**System capability:** SystemCapability.Security.Cert

## ERR_CERT_KEYUSAGE_MISMATCH

```TypeScript
ERR_CERT_KEYUSAGE_MISMATCH = 19030014
```

Key usage mismatch in the certificate.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-CertResult-ERR_CERT_KEYUSAGE_MISMATCH = 19030014--><!--Device-CertResult-ERR_CERT_KEYUSAGE_MISMATCH = 19030014-End-->

**System capability:** SystemCapability.Security.Cert

## ERR_CERT_NOT_YET_VALID

```TypeScript
ERR_CERT_NOT_YET_VALID = 19030003
```

The certificate has not taken effect.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-CertResult-ERR_CERT_NOT_YET_VALID = 19030003--><!--Device-CertResult-ERR_CERT_NOT_YET_VALID = 19030003-End-->

**System capability:** SystemCapability.Security.Cert

## ERR_CERT_SIGNATURE_FAILURE

```TypeScript
ERR_CERT_SIGNATURE_FAILURE = 19030002
```

The certificate signature verification failed.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-CertResult-ERR_CERT_SIGNATURE_FAILURE = 19030002--><!--Device-CertResult-ERR_CERT_SIGNATURE_FAILURE = 19030002-End-->

**System capability:** SystemCapability.Security.Cert

## ERR_CERT_UNTRUSTED

```TypeScript
ERR_CERT_UNTRUSTED = 19030009
```

This error code is reported if the certificate is untrusted.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-CertResult-ERR_CERT_UNTRUSTED = 19030009--><!--Device-CertResult-ERR_CERT_UNTRUSTED = 19030009-End-->

**System capability:** SystemCapability.Security.Cert

## ERR_CRL_HAS_EXPIRED

```TypeScript
ERR_CRL_HAS_EXPIRED = 19030017
```

This error code is reported if the CRL has expired.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-CertResult-ERR_CRL_HAS_EXPIRED = 19030017--><!--Device-CertResult-ERR_CRL_HAS_EXPIRED = 19030017-End-->

**System capability:** SystemCapability.Security.Cert

## ERR_CRL_ISSUER_NOT_FOUND

```TypeScript
ERR_CRL_ISSUER_NOT_FOUND = 19030019
```

This error code is reported if the attempt to obtain the CRL issuer fails.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-CertResult-ERR_CRL_ISSUER_NOT_FOUND = 19030019--><!--Device-CertResult-ERR_CRL_ISSUER_NOT_FOUND = 19030019-End-->

**System capability:** SystemCapability.Security.Cert

## ERR_CRL_NOT_FOUND

```TypeScript
ERR_CRL_NOT_FOUND = 19030015
```

This error code is reported if the attempt to obtain the CRL fails.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-CertResult-ERR_CRL_NOT_FOUND = 19030015--><!--Device-CertResult-ERR_CRL_NOT_FOUND = 19030015-End-->

**System capability:** SystemCapability.Security.Cert

## ERR_CRL_NOT_YET_VALID

```TypeScript
ERR_CRL_NOT_YET_VALID = 19030016
```

This error code is reported if the CRL has not taken effect.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-CertResult-ERR_CRL_NOT_YET_VALID = 19030016--><!--Device-CertResult-ERR_CRL_NOT_YET_VALID = 19030016-End-->

**System capability:** SystemCapability.Security.Cert

## ERR_CRL_SIGNATURE_FAILURE

```TypeScript
ERR_CRL_SIGNATURE_FAILURE = 19030018
```

This error code is reported if the CRL signature verification fails.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-CertResult-ERR_CRL_SIGNATURE_FAILURE = 19030018--><!--Device-CertResult-ERR_CRL_SIGNATURE_FAILURE = 19030018-End-->

**System capability:** SystemCapability.Security.Cert

## ERR_CRYPTO_OPERATION

```TypeScript
ERR_CRYPTO_OPERATION = 19030001
```

An error occurs when the API of a third-party algorithm library is called.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-CertResult-ERR_CRYPTO_OPERATION = 19030001--><!--Device-CertResult-ERR_CRYPTO_OPERATION = 19030001-End-->

**System capability:** SystemCapability.Security.Cert

## ERR_KEYUSAGE_NO_CERTSIGN

```TypeScript
ERR_KEYUSAGE_NO_CERTSIGN = 19030006
```

The key cannot be used for signing a certificate.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-CertResult-ERR_KEYUSAGE_NO_CERTSIGN = 19030006--><!--Device-CertResult-ERR_KEYUSAGE_NO_CERTSIGN = 19030006-End-->

**System capability:** SystemCapability.Security.Cert

## ERR_KEYUSAGE_NO_DIGITAL_SIGNATURE

```TypeScript
ERR_KEYUSAGE_NO_DIGITAL_SIGNATURE = 19030007
```

The key cannot be used for digital signature.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-CertResult-ERR_KEYUSAGE_NO_DIGITAL_SIGNATURE = 19030007--><!--Device-CertResult-ERR_KEYUSAGE_NO_DIGITAL_SIGNATURE = 19030007-End-->

**System capability:** SystemCapability.Security.Cert

## ERR_MAYBE_WRONG_PASSWORD

```TypeScript
ERR_MAYBE_WRONG_PASSWORD = 19030008
```

The private key password may be incorrect.

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-CertResult-ERR_MAYBE_WRONG_PASSWORD = 19030008--><!--Device-CertResult-ERR_MAYBE_WRONG_PASSWORD = 19030008-End-->

**System capability:** SystemCapability.Security.Cert

## ERR_NETWORK_TIMEOUT

```TypeScript
ERR_NETWORK_TIMEOUT = 19030024
```

This error code is reported if the network connection times out.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-CertResult-ERR_NETWORK_TIMEOUT = 19030024--><!--Device-CertResult-ERR_NETWORK_TIMEOUT = 19030024-End-->

**System capability:** SystemCapability.Security.Cert

## ERR_OCSP_CERT_STATUS_UNKNOWN

```TypeScript
ERR_OCSP_CERT_STATUS_UNKNOWN = 19030023
```

This error code is reported if the OCSP certificate status is unknown.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-CertResult-ERR_OCSP_CERT_STATUS_UNKNOWN = 19030023--><!--Device-CertResult-ERR_OCSP_CERT_STATUS_UNKNOWN = 19030023-End-->

**System capability:** SystemCapability.Security.Cert

## ERR_OCSP_RESPONSE_INVALID

```TypeScript
ERR_OCSP_RESPONSE_INVALID = 19030021
```

This error code is reported if the OCSP response is invalid.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-CertResult-ERR_OCSP_RESPONSE_INVALID = 19030021--><!--Device-CertResult-ERR_OCSP_RESPONSE_INVALID = 19030021-End-->

**System capability:** SystemCapability.Security.Cert

## ERR_OCSP_RESPONSE_NOT_FOUND

```TypeScript
ERR_OCSP_RESPONSE_NOT_FOUND = 19030020
```

This error code is reported if the attempt to obtain the Online Certificate Status Protocol (OCSP) response fails.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-CertResult-ERR_OCSP_RESPONSE_NOT_FOUND = 19030020--><!--Device-CertResult-ERR_OCSP_RESPONSE_NOT_FOUND = 19030020-End-->

**System capability:** SystemCapability.Security.Cert

## ERR_OCSP_SIGNATURE_FAILURE

```TypeScript
ERR_OCSP_SIGNATURE_FAILURE = 19030022
```

This error code is reported if the OCSP signature verification fails.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-CertResult-ERR_OCSP_SIGNATURE_FAILURE = 19030022--><!--Device-CertResult-ERR_OCSP_SIGNATURE_FAILURE = 19030022-End-->

**System capability:** SystemCapability.Security.Cert

## ERR_OUT_OF_MEMORY

```TypeScript
ERR_OUT_OF_MEMORY = 19020001
```

Memory error.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-CertResult-ERR_OUT_OF_MEMORY = 19020001--><!--Device-CertResult-ERR_OUT_OF_MEMORY = 19020001-End-->

**System capability:** SystemCapability.Security.Cert

## ERR_PARAMETER_CHECK_FAILED

```TypeScript
ERR_PARAMETER_CHECK_FAILED = 19020003
```

Parameter check failed.

**Since:** 20

**Atomic service API:** This API can be used in atomic services since API version 20.

<!--Device-CertResult-ERR_PARAMETER_CHECK_FAILED = 19020003--><!--Device-CertResult-ERR_PARAMETER_CHECK_FAILED = 19020003-End-->

**System capability:** SystemCapability.Security.Cert

## ERR_RUNTIME_ERROR

```TypeScript
ERR_RUNTIME_ERROR = 19020002
```

This error code is reported if an error occurs during running.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-CertResult-ERR_RUNTIME_ERROR = 19020002--><!--Device-CertResult-ERR_RUNTIME_ERROR = 19020002-End-->

**System capability:** SystemCapability.Security.Cert

## ERR_UNABLE_TO_GET_ISSUER_CERT_LOCALLY

```TypeScript
ERR_UNABLE_TO_GET_ISSUER_CERT_LOCALLY = 19030005
```

Failed to obtain the certificate issuer.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-CertResult-ERR_UNABLE_TO_GET_ISSUER_CERT_LOCALLY = 19030005--><!--Device-CertResult-ERR_UNABLE_TO_GET_ISSUER_CERT_LOCALLY = 19030005-End-->

**System capability:** SystemCapability.Security.Cert

## ERR_UNKNOWN_CRITICAL_EXTENSION

```TypeScript
ERR_UNKNOWN_CRITICAL_EXTENSION = 19030011
```

This error code is reported if there is an unknown critical extension.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-CertResult-ERR_UNKNOWN_CRITICAL_EXTENSION = 19030011--><!--Device-CertResult-ERR_UNKNOWN_CRITICAL_EXTENSION = 19030011-End-->

**System capability:** SystemCapability.Security.Cert

## INVALID_PARAMS

```TypeScript
INVALID_PARAMS = 401
```

Invalid parameter.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-CertResult-INVALID_PARAMS = 401--><!--Device-CertResult-INVALID_PARAMS = 401-End-->

**System capability:** SystemCapability.Security.Cert

## NOT_SUPPORT

```TypeScript
NOT_SUPPORT = 801
```

Unsupported operation.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-CertResult-NOT_SUPPORT = 801--><!--Device-CertResult-NOT_SUPPORT = 801-End-->

**System capability:** SystemCapability.Security.Cert
