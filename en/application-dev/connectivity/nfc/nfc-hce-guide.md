# HCE Development

<!--Kit: Connectivity Kit-->
<!--Subsystem: Communication-->
<!--Owner: @amunra03-->
<!--Designer: @wenxiaolin-->
<!--Tester: @zs_111-->

## Introduction
Near Field Communication (NFC) is a short-range, high-frequency radio technology that operates at a frequency of 13.56 MHz, with a typical communication range of within 10 centimeters. Host Card Emulation (HCE) provides card emulation that does not depend on a secure element. It allows an application to emulate a card and communicate with an NFC card reader through the NFC service.

## When to Use
An application emulates a card and communicates with an NFC card reader through the NFC service. The device can communicate with an NFC card reader by using a started application (foreground mode) or without starting an application (background mode).
- HCE foreground card swiping<br>
The user starts a specific application to communicate with the NFC card reader. Specifically, the user starts the application, opens the application page, and taps the device on the NFC card reader. In this case, the transaction data is distributed only to the foreground application.
- HCE background card swiping<br>
The user taps the device on an NFC card reader without starting any HCE application. Then, the device selects an HCE application based on the Applet ID (AID, which complies with ISO/IEC 7816-4) provided by the NFC card reader, and completes the card swiping transaction. If multiple HCE applications are matched, an application selector will be displayed, listing all the available applications. In this case, the user needs to open the desired HCE application and tap the device on the NFC card reader again to trigger the card swiping transaction.

## Constraints
1. For security reasons, regardless of whether the HCE application performs card swiping in the foreground or background, the device does not support HCE card swiping operations when it is in the screen-off state.<br>
2. A device must be equipped with an NFC controller chip to support HCE card swiping capabilities. There are no constraints on whether it has an NFC secure element.<br>
3. An HCE application must declare the NFC card emulation permission. For specific details, see the sample code.<br>

## Available APIs

For details about the JS APIs and sample code, [NFC Card Emulation](../../reference/apis-connectivity-kit/js-apis-cardEmulation.md).

The following table describes the APIs for implementing HCE.

| API                            | Description                                                                      |
| ---------------------------------- | ------------------------------------------------------------------------------ |
| start(elementName: ElementName, aidList: string[]): void                   | Starts HCE, including enabling this application to run in the foreground preferentially and dynamically registering the AID list.                                                              |
| stop(elementName: ElementName): void  | Stops HCE, including canceling the subscription of APDU data, exiting this application from the foreground, and releasing the dynamically registered AID list.
| on(type: 'hceCmd', callback: AsyncCallback\<number[]>): void                | Registers a callback to receive APDUs from the peer card reader.
| transmit(response: number[]): Promise\<void>                  | Transmits APDU data to the peer card reader.|                                                     |

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

              // Make sure that ohos.nfc.cardemulation.action.HOST_APDU_SERVICE is present in actions.
              "ohos.nfc.cardemulation.action.HOST_APDU_SERVICE"
            ]
          }
        ]
      }
    ],
    "requestPermissions": [
      {
        // Add the permission required for NFC card emulation.
        "name": "ohos.permission.NFC_CARD_EMULATION",
        "reason": "$string:app_name",
      }
    ]
```

```ts
import { cardEmulation } from '@kit.ConnectivityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { AsyncCallback } from '@kit.BasicServicesKit';
import { AbilityConstant, UIAbility, Want, bundleManager } from '@kit.AbilityKit';

let hceElementName: bundleManager.ElementName;
let hceService: cardEmulation.HceService;

const hceCommandCb : AsyncCallback<number[]> = (error : BusinessError, hceCommand : number[]) => {
  if (!error) {
    if (hceCommand == null) {
      hilog.error(0x0000, 'testTag', 'hceCommandCb has invalid hceCommand.');
      return;
    }
    // Check the command and send a response.
    hilog.info(0x0000, 'testTag', 'hceCommand = %{public}s', JSON.stringify(hceCommand));
    let responseData = [0x90, 0x00]; // Modify the response based on the received command.
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

    // Check whether the device supports the NFC and HCE capabilities.
    if (!canIUse("SystemCapability.Communication.NFC.Core")) {
      hilog.error(0x0000, 'testTag', 'nfc unavailable.');
      return;
    }
    if (!cardEmulation.hasHceCapability()) {
      hilog.error(0x0000, 'testTag', 'hce unavailable.');
      return;
    }

    // hceElementName cannot be empty. You can obtain elementName of the application through Want or fill in elementName based on the application information.
    hceElementName = {
      bundleName: want.bundleName ?? '',
      abilityName: want.abilityName ?? '',
      moduleName: want.moduleName,
    }
    hceService = new cardEmulation.HceService();
  }

  onForeground() {
    // Switch the application to the foreground.
    hilog.info(0x0000, 'testTag', '%{public}s', 'Ability onForeground');
    if (hceElementName != undefined) {
      try {
        // Enable the foreground HCE application to preferentially process NFC card swiping.
        let aidList = ["A0000000031010," "A0000000031011"]; // Set the AID list correctly.
        hceService.start(hceElementName, aidList);

        // Subscribe to the HCE APDU receiving events.
        hceService.on('hceCmd', hceCommandCb);
      } catch (error) {
        hilog.error(0x0000, 'testTag', 'hceService.start error = %{public}s', JSON.stringify(error));
      }
    }
  }

  onBackground() {
    // Switch the application to the background.
    hilog.info(0x0000, 'testTag', '%{public}s', 'Ability onBackground');
    // When exiting the NFC tag page of the application, call the tag module API to exit the foreground mode.
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

              // Make sure that ohos.nfc.cardemulation.action.HOST_APDU_SERVICE is present in actions.
              "ohos.nfc.cardemulation.action.HOST_APDU_SERVICE"
            ]
          }
        ],
        "metadata": [
          {
            "name": "payment-aid",
            "value": "A0000000031010" // Set a correct AID.
          },
          {
            "name": "other-aid",
            "value": "A0000000031011" // Set a correct AID.
          }
        ]
      }
    ],
    "requestPermissions": [
      {
        // Add the permission required for NFC card emulation.
        "name": "ohos.permission.NFC_CARD_EMULATION",
        "reason": "$string:app_name",
      }
    ]
```

```ts
import { cardEmulation } from '@kit.ConnectivityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { AsyncCallback } from '@kit.BasicServicesKit';
import { AbilityConstant, UIAbility, Want, bundleManager } from '@kit.AbilityKit';

let hceElementName : bundleManager.ElementName;
let hceService: cardEmulation.HceService;

const hceCommandCb : AsyncCallback<number[]> = (error : BusinessError, hceCommand : number[]) => {
  if (!error) {
    if (hceCommand == null || hceCommand == undefined) {
      hilog.error(0x0000, 'testTag', 'hceCommandCb has invalid hceCommand.');
      return;
    }

    // Check the command and send a response.
    hilog.info(0x0000, 'testTag', 'hceCommand = %{public}s', JSON.stringify(hceCommand));
    let responseData = [0x90, 0x00]; // change the response depend on different received command.
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

    // Check whether the device supports the NFC and HCE capabilities.
    if (!canIUse("SystemCapability.Communication.NFC.Core")) {
      hilog.error(0x0000, 'testTag', 'nfc unavailable.');
      return;
    }
    if (!cardEmulation.hasHceCapability()) {
      hilog.error(0x0000, 'testTag', 'hce unavailable.');
      return;
    }

    hceElementName = {
      bundleName: want.bundleName ?? '',
      abilityName: want.abilityName ?? '',
      moduleName: want.moduleName,
    }
    hceService = new cardEmulation.HceService();
    hceService.on('hceCmd', hceCommandCb);
  }

  onForeground() {
    // Switch the application to the foreground.
    hilog.info(0x0000, 'testTag', '%{public}s', 'Ability onForeground');
  }

  onDestroy() {
    // Exit the application.
    hilog.info(0x0000, 'testTag', '%{public}s', 'Ability onDestroy');
    // When exiting the NFC tag page of the application, call the tag module API to exit the foreground mode.
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
