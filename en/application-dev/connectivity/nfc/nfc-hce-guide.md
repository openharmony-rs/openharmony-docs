# HCE Development

<!--Kit: Connectivity Kit-->
<!--Subsystem: Communication-->
<!--Owner: @amunra03-->
<!--Designer: @wenxiaolin-->
<!--Tester: @zs_111-->
<!--Adviser: @zhang_yixin13-->
<!-- md-trans-meta sourceCommit=dcae6f10c07044342acb5b2dc0416e100c5bcaa2 translatedAt=2026-06-17T06:38:44.790Z pushedAt=2026-06-22T02:45:44.815Z -->

## Introduction

Near Field Communication (NFC) is a short-range, high-frequency radio technology that operates at a frequency of 13.56 MHz, with a typical communication range of within 10 centimeters. Host Card Emulation (HCE) provides card emulation that does not depend on a secure element. It allows an application to emulate a card and communicate with an NFC card reader to complete NFC card swiping. Off Host Card Emulation (OFFHOST) is supported since API version 22. It simulates a card using a separate chip (called as the secure element or SE) on the device. Some SIM cards of wireless carriers contain SEs.

## When to Use

An application emulates a card and communicates with an NFC card reader to complete NFC card swiping. The device can communicate with an NFC card reader by using a started application (foreground mode) or without starting an application (background mode).

- HCE foreground card swiping<br>

In the foreground mode, the user has to start a specific application that communicates with the NFC card reader. Specifically, the user starts the application, opens the application page, and taps the device on the NFC card reader. In this case, the transaction data is distributed only to the foreground application. When the application switches to the background or exits, the foreground priority is also suspended.

- HCE background card swiping<br>

The user taps the device on an NFC card reader without starting any HCE application. Then, the device selects an HCE application based on the Applet ID (AID, which complies with ISO/IEC 7816-4) provided by the NFC card reader, and completes the card swiping transaction. If multiple HCE applications are matched, an application selector will be displayed, listing all the available applications. In this case, the user needs to open the desired HCE application and tap the device on the NFC card reader again to trigger the card swiping transaction.

The SE emulates an NFC card and communicates with an NFC card reader to complete the NFC card swiping. The card to be emulated is configured in the SE through the application. When the device taps the NFC card reader, data is not processed by the device CPU, but is directly sent to the SE to complete the card swiping.

## Constraints

1. For security reasons, regardless of whether the HCE application performs card swiping in the foreground or background, the device does not support HCE card swiping operations when it is in the screen-off state.<br>

2. A device must be equipped with an NFC controller chip to support HCE card swiping capabilities. There are no constraints on whether it has an NFC secure element.<br>

3. An HCE application must declare the NFC card emulation permission. For specific details, see the sample code.<br>

## Available APIs

For the complete API description and sample code, see [@ohos.nfc.cardEmulation (Standard NFC Card Emulation)](../../reference/apis-connectivity-kit/js-apis-cardEmulation.md).

The following table describes the APIs for implementing HCE.

| API                            | Supported Version               | Description                                                                                                                             |
| ---------------------------------- | ------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------- |
| hasHceCapability(): boolean       | API version 9+                  | Checks whether the device supports HCE card emulation.                                                                                 |
| isDefaultService(elementName: ElementName, type: CardType): boolean | API version 9+ | Checks whether the specified application is the default application for the given service type.                                         |
| start(elementName: ElementName, aidList: string[]): void            | API version 9+                  | Starts the HCE service, including setting the current application as the foreground preferred application and dynamically registering the AID list. |
| stop(elementName: ElementName): void                                | API version 9+                  | Stops the HCE service, including unsubscribing from APDU data reception, exiting foreground preferred status, and releasing the dynamically registered AID list. |
| on(type: 'hceCmd', callback: AsyncCallback\<number[]>): void        | API version 8+                  | Subscribes to a callback for receiving APDU data sent from the peer card reader.                                                       |
| transmit(response: number[]): Promise\<void>                        | API version 9+                  | Transmits APDU data to the peer card reader.                                                                                           |
| off(type: 'hceCmd', callback?: AsyncCallback\<number[]>): void      | API version 18+                 | Unsubscribes from APDU data reception.                                                                                                 |

## Preparations

### Selecting Foreground or Background Card Swiping

HCE application developers can choose to implement either foreground or background card swiping based on service requirements. These two methods differ in their code implementation.

- HCE foreground card swiping<br>

1. In the **module.json5** configuration file, there is no need to statically declare the Applet ID (AID, which complies with ISO/IEC 7816-4) selected by the NFC card reader. Instead, dynamically register an AID by using [start](../../reference/apis-connectivity-kit/js-apis-cardEmulation.md#start9).

2. When the card swiping page of the HCE application exits, explicitly call [stop](../../reference/apis-connectivity-kit/js-apis-cardEmulation.md#stop9) to release the dynamically registered AID.

- HCE background card swiping<br>

1. In the **module.json5** configuration file, statically declare the AID selected by the NFC card reader. Based on service requirements, specify whether the declared AID belongs to the **Payment** type or the **Other** type.

2. If the **Payment** type is selected, the HCE application will appear in the NFC default payment application list on the system settings page. After the user selects this HCE application as the default payment application, conflict-free background card swiping can be implemented. Since a default payment application is designated, there will be no conflicts between multiple HCE applications of the **Payment** type.

3. If the **Other** type is selected, the HCE application will not appear in the NFC default payment app list on the system settings page. However, conflicts may arise if multiple HCE applications declare the same AID of the **Other** type.

4. When implementing HCE background card swiping, you do not need to call the **start** and **stop** APIs.

5. You are advised to use a dedicated **HceAbility** for HCE application background card swiping to reduce the time spent in [onCreate](../../reference/apis-ability-kit/js-apis-app-ability-uiAbility.md#oncreate).

6. In the **OnCreate** function of **HceAbility**, minimize operations other than [hceService.on](../../reference/apis-connectivity-kit/js-apis-cardEmulation.md#on8).

7. Call **hceService.on** synchronously in the **onCreate** function of **HceAbility**. Do not call it asynchronously, as this may affect the HCE communication timing.

> **NOTE**
>
> - Starting from API version 9, application development supports the [stage model](../../application-models/ability-terminology.md#stage-model), which is recommended for long-term evolution.
> - All the HCE sample code in this document is based on the [stage model](../../application-models/ability-terminology.md#stage-model).

## How to Develop

### HCE Foreground Card Swiping

1. Declare the permission required for NFC card emulation and HCE action in the **module.json5** file.

2. Import modules.

3. Check whether the device supports the NFC and HCE capabilities.

4. Enable the foreground HCE application to preferentially process NFC card swiping.

5. Subscribe to the HCE APDU receiving events.

6. Receive and send APDU data for HCE card swiping.

7. Exit the HCE foreground mode when the application exits the NFC card swiping page.

```ts
    "abilities": [
      {
        // The variable names used below must be declared and defined first if they have no default values.
        "name": "EntryAbility",
        "srcEntry": "./ets/entryability/EntryAbility.ts",
        "description": "$string:EntryAbility_desc",
        "icon": "$media:icon",
        "label": "$string:EntryAbility_label",
        "startWindowIcon": "$media:icon",
        "startWindowBackground": "$color:start_window_background",
        "exported": true,
        "skills": [
          {
            "entities": [
              "entity.system.home"
            ],
            "actions": [
              "ohos.want.action.home",

              // actions must include "ohos.nfc.cardemulation.action.HOST_APDU_SERVICE".
              "ohos.nfc.cardemulation.action.HOST_APDU_SERVICE"
            ]
          }
        ]
      }
    ],
    "requestPermissions": [
      {
        // Add the permission required for using NFC card emulation.
        "name": "ohos.permission.NFC_CARD_EMULATION",
        "reason": "$string:app_name",
      }
    ]
```

```ts
import { cardEmulation, nfcController } from '@kit.ConnectivityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { AsyncCallback } from '@kit.BasicServicesKit';
import { AbilityConstant, UIAbility, Want, bundleManager } from '@kit.AbilityKit';

let hceElementName: bundleManager.ElementName;
let hceService: cardEmulation.HceService;

const hceCommandCb: AsyncCallback<number[]> = (error: BusinessError, hceCommand: number[]) => {
  if (!error) {
    if (hceCommand == null) {
      hilog.error(0x0000, 'testTag', 'hceCommandCb has invalid hceCommand.');
      return;
    }
    // Implement your service logic to verify the received command and send the corresponding response.
    hilog.info(0x0000, 'testTag', 'hceCommand = %{public}s', JSON.stringify(hceCommand));
    let responseData = [0x90, 0x00]; // Update the response data based on the received command.
    hceService.transmit(responseData).then(() => {
      hilog.info(0x0000, 'testTag', 'hceService transmit Promise success.');
    }).catch((err: BusinessError) => {
      hilog.error(0x0000, 'testTag', 'hceService transmit Promise error = %{public}s', JSON.stringify(err));
    });
  } else {
    hilog.error(0x0000, 'testTag', 'hceCommandCb error %{public}s', JSON.stringify(error));
  }
}

export default class EntryAbility extends UIAbility {
  onCreate(want: Want, launchParam: AbilityConstant.LaunchParam) {
    hilog.info(0x0000, 'testTag', '%{public}s', 'Ability onCreate');

    // Check whether the device supports NFC and HCE capabilities.
    if (!canIUse("SystemCapability.Communication.NFC.Core")) {
      hilog.error(0x0000, 'testTag', 'NFC System Capability not supported.');
      return;
    }
    if (!nfcController.isNfcSupported()) {
      hilog.error(0x0000, 'testTag', 'NFC not supported on this device.');
      return;
    }
    if (!cardEmulation.hasHceCapability()) {
      hilog.error(0x0000, 'testTag', 'hce unavailable.');
      return;
    }

    // The elements in hceElementName cannot be empty. Obtain the application's elementname through want or fill in based on the actual application information.
    hceElementName = {
      bundleName: want.bundleName ?? '',
      abilityName: want.abilityName ?? '',
      moduleName: want.moduleName,
    }
    hceService = new cardEmulation.HceService();
  }

  onForeground() {
    // The application enters the foreground.
    hilog.info(0x0000, 'testTag', '%{public}s', 'Ability onForeground');
    if (hceElementName != undefined) {
      try {
        // Call the API to enable the foreground HCE application to prioritize NFC card swiping.
        let aidList = ["A0000000031010", "A0000000031011"]; // Modify to the correct AID.
        hceService.start(hceElementName, aidList);

        // Subscribe to the HCE APDU receiving events.
        hceService.on('hceCmd', hceCommandCb);
      } catch (error) {
        hilog.error(0x0000, 'testTag', 'hceService.start error = %{public}s', JSON.stringify(error));
      }
    }
  }

  onBackground() {
    // The application enters the background.
    hilog.info(0x0000, 'testTag', '%{public}s', 'Ability onBackground');
    // The application exits the foreground and stops HCE services.
    if (hceElementName != undefined) {
      try {
        hceService.stop(hceElementName);
      } catch (error) {
        hilog.error(0x0000, 'testTag', 'hceService.stop error = %{public}s', JSON.stringify(error));
      }
    }
  }
}
```

### HCE Background Card Swiping

1. Declare the permission required for NFC card emulation, HCE action, and AIDs for application matching in the **module.json5** file.

2. Import modules.

3. Check whether the device supports the NFC and HCE capabilities.

4. Subscribe to the HCE APDU receiving events.

5. Receive and send APDU data for HCE card swiping.

6. Cancel the subscription when the application exits.

```ts
    "abilities": [
      {
        "name": "HceUIAbility",
        "srcEntry": "./ets/hceuiability/HceUIAbility.ts",
        "description": "$string:EntryAbility_desc",
        "icon": "$media:icon",
        "label": "$string:EntryAbility_label",
        "startWindowIcon": "$media:icon",
        "startWindowBackground": "$color:start_window_background",
        "exported": true,
        "skills": [
          {
            "entities": [
              "entity.system.home"
            ],
            "actions": [
              "ohos.want.action.home",

              // actions must include "ohos.nfc.cardemulation.action.HOST_APDU_SERVICE".
              "ohos.nfc.cardemulation.action.HOST_APDU_SERVICE"
            ]
          }
        ],

        // Define at least one AID of the Payment type or Other type based on service requirements; multiple AIDs can be defined.
        "metadata": [
          {
            "name": "payment-aid",
            "value": "A0000000031010" // Define an AID of the Payment type.
          },
          {
            "name": "other-aid",
            "value": "A0000000031011" // Define an AID of the Other type.
          }
        ]
      }
    ],
    "requestPermissions": [
      {
        // Add the permission required for using NFC card emulation.
        "name": "ohos.permission.NFC_CARD_EMULATION",
        "reason": "$string:app_name",
      }
    ]
```

```ts
import { cardEmulation, nfcController } from '@kit.ConnectivityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { AsyncCallback } from '@kit.BasicServicesKit';
import { AbilityConstant, UIAbility, Want, bundleManager } from '@kit.AbilityKit';

let hceElementName: bundleManager.ElementName;
let hceService: cardEmulation.HceService;

const hceCommandCb: AsyncCallback<number[]> = (error: BusinessError, hceCommand: number[]) => {
  if (!error) {
    if (hceCommand == null) {
      hilog.error(0x0000, 'testTag', 'hceCommandCb has invalid hceCommand.');
      return;
    }

    // The application checks the content of the received command and sends the matching response data based on its own service implementation.
    hilog.info(0x0000, 'testTag', 'hceCommand = %{public}s', JSON.stringify(hceCommand));
    let responseData = [0x90, 0x00]; // Change the response data based on different received commands.
    hceService.transmit(responseData).then(() => {
      hilog.info(0x0000, 'testTag', 'hceService transmit Promise success.');
    }).catch((err: BusinessError) => {
      hilog.error(0x0000, 'testTag', 'hceService transmit Promise error = %{public}s', JSON.stringify(err));
    });
  } else {
    hilog.error(0x0000, 'testTag', 'hceCommandCb error %{public}s', JSON.stringify(error));
  }
}

// Use a dedicated HceAbility implementation to reduce the time consumed by the OnCreate function.
export default class HceUIAbility extends UIAbility {
  onCreate(want: Want, launchParam: AbilityConstant.LaunchParam) {
    // Minimize operations in the OnCreate function other than hceService.on.
    hilog.info(0x0000, 'testTag', '%{public}s', 'Ability onCreate');

    // Determine whether the device supports NFC and HCE capabilities.
    if (!canIUse("SystemCapability.Communication.NFC.Core")) {
      hilog.error(0x0000, 'testTag', 'NFC System Capability not supported.');
      return;
    }
    if (!nfcController.isNfcSupported()) {
      hilog.error(0x0000, 'testTag', 'NFC not supported on this device.');
      return;
    }
    if (!cardEmulation.hasHceCapability()) {
      hilog.error(0x0000, 'testTag', 'hce unavailable.');
      return;
    }
    // Subscribe to HCE card swiping events when the application is brought to the foreground.
    hceService = new cardEmulation.HceService();
    // hceService.on must be executed synchronously, not asynchronously, to avoid affecting the HCE communication timing
    hceService.on('hceCmd', hceCommandCb);
  }

  onForeground() {
    // Application enters the foreground.
    hilog.info(0x0000, 'testTag', '%{public}s', 'Ability onForeground');
  }

  onDestroy() {
    hilog.info(0x0000, 'testTag', '%{public}s', 'Ability onDestroy');
    // Exit the application and unsubscribe from HCE card swiping events.
    hceService.off('hceCmd', hceCommandCb);
  }
}
```

### OFFHOST Card Swiping

1. Declare the OFFHOST action, AIDs for application matching, and SEs in the **module.json5** file.

2. Set the OFFHOST application as the default payment application.

> **NOTE**
>
> - OFFHOST is supported since API version 22.
> - Only the AID of the **Payment** type is supported.
> - Only the SIM card can be used as the SE.

```ts
"abilities": [
      {
        "name": "EntryAbility",
        "srcEntry": "./ets/entryability/EntryAbility.ts",
        "description": "$string:EntryAbility_desc",
        "icon": "$media:icon",
        "label": "$string:EntryAbility_label",
        "startWindowIcon": "$media:icon",
        "startWindowBackground": "$color:start_window_background",
        "exported": true,
        "skills": [
          {
            "entities": [
              "entity.system.home"
            ],
            "actions": [
              "ohos.want.action.home",

              // actions must include "ohos.nfc.cardemulation.action.OFF_HOST_APDU_SERVICE".
              "ohos.nfc.cardemulation.action.OFF_HOST_APDU_SERVICE"
            ]
          }
        ],
        // Define at least one AID of the Payment type based on service requirements.
        "metadata": [
          {
            "name": "payment-aid",
            "value": "A0000000031010" // Define the AID of the Payment type. The AID must be correct.
          },
           {
             "name": "secureElement",
             "value": "SIM" // Define secureElement.
            },
        ]
      }
    ]
```