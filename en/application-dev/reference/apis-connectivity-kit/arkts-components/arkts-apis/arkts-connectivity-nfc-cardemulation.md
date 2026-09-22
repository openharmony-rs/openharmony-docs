# @ohos.nfc.cardEmulation(Standard NFC Card Emulation)

**Since:** 6

**Model restriction:** This API can be used in both the stage model and FA model.

**System capability:** SystemCapability.Communication.NFC.CardEmulation

## HCE and AID Declaration

Before developing an application related to HCE, you must declare NFC-related attributes in the **module.json5**file.

```json5
// Applicable to devices other than lite wearables
{
  "module": {
    // Other declared attributes
    "abilities": [
      {
        // Other declared attributes
        "skills": [
          {
            "actions": [
              "ohos.nfc.cardemulation.action.HOST_APDU_SERVICE"
            ]
          }
        ],
        "metadata": [
          {
            "name": "payment-aid",
            "value": "your payment aid"
          },
          {
            "name": "other-aid",
            "value": "your other aid"
          }
        ]
      }
    ],
    "requestPermissions": [
      {
        "name": "ohos.permission.NFC_CARD_EMULATION",
        // Set reason to card_emulation_reason.
        "reason": "$string:card_emulation_reason"
      }
    ]
  }
}
```

  
```json5
// Applicable to lite wearables
{
  "module": {
    // Other declared attributes
    "abilities": [
      {
        // Other declared attributes
        "metaData": {
          "customizeData": [
            {
              "name": "paymentAid",
              "value": "A0000000041012"
            },
            {
              "name": "otherAid",
              "value": "A0000000041010"
            }
          ]
        },
        "skills": [
          {
            "entities": [
              "ohos.nfc.cardemulation.action.HOST_APDU_SERVICE"
            ],
            "actions": [
              "ohos.nfc.cardemulation.action.HOST_APDU_SERVICE"
            ]
          }
        ]
      }
    ],
    "reqPermissions": [
      {
        "name": "ohos.permission.NFC_CARD_EMULATION",
        // Set reason to card_emulation_reason.
        "reason": "$string:card_emulation_reason",
        "usedScene": {
          "ability": [
            "FormAbility"
          ],
          "when": "always"
        }
      },
      {
        "name": "ohos.permission.NFC_TAG",
        // Set reason to card_emulation_reason.
        "reason": "$string:card_emulation_reason",
        "usedScene": {
          "ability": [
            "FormAbility"
          ],
          "when": "always"
        }
      }
    ]
  }
}
```



> **NOTE:** 
> 

> 1. The **actions** field must contain **ohos.nfc.cardemulation.action.HOST_APDU_SERVICE** and cannot be changed.
> 

> 2. When declaring an AID (in compliance with ISO/IEC 7816-4), ensure that **name** is set to **payment-aid** or

> **other-aid**. Incorrect setting will cause a parsing failure.
> 

> 3. The **name** field of **requestPermissions** must be **ohos.permission.NFC_CARD_EMULATION** and cannot be

> changed.
> 

> 4. Lite wearables support only the [FA Model](../../../application-models/ability-terminology.md#fa-model), with

> attribute configurations and API invocation methods differing from those of other device types. Refer to the

> example code for detailed implementations.

## Modules to Import

```TypeScript
import { cardEmulation } from '@kit.ConnectivityKit';
```

## Summary

### Functions

| Name | Description |
| --- | --- |
| [hasHceCapability](arkts-connectivity-cardemulation-hashcecapability-f.md) | Checks whether the device supports HCE. |
| [isDefaultService](arkts-connectivity-cardemulation-isdefaultservice-f.md) | Checks whether an application is the default application of the specified service type. |
| [isSupported](arkts-connectivity-cardemulation-issupported-f.md) | Checks whether a certain type of card emulation is supported. |

<!--Del-->
### Functions(System API)

| Name | Description |
| --- | --- |
| [getPaymentServices](arkts-connectivity-cardemulation-getpaymentservices-f-sys.md) | Obtains all payment services. If an application declares the support for the HCE feature and **payment-aid**, the application is contained in the payment service list. For details, see [HCE and AID Declaration](../../../reference/apis-connectivity-kit/js-apis-cardEmulation.md#hce-and-aid-declaration). |
<!--DelEnd-->

### Classes

| Name | Description |
| --- | --- |
| [HceService](arkts-connectivity-cardemulation-hceservice-c.md) | Provides APIs for implementing HCE, including receiving Application Protocol Data Units (APDUs) from the peer card reader and sending a response. Before using HCE-related APIs, check whether the device supports HCE. |

### Enums

| Name | Description |
| --- | --- |
| [CardType](arkts-connectivity-cardemulation-cardtype-e.md) | Enumerates the types of services used by the card emulation application. |
| [FeatureType](arkts-connectivity-cardemulation-featuretype-e.md) | Enumerates the NFC card emulation types. |
