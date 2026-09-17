# PairingType

Enumerates the NearLink pairing types.

**Since:** 26.0.0

**System capability:** SystemCapability.Communication.NearLink.Base

## NO_PASSKEY_CONFIRMATION

```TypeScript
NO_PASSKEY_CONFIRMATION = 0
```

Pairing type that does not require a passkey. Users do not need to check the pairing code.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Communication.NearLink.Base

## PAIRING_TYPE_PASSCODE

```TypeScript
PAIRING_TYPE_PASSCODE = 1
```

Pairing type with passcode authentication. Users need to enter the pairing code displayed on one device into the other device.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Communication.NearLink.Base

## PAIRING_TYPE_NUMBER_COMPARE

```TypeScript
PAIRING_TYPE_NUMBER_COMPARE = 2
```

Pairing type with authentication based on digit comparison. Users must ensure that the pairing codes on both devices are the same.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Communication.NearLink.Base
