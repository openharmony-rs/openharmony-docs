# PairingType

```TypeScript
enum PairingType
```

星闪配对类型，为枚举值。

**起始版本：** 26.0.0

<!--Device-remoteDevice-enum PairingType--><!--Device-remoteDevice-enum PairingType-End-->

**系统能力：** SystemCapability.Communication.NearLink.Base

## NO_PASSKEY_CONFIRMATION

```TypeScript
NO_PASSKEY_CONFIRMATION = 0
```

表示不需要passkey的配对方式，用户无需检查配对码。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PairingType-NO_PASSKEY_CONFIRMATION = 0--><!--Device-PairingType-NO_PASSKEY_CONFIRMATION = 0-End-->

**系统能力：** SystemCapability.Communication.NearLink.Base

## PAIRING_TYPE_PASSCODE

```TypeScript
PAIRING_TYPE_PASSCODE = 1
```

表示通行码鉴权方式，用户需在一端设备输入另一端设备显示的配对码。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PairingType-PAIRING_TYPE_PASSCODE = 1--><!--Device-PairingType-PAIRING_TYPE_PASSCODE = 1-End-->

**系统能力：** SystemCapability.Communication.NearLink.Base

## PAIRING_TYPE_NUMBER_COMPARE

```TypeScript
PAIRING_TYPE_NUMBER_COMPARE = 2
```

表示数字比较鉴权方式，用户需在两端设备确认配对码一致。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PairingType-PAIRING_TYPE_NUMBER_COMPARE = 2--><!--Device-PairingType-PAIRING_TYPE_NUMBER_COMPARE = 2-End-->

**系统能力：** SystemCapability.Communication.NearLink.Base
