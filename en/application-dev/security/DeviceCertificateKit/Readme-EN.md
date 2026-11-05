# Device Certificate Kit (Device Certificate Kit)

<!--Kit: Device Certificate Kit-->
<!--Subsystem: Security-->
<!--Owner: @zxz--3; @chaceli-->
<!--Designer: @lanming; @chande-->
<!--Tester: @PAFT; @zhangzhi1995-->
<!--Adviser: @zengyawen-->
<!-- md-trans-meta sourceCommit=c8093d1c731a16c88278ff4829f8fe5986157773 translatedAt=2026-11-03T05:14:16.480Z pushedAt=2026-11-03T06:52:43.640Z nl=1 -->

- [About This Kit](device-certificate-kit-intro.md)
- Certificate Framework<!--certificate-framework-->
  - [Certificate Framework Overview](certificate-framework-overview.md)
  - [Certificate Development](create-parse-verify-cert-object.md)
  - [Certificate Extension Development](create-parse-verify-certextension-object.md)
  - [CRL Development](create-parse-verify-crl-object.md)
  - [Creating a TrustAnchor Object Array from a PKCS #12 File](create-trustanchor-from-p12.md)
  - [Certificate Chain Validator Development](create-verify-cerchainvalidator-object.md)
  - [Certificate and CRL Collection Development](create-get-cert-crl-object.md)
  - [Certificate Chain Development](create-verify-certchain-object.md)
  - [Using the Prebuilt CA Certificate to Validate a Certificate Chain](verify-certchain-by-systemca.md)
  - [Certificate Signing with CMS](create-cms-sign-object.md)
  - [Certificate Encapsulation with CMS](create-cms-enveloped-object.md)
  - [Certificate Signature Verification with CMS](create-cms-verify-object.md)
  - [Certificate Decapsulation with CMS](create-cms-decapsulation-object.md)
  - [Creating and Parsing a Certificate with PKCS #12](create-parse-pkcs12.md)
  - [Online Validation of Certificate Revocation Status of a Certificate Chain](create-verify-cerchainvalidator-revocation-object.md)
  - [Downloading the Missing Intermediate CA Certificate During Certificate Chain Validation](allow-download-Intermediate-Cert.md)
  - [Building and Verifying a Certificate Chain](build-and-verify-cert-chain.md)
- Certificate Management Service<!--certmanager-->
  - [Certificate Manager Overview](certManager-overview.md)
  - [CA Certificate Development](certManager-ca-certs-guidelines.md)
  - [Application Certificate Development](certManager-private-credential-guidelines.md)
  - [User Certificate Credential Development](certManager-user-credential-guidelines.md)
  - [System Certificate Credential Development](certManager-system-credential-guidelines.md)
  - [Certificate Management Command-Line Tool Usage Guide](certmgr-cmdline-tool.md)
- [Glossary](device-certificate-glossary.md)