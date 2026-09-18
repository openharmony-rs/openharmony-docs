# CertRevocationFlag

Enumerates the certificate revocation flags.

**Since:** 26.0.0

**System capability:** SystemCapability.Security.Cert

## CERT_REVOCATION_PREFER_OCSP

```TypeScript
CERT_REVOCATION_PREFER_OCSP = 0
```

OCSP check is preferred. This flag is valid only when CERT_REVOCATION_CRL_CHECK and CERT_REVOCATION_OCSP_CHECK are both set.

- If this flag is set, OCSP check is performed first, and CRL check is performed if no OCSP response is found or  
a timeout occurs;  
- If this flag is not set, CRL check is performed first, and OCSP check is performed if no CRL is found or a  
timeout occurs.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.Security.Cert

## CERT_REVOCATION_CRL_CHECK

```TypeScript
CERT_REVOCATION_CRL_CHECK = 1
```

Enables the CRL check. Checks the certificate status using a certificate revocation list.

<br>First, the **crls** parameter of [X509CertRevokedParams](arkts-devicecertificate-cert-x509certrevokedparams-i.md) is used. If no matching CRL is found and **allowDownloadCrl** of [X509CertRevokedParams](arkts-devicecertificate-cert-x509certrevokedparams-i.md) is set to **true**, the CDP extension of the certificate is used to download the CRL.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.Security.Cert

## CERT_REVOCATION_OCSP_CHECK

```TypeScript
CERT_REVOCATION_OCSP_CHECK = 2
```

Enables OCSP check. Checks the certificate status using the Online Certificate Status Protocol.

<br>First, the **ocspResponses** parameter of [X509CertRevokedParams](arkts-devicecertificate-cert-x509certrevokedparams-i.md) is used. If no matching OCSP response is found and **allowOcspCheckOnline** of [X509CertRevokedParams](arkts-devicecertificate-cert-x509certrevokedparams-i.md) is set to **true**, the system attempts to obtain the OCSP URL from the certificate AIA extension and sends a request to obtain the response.

> **NOTE:** 
> 
> - Always verify the validity period of the OCSP response against the current system time, and allow a time tolerance of ±5 minutes.
> - The validity period of the OCSP signature certificate chain is always verified using the current system time.
> - Allows ocsp response to be missing nonce and nextUpdate.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.Security.Cert

## CERT_REVOCATION_CHECK_ALL_CERT

```TypeScript
CERT_REVOCATION_CHECK_ALL_CERT = 3
```

Checks the revocation status of all certificates.

- If this flag is set, revocation check is performed on all certificates in the certificate chain  
(skips self-signed certificates);  
- If this flag is not set, only the end-entity certificate (the first certificate in the certificate chain) is  
checked.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.Security.Cert
