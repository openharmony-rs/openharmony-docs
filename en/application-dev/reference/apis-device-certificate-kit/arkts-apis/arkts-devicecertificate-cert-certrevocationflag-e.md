# CertRevocationFlag

```TypeScript
enum CertRevocationFlag
```

Enumerates the certificate revocation flags.

**Since:** 26.0.0

<!--Device-cert-enum CertRevocationFlag--><!--Device-cert-enum CertRevocationFlag-End-->

**System capability:** SystemCapability.Security.Cert

## CERT_REVOCATION_CHECK_ALL_CERT

```TypeScript
CERT_REVOCATION_CHECK_ALL_CERT = 3
```

Revocation status check of all certificates.

- If this flag is set, revocation check is performed on all certificates in the certificate chain  
(skips self-signed certificates);  
- If this flag is not set, only the end-entity certificate (the first certificate in the certificate chain) is  
checked.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-CertRevocationFlag-CERT_REVOCATION_CHECK_ALL_CERT = 3--><!--Device-CertRevocationFlag-CERT_REVOCATION_CHECK_ALL_CERT = 3-End-->

**System capability:** SystemCapability.Security.Cert

## CERT_REVOCATION_CRL_CHECK

```TypeScript
CERT_REVOCATION_CRL_CHECK = 1
```

CRL check. Verify the certificate status based on a CRL. Match a CRL using the **crls** parameter of [X509CertRevokedParams](arkts-devicecertificate-cert-x509certrevokedparams-i.md). If no matching CRL is found and **allowDownloadCrl** of [X509CertRevokedParams](arkts-devicecertificate-cert-x509certrevokedparams-i.md) is set to **true**, the CDP extension of the certificate is used to download the CRL.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-CertRevocationFlag-CERT_REVOCATION_CRL_CHECK = 1--><!--Device-CertRevocationFlag-CERT_REVOCATION_CRL_CHECK = 1-End-->

**System capability:** SystemCapability.Security.Cert

## CERT_REVOCATION_OCSP_CHECK

```TypeScript
CERT_REVOCATION_OCSP_CHECK = 2
```

OCSP check. Verify the certificate status based on the OCSP response.

<br>First, the **ocspResponses** parameter of [X509CertRevokedParams](arkts-devicecertificate-cert-x509certrevokedparams-i.md) is used. If no matching OCSP response is found and **allowOcspCheckOnline** of [X509CertRevokedParams](arkts-devicecertificate-cert-x509certrevokedparams-i.md) is set to **true**, the system attempts to obtain the OCSP URL from the certificate AIA extension and sends a request to obtain the response.

> **NOTE:** 
> 
> - Always use the current system time to verify the validity period of the OCSP response, and allow a time tolerance of ±5 minutes.
> - Always use the current system time to verify the validity period of the OCSP signing certificate chain.
> - Lack of **nonce** and **nextUpdate** is allowed.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-CertRevocationFlag-CERT_REVOCATION_OCSP_CHECK = 2--><!--Device-CertRevocationFlag-CERT_REVOCATION_OCSP_CHECK = 2-End-->

**System capability:** SystemCapability.Security.Cert

## CERT_REVOCATION_PREFER_OCSP

```TypeScript
CERT_REVOCATION_PREFER_OCSP = 0
```

OCSP check (preferred). This flag takes effect only when both **CERT_REVOCATION_CRL_CHECK** and **CERT_REVOCATION_OCSP_CHECK** are set.

- After this flag is set, the OCSP check is performed first, and the CRL check is performed if no OCSP response  
is found or a timeout occurs;  
- If this flag is not set, the CRL check is performed first, and the OCSP check is performed if no CRL is found  
or a timeout occurs.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-CertRevocationFlag-CERT_REVOCATION_PREFER_OCSP = 0--><!--Device-CertRevocationFlag-CERT_REVOCATION_PREFER_OCSP = 0-End-->

**System capability:** SystemCapability.Security.Cert
