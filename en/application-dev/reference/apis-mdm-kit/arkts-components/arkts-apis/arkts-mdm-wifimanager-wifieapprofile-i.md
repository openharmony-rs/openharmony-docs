# WifiEapProfile

Represents EAP profile (configuration) information.

**Since:** 12

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## Modules to Import

```TypeScript
import { wifiManager } from '@kit.MDMKit';
```

## altSubjectMatch

```TypeScript
altSubjectMatch: string
```

A string to match the alternate subject. In addition to checking the primary domain name of the certificate, the system checks whether the alternate subject name of the certificate matches the certificate.

**Type:** string

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## anonymousIdentity

```TypeScript
anonymousIdentity: string
```

Anonymous identity.

**Type:** string

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## caCertAliases

```TypeScript
caCertAliases: string
```

CA certificate alias.

**Type:** string

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## caPath

```TypeScript
caPath: string
```

CA certificate path.

**Type:** string

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## certEntry

```TypeScript
certEntry: Uint8Array
```

Client certificate content. When **eapMethod** is set to **EAP_TLS**, if this field is empty, the client certificate alias cannot be empty.

**Type:** Uint8Array

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## certPassword

```TypeScript
certPassword: string
```

CA certificate password.

**Type:** string

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## clientCertAliases

```TypeScript
clientCertAliases: string
```

Client certificate alias. When the client certificate content is empty, the client certificate must be installed first via the certificate management API before passing in the alias.

**Type:** string

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## domainSuffixMatch

```TypeScript
domainSuffixMatch: string
```

A string to match the domain suffix.

**Type:** string

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## eapMethod

```TypeScript
eapMethod: EapMethod
```

EAP authentication method.

**Type:** [EapMethod](arkts-mdm-wifimanager-eapmethod-e.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## eapSubId

```TypeScript
eapSubId: number
```

Sub-ID of the SIM card.

**Type:** number

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## identity

```TypeScript
identity: string
```

Identity Information. This parameter cannot be empty when **eapMethod** is **TLS**.

**Type:** string

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## password

```TypeScript
password: string
```

Password Authentication (PWD). It enables password-based authentication and does not require a server certificate.

**Type:** string

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## phase2Method

```TypeScript
phase2Method: Phase2Method
```

Phase 2 authentication method. This parameter is mandatory only when **eapMethod** is **EAP_PEAP** or **EAP_TTLS**.

**Type:** [Phase2Method](arkts-mdm-wifimanager-phase2method-e.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## plmn

```TypeScript
plmn: string
```

Credential provider.

**Type:** string

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## realm

```TypeScript
realm: string
```

Realm for the passpoint credential.

**Type:** string

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager
