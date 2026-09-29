# WifiEapConfig

```TypeScript
interface WifiEapConfig
```

Wi-Fi EAP config. @typedef WifiEapConfig

**Since:** 10

<!--Device-wifiManager-interface WifiEapConfig--><!--Device-wifiManager-interface WifiEapConfig-End-->

**System capability:** SystemCapability.Communication.WiFi.STA

## Modules to Import

```TypeScript
import { wifiManager } from '@kit.ConnectivityKit';
```

## altSubjectMatch

```TypeScript
altSubjectMatch: string
```

Alternate subject match

**Type:** string

**Since:** 10

<!--Device-WifiEapConfig-altSubjectMatch: string--><!--Device-WifiEapConfig-altSubjectMatch: string-End-->

**System capability:** SystemCapability.Communication.WiFi.STA

## anonymousIdentity

```TypeScript
anonymousIdentity: string
```

Anonymous identity

**Type:** string

**Since:** 10

<!--Device-WifiEapConfig-anonymousIdentity: string--><!--Device-WifiEapConfig-anonymousIdentity: string-End-->

**System capability:** SystemCapability.Communication.WiFi.STA

## caCertAlias

```TypeScript
caCertAlias: string
```

CA certificate alias

**Type:** string

**Since:** 10

<!--Device-WifiEapConfig-caCertAlias: string--><!--Device-WifiEapConfig-caCertAlias: string-End-->

**System capability:** SystemCapability.Communication.WiFi.STA

## caPath

```TypeScript
caPath: string
```

CA certificate path

**Type:** string

**Since:** 10

<!--Device-WifiEapConfig-caPath: string--><!--Device-WifiEapConfig-caPath: string-End-->

**System capability:** SystemCapability.Communication.WiFi.STA

## certEntry

```TypeScript
certEntry: Uint8Array
```

content of user's certificate

**Type:** Uint8Array

**Since:** 10

<!--Device-WifiEapConfig-certEntry: Uint8Array--><!--Device-WifiEapConfig-certEntry: Uint8Array-End-->

**System capability:** SystemCapability.Communication.WiFi.STA

## certPassword

```TypeScript
certPassword: string
```

Password of user's certificate

**Type:** string

**Since:** 10

<!--Device-WifiEapConfig-certPassword: string--><!--Device-WifiEapConfig-certPassword: string-End-->

**System capability:** SystemCapability.Communication.WiFi.STA

## clientCertAlias

```TypeScript
clientCertAlias: string
```

Client certificate alias

**Type:** string

**Since:** 10

<!--Device-WifiEapConfig-clientCertAlias: string--><!--Device-WifiEapConfig-clientCertAlias: string-End-->

**System capability:** SystemCapability.Communication.WiFi.STA

## domainSuffixMatch

```TypeScript
domainSuffixMatch: string
```

Domain suffix match

**Type:** string

**Since:** 10

<!--Device-WifiEapConfig-domainSuffixMatch: string--><!--Device-WifiEapConfig-domainSuffixMatch: string-End-->

**System capability:** SystemCapability.Communication.WiFi.STA

## eapMethod

```TypeScript
eapMethod: EapMethod
```

EAP authentication method

**Type:** [EapMethod](arkts-connectivity-wifimanager-eapmethod-e.md)

**Since:** 10

<!--Device-WifiEapConfig-eapMethod: EapMethod--><!--Device-WifiEapConfig-eapMethod: EapMethod-End-->

**System capability:** SystemCapability.Communication.WiFi.STA

## eapSubId

```TypeScript
eapSubId: number
```

Sub ID of the SIM card

**Type:** number

**Since:** 10

<!--Device-WifiEapConfig-eapSubId: int--><!--Device-WifiEapConfig-eapSubId: int-End-->

**System capability:** SystemCapability.Communication.WiFi.STA

## identity

```TypeScript
identity: string
```

The identity

**Type:** string

**Since:** 10

<!--Device-WifiEapConfig-identity: string--><!--Device-WifiEapConfig-identity: string-End-->

**System capability:** SystemCapability.Communication.WiFi.STA

## password

```TypeScript
password: string
```

Password

**Type:** string

**Since:** 10

<!--Device-WifiEapConfig-password: string--><!--Device-WifiEapConfig-password: string-End-->

**System capability:** SystemCapability.Communication.WiFi.STA

## phase2Method

```TypeScript
phase2Method: Phase2Method
```

Phase 2 authentication method

**Type:** [Phase2Method](arkts-connectivity-wifimanager-phase2method-e.md)

**Since:** 10

<!--Device-WifiEapConfig-phase2Method: Phase2Method--><!--Device-WifiEapConfig-phase2Method: Phase2Method-End-->

**System capability:** SystemCapability.Communication.WiFi.STA

## plmn

```TypeScript
plmn: string
```

Public Land Mobile Network of the provider of Passpoint credential

**Type:** string

**Since:** 10

<!--Device-WifiEapConfig-plmn: string--><!--Device-WifiEapConfig-plmn: string-End-->

**System capability:** SystemCapability.Communication.WiFi.STA

## realm

```TypeScript
realm: string
```

Realm for Passpoint credential

**Type:** string

**Since:** 10

<!--Device-WifiEapConfig-realm: string--><!--Device-WifiEapConfig-realm: string-End-->

**System capability:** SystemCapability.Communication.WiFi.STA
