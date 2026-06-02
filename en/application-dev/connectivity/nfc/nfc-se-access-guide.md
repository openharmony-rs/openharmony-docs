# SE Access Development

<!--Kit: Connectivity Kit-->
<!--Subsystem: Communication-->
<!--Owner: @amunra03-->
<!--Designer: @wenxiaolin-->
<!--Tester: @zs_111-->
<!--Adviser: @zhang_yixin13-->
<!-- md-trans-meta sourceCommit=aaafc9fd6ce220a97d41d65de36c3b10ebecc876 translatedAt=2026-06-01T12:50:11.986Z pushedAt=2026-06-02T07:46:18.699Z -->

## Introduction

An electronic device may have one or more secure elements (SEs), such as the embedded SE (eSE) and SIM card. Access control for SEs is implemented in accordance with the Global Platform Access Control (GPAC) specification.

## When to Use

An application can access an SE through APIs, for example, writing data to an SE to emulate an NFC card on an electronic device. The card data may be stored in an eSE or a SIM card SE. Generally, access control rules (GPAC specifications) are preset on the SE. The application must have the corresponding permissions, as described in [secure element APIs](../../reference/apis-connectivity-kit/js-apis-secureElement.md). In other words, the application can access the SE only after passing the access control permission verification of the element.

## Available APIs

For details about the APIs and sample code, see [SE Management](../../reference/apis-connectivity-kit/js-apis-secureElement.md).

The following APIs are required for accessing an SE.

| Name                             | Supported Since    | Function Description                                                                       |
| ---------------------------------- | ----- | ------------------------------------------------------------------------- |
| createService(): Promise\<SEService>      |   API version 12   | Creates a connection that can be used to connect to all available SEs in the system.             |
| getReaders(): Reader[]           | API version 10   | Returns an array of available SE readers, including all supported SEs on the device.                  |
| openSession(): Session         | API version 10  | Creates a connection session on an SE reader instance and returns a session instance.                                  |
| openLogicalChannel(aid: number[]): Promise\<Channel>       |  API version 10  | Opens a logical channel and returns a logical channel instance object.              |
| transmit(command: number[]): Promise\<number[]>   | API version 10   | Sends APDU data to the SE.                                   |
| close(): void    |   API version 10  | Closes the channel.                                                            |

## How to Develop

### Accessing an SE

1. Import related modules.

2. Check whether the device supports SEs.

3. Access an SE and read or write data.

4. Release channel resources.

> **NOTE**
>
> - Starting from API version 9, application development supports the [stage model](../../application-models/ability-terminology.md#stage-model), which is the recommended and long-term evolution model.
> - Due to the high security level of the SE, you must set the build mode to release for packaging; otherwise, the application will not run properly.

```ts
import { omapi } from '@kit.ConnectivityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { AbilityConstant, UIAbility, Want } from '@kit.AbilityKit';

let seService: omapi.SEService;
let seReaders: omapi.Reader[];
let seSession: omapi.Session;
let seChannel: omapi.Channel;
let testSelectedAid: number[] = [0xA0, 0x00, 0x00, 0x00, 0x03, 0x10, 0x10];
let p2: number = 0x00;

export default class EntryAbility extends UIAbility {
  onCreate(want: Want, launchParam: AbilityConstant.LaunchParam) {
    hilog.info(0x0000, 'testTag', '%{public}s', 'Ability onCreate');

    // Check whether the device supports SEs.
    if (!canIUse("SystemCapability.Communication.SecureElement")) {
      hilog.error(0x0000, 'testTag', 'secure element unavailable.');
      return;
    }
    hilog.info(0x0000, 'testTag', 'secure element available.');
    this.omaTest();
  }

  private async omaTest() {
    // Create an SEService instance for SE access.
    await omapi.createService().then((data) => {
      if (data == undefined || !data.isConnected()) {
        hilog.error(0x0000, 'testTag', 'secure element service disconnected.');
        return;
      }
      seService = data;
      hilog.info(0x0000, 'testTag', 'secure element service connected.');
    }).catch((error: BusinessError) => {
      hilog.error(0x0000, 'testTag', 'createService error %{public}s', JSON.stringify(error));
      return;
    });

    // Obtain all supported readers on the device, that is, the list of all SEs.
    try {
      seReaders = seService.getReaders();
    } catch (error) {
      hilog.error(0x0000, 'testTag', 'getReaders error %{public}s', JSON.stringify(error));
    }
    if (seReaders == undefined || seReaders.length == 0) {
      hilog.error(0x0000, 'testTag', 'no valid reader found.');
      seService.shutdown();
      return;
    }

    // Select an SE (such as the eSE, SIM card, or SIM2 card) for access based on the service requirements. The SIM2 card is supported since API version 22.
    let reader: (omapi.Reader | undefined);
    for (let i = 0; i < seReaders.length; ++i) {
      let r = seReaders[i];
      // Distinguish the SE by name, for example, eSE, SIM, or SIM2.
      if (r.getName() === 'SIM') {
        reader = r;
        break;
      }
    }
    if (reader == undefined) {
      hilog.error(0x0000, 'testTag', 'no valid sim reader.');
      seService.shutdown();
      return;
    }
    hilog.info(0x0000, 'testTag', 'reader is %{public}s', reader?.getName());

    // Open a session on a specified SE instance.
    try {
      seSession = reader?.openSession() as omapi.Session;
    } catch (error) {
      hilog.error(0x0000, 'testTag', 'openSession error %{public}s', JSON.stringify(error));
    }
    if (seSession == undefined) {
      hilog.error(0x0000, 'testTag', 'seSession invalid.');
      seService.shutdown();
      return;
    }

    // Create a logical channel or basic channel via the session instance. Generally, the logical channel is used for access, as the basic channel may be restricted.
    try {
      // Change the value of testSelectedAid to the AID of the application that opens the logical channel.
      seChannel = await seSession.openLogicalChannel(testSelectedAid, p2);
    } catch (exception) {
      hilog.error(0x0000, 'testTag', 'openLogicalChannel exception %{public}s', JSON.stringify(exception));
    }

    if (seChannel == undefined) {
      hilog.error(0x0000, 'testTag', 'seChannel invalid.');
      seService.shutdown();
      return;
    }

    // Send APDUs to the SE over the logical channel. Set testApduData correctly based on actual service requirements, and ensue that the APDU format complies with the APDU specification.
    let testApduData = [0x01, 0x02, 0x03, 0x04];
    try {
      let response: number[] = await seChannel.transmit(testApduData);
      hilog.info(0x0000, 'testTag', 'seChannel.transmit() response = %{public}s.', JSON.stringify(response));
    } catch (exception) {
      hilog.error(0x0000, 'testTag', 'seChannel.transmit() exception = %{public}s.', JSON.stringify(exception));
    }

    // Close the channel to release resources when the SE access is complete.
    try {
      seChannel.close();
    } catch (exception) {
      hilog.error(0x0000, 'testTag', 'seChannel.close() exception = %{public}s.', JSON.stringify(exception));
    }

    // Close the service, and disable the binding relationship between the application and the SE service.
    seService.shutdown();
  }
}

```