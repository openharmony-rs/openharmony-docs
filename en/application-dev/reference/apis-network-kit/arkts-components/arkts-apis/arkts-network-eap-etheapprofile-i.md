# EthEapProfile

Represents the EAP profile information.

**Since:** 20

**System capability:** SystemCapability.Communication.NetManager.Eap

## Modules to Import

```TypeScript
import { eap } from '@kit.NetworkKit';
```

## altSubjectMatch

```TypeScript
altSubjectMatch: string
```

A string to match the alternate subject.

**Type:** string

**Since:** 20

**System capability:** SystemCapability.Communication.NetManager.Eap

## anonymousIdentity

```TypeScript
anonymousIdentity: string
```

Anonymous identity.

**Type:** string

**Since:** 20

**System capability:** SystemCapability.Communication.NetManager.Eap

## caCertAliases

```TypeScript
caCertAliases: string
```

CA certificate alias.

**Type:** string

**Since:** 20

**System capability:** SystemCapability.Communication.NetManager.Eap

## caPath

```TypeScript
caPath: string
```

CA certificate path.

**Type:** string

**Since:** 20

**System capability:** SystemCapability.Communication.NetManager.Eap

## certEntry

```TypeScript
certEntry: Uint8Array
```

CA certificate content.

**Type:** Uint8Array

**Since:** 20

**System capability:** SystemCapability.Communication.NetManager.Eap

## certPassword

```TypeScript
certPassword: string
```

CA certificate password.

**Type:** string

**Since:** 20

**System capability:** SystemCapability.Communication.NetManager.Eap

## clientCertAliases

```TypeScript
clientCertAliases: string
```

Client certificate alias.

**Type:** string

**Since:** 20

**System capability:** SystemCapability.Communication.NetManager.Eap

## domainSuffixMatch

```TypeScript
domainSuffixMatch: string
```

A string to match the domain suffix.

**Type:** string

**Since:** 20

**System capability:** SystemCapability.Communication.NetManager.Eap

## eapMethod

```TypeScript
eapMethod: EapMethod
```

EAP authentication method.

**Type:** [EapMethod](arkts-network-eap-eapmethod-e.md)

**Since:** 20

**System capability:** SystemCapability.Communication.NetManager.Eap

## eapSubId

```TypeScript
eapSubId: number
```

Sub-ID of the SIM card.

**Type:** number

**Since:** 20

**System capability:** SystemCapability.Communication.NetManager.Eap

## identity

```TypeScript
identity: string
```

Identity information.

**Type:** string

**Since:** 20

**System capability:** SystemCapability.Communication.NetManager.Eap

## password

```TypeScript
password: string
```

Password.

**Type:** string

**Since:** 20

**System capability:** SystemCapability.Communication.NetManager.Eap

## phase2Method

```TypeScript
phase2Method: Phase2Method
```

Phase 2 authentication method.

**Type:** [Phase2Method](arkts-network-eap-phase2method-e.md)

**Since:** 20

**System capability:** SystemCapability.Communication.NetManager.Eap

## plmn

```TypeScript
plmn: string
```

Public land mobile network (PLMN) of the passpoint credential provider.

**Type:** string

**Since:** 20

**System capability:** SystemCapability.Communication.NetManager.Eap

## realm

```TypeScript
realm: string
```

Realm for the passpoint credential.

**Type:** string

**Since:** 20

**System capability:** SystemCapability.Communication.NetManager.Eap
