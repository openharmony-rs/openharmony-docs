# @ohos.InputMethodExtensionAbility (InputMethodExtensionAbility)

<!--Kit: IME Kit-->
<!--Subsystem: MiscServices-->
<!--Owner: @codexu62-->
<!--Designer: @andeszhang-->
<!--Tester: @murphy84-->
<!--Adviser: @zhang_yixin13-->
<!-- md-trans-meta sourceCommit=95b635b2657acaf53c78b86c96c7e9bdaf7f7668 translatedAt=2026-08-25T01:25:05.436Z pushedAt=2026-08-26T09:18:21.393Z -->

The **@ohos.InputMethodExtensionAbility** module provides the base class definition for the input method ExtensionAbility. It serves as the entry point and lifecycle management framework for developing input method apps.

As the core class module for input method ExtensionAbility, this module defines the **InputMethodExtensionAbility** class which acts as the base extension class for input method apps. You need to inherit this class and implement the **onCreate** and **onDestroy** lifecycle callbacks. The system invokes these callbacks automatically when starting or destroying the input method extension.

This module provides two core capabilities: (1) initialization of the input method app via the **onCreate(want)** callback. This callback is invoked when the system launches the input method extension, where you complete initialization tasks such as resource loading and panel creation. (2) resource cleanup for the input method app via the **onDestroy()** callback. This callback is invoked when the system destroys the input method extension, where you release resources. In addition, the **context** property provides an **InputMethodExtensionContext** object, allowing you to perform context-level operations such as destroying the extension and launching other apps during the lifecycle.

This module is mandatory for input method app development. The workflow is as follows: inherit **InputMethodExtensionAbility** → configure ExtensionAbility information in **module.json5** → **onCreate** (initialization) is triggered upon system startup → **onDestroy** (cleanup) is triggered by system destruction or a proactive developer call to **context.destroy()**.

> **NOTE**
>
> The initial APIs of this module are supported since API version 9. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
> **InputMethodExtensionAbility** defines only the basic lifecycle callbacks **onCreate** and **onDestroy**. The core interaction capabilities of the input method (such as panel creation/destruction, keyboard event listening, and client attachment) are obtained from the **InputMethodAbility** object provided by the **@ohos.inputMethodEngine** module inside the **onCreate** callback. **onCreate** is the sole entry for acquiring all key objects and creating panels, and initialization must be completed within this callback.
>
> The type of the **context** property of **InputMethodExtensionAbility** is **InputMethodExtensionContext** (from the **@ohos.InputMethodExtensionContext** module). This represents an association relationship: **InputMethodExtensionAbility** owns the context capability of **InputMethodExtensionContext**.

| Class | Description |
|---|---|
| InputMethodExtensionAbility | Base class of the input method ExtensionAbility, providing the lifecycle management framework for input method apps. Key members include: the **context** property (an **InputMethodExtensionContext** object), the **onCreate(want)** method (initialization callback), and the **onDestroy()** method (destruction callback). You need to inherit this class and override the lifecycle method. |

## Constraints

To ensure system security and stability and prevent **InputMethodExtensionAbility** from abusing system resources, the system imposes capability control. References to certain modules are not supported. For details, see [Appendix](#appendix).

In addition, input method apps are classified into basic mode and full experience mode. The two modes are described as follows:

**Basic mode:**
In basic mode, the input method extension (**InputMethodExtensionAbility**) process cannot launch other UIAbilities or ExtensionAbilities.

In basic mode, the input method extension is subject to system control. It cannot use various APIs that access or expose user's personal data, nor can it transfer data out of the process. The controlled features include but are not limited to: network, SMS, telephony, microphone, location, camera, Bluetooth, wallpaper, payment, calendar, game, speaker, Wi-Fi, clipboard, multimedia, contacts, common events, system accounts, health data, map services, push services, unified search, shared memory, distributed features, advertising device identifiers, and vibration.

In basic mode, the input method extension can use the system capabilities necessary for basic input features, such as IME Kit, ArkUI, window, graphics, and screen management.

In basic mode, the input method extension has read-only access to the shared sandbox and read/write access to its dedicated sandbox. The main app entry has read/write access to both the shared sandbox and its dedicated sandbox.

**Full experience mode:**

In full experience mode, the input method extension is not subject to the restrictions of basic mode. For example, it can launch other UIAbilities or ExtensionAbilities and call APIs that access user data.

In full experience mode, the input method extension has read/write access to the shared sandbox.

## Modules to Import

```ts
import { InputMethodExtensionAbility } from '@kit.IMEKit';
```

## InputMethodExtensionAbility

Provides the core capabilities for input method apps and supports you in creating input method apps.

To use the following APIs, you need to create a subclass that inherits from **InputMethodExtensionAbility** and then override or use them in the subclass.

**Model restriction:** This API can be used only in the stage model.

**System capability**: SystemCapability.MiscServices.InputMethodFramework

| Name| Type| Read-Only| Optional| Description|
| -------- | -------- | -------- | -------- | -------- |
| context | [InputMethodExtensionContext](js-apis-inputmethod-extension-context.md) | No | No | Context of the **InputMethodExtensionAbility**, inherited from **ExtensionContext**. |

Suggestions for using the **context** parameter:

- Meaning/Function: Provides an **InputMethodExtensionContext** object for performing context-level operations of an input method app, including destroying the context (**destroy()**) and launching other apps (**startAbility()**).

- Usage scenarios: Use the **context** property when the input method app needs to actively terminate itself or launch a target app. **context** becomes available after the **onCreate** callback is triggered.

- Use effect: **context.destroy()** can be used to destroy the current ExtensionAbility, and **context.startAbility(want)** can be used to launch the target app.

- Preconditions: **context** is automatically assigned by the system when the **InputMethodExtensionAbility** instance is created, and you do not need to create it manually. **context** is valid only within the ExtensionAbility lifecycle, and after the **onDestroy** callback is executed, **context** becomes unavailable.

- Usage with related APIs: **context** must be used together with the **@ohos.inputMethodEngine** module. In the **onCreate** callback, **context** is passed as a parameter of **InputMethodAbility.createPanel()** to create the input method panel.

### onCreate

onCreate(want: Want): void

Lifecycle callback invoked when the input method extension is started for initializing the input method app.

- Meaning/Function: Initialization callback triggered when the system starts the input method ExtensionAbility. In this callback, you perform all key initialization work for the input method app, including obtaining core capability objects, creating the input method panel, and subscribing to events.

- Usage scenarios: Automatically triggered when the system starts the input method ExtensionAbility according to **module.json5**. This is the only entry for initializing the input method app. Acquisition of all key objects and panel creation must be completed within this callback.

- Use effect: After the callback finishes execution, the input method app enters the normal running state. The system subsequently triggers events such as keyboard show/hide requests and client attachment. The input method app must finish initialization (for example, subscribing to the **on('inputStart')** event and creating panels) before these events arrive; otherwise, subsequent events may not be responded to properly.

**Model restriction:** This API can be used only in the stage model.

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Parameters**

| Name| Type         | Mandatory| Description                            |
| ------ | ----------- | ---- | ------------------------------- |
| want   | [Want](../apis-ability-kit/js-apis-app-ability-want.md) | Yes   | Want type information related to the current extension, including the ability name, bundle name, and more. |

Suggestions for using the **want** parameter:

- Meaning/Function: Want information passed by the system to the **onCreate** callback, describing the startup information of the current ExtensionAbility.

- Usage scenarios: Obtain startup parameters (such as **abilityName** and **bundleName**) through **want** to determine the startup scenario or obtain configuration parameters.

- Value range: Want objects contain properties of multiple types. Common properties such as **abilityName** and **bundleName** are of the string type. The **abilityName** and **bundleName** contained in **want** are consistent with the values configured in **module.json5**.

- Precautions: The **want** parameter is automatically passed in by the system, and you do not need to construct it manually.

**NOTE**

- Preconditions: **onCreate** is the core entry for initializing an input method app. The following key initialization tasks must be completed in **onCreate**:

  1. Obtain the **InputMethodAbility** instance via **inputMethodEngine.getInputMethodAbility()**.

  2. Obtain the **KeyboardDelegate** instance via **inputMethodEngine.getKeyboardDelegate()**.

  3. Subscribe to the **on('inputStart')** event to receive edit box attachment notifications.

  4. Create an input method panel (**InputMethodAbility.createPanel(this.context, panelInfo)**). Note that the **this.context** parameter must be passed in.

  5. Subscribe to other necessary events (such as **on('keyboardShow')** and **on('setSubtype')**).

- Development suggestions: It is recommended that you complete panel creation and event subscription in **onCreate** to avoid missing events or panel creation failures caused by initialization at other times.

Usage with related APIs: **onCreate** must be used with the following APIs:

- **inputMethodEngine.getInputMethodAbility()**: Obtains the input method capability object.

- **inputMethodEngine.getKeyboardDelegate()**: Obtains the keyboard delegate object.

- **InputMethodAbility.createPanel(this.context, panelInfo)**: When creating a panel, you must use **this.context** as the parameter, which is available in **onCreate**.

- **InputMethodAbility.on('inputStart')**: This must be subscribed to inside **onCreate**; otherwise, subsequent edit box attachment events cannot be received.

**Example**

```ts
import { InputMethodExtensionAbility, InputMethodAbility, KeyboardDelegate, PanelInfo, PanelType, PanelFlag, inputMethodEngine } from '@kit.IMEKit';
import { Want } from '@kit.AbilityKit';

class InputMethodExt extends InputMethodExtensionAbility {
  onCreate(want: Want): void {
    console.info(`onCreate, want: ${want.abilityName}`);

    // Obtain the input method capability object.
    let ability: InputMethodAbility = inputMethodEngine.getInputMethodAbility();

    // Obtain the keyboard proxy object.
    let keyboardDelegate: KeyboardDelegate = inputMethodEngine.getKeyboardDelegate();

    // Create a panel.
    let panelInfo: PanelInfo = {
      type: PanelType.SOFT_KEYBOARD,
      flag: PanelFlag.FLG_FIXED
    };
    ability.createPanel(this.context, panelInfo, (err, panel) => {
      if (err) {
        console.error(`Failed to create panel: ${err.code}`);
        return;
      }
      console.info('Succeeded in creating panel.');
    });

    // Subscribe to the input method attachment event.
    ability.on('inputStart', (kbController, inputClient) => {
      console.info('Input method bound to client.');
    });
  }
}
```

### onDestroy

onDestroy(): void

Lifecycle callback invoked when the input method app is destroyed for resource cleanup.

- Meaning/Function: Cleanup callback triggered when the system destroys the input method ExtensionAbility. In this callback, you release panels, cancel event subscriptions, and perform other resource cleanup work.

- Usage scenarios: Automatically triggered when the system proactively destroys the input method ExtensionAbility (for example, when the system reclaims resources or the user switches to another input method) or when you proactively call **context.destroy()** to trigger destruction. Note: After the **onDestroy** callback is executed, **context** becomes unavailable, and the **context** object should not be used during or after the callback.

- Use effect: After the callback execution completes, the input method ExtensionAbility process is terminated, and all resources are released. Any subsequent operations will have no effect.

**Model restriction:** This API can be used only in the stage model.

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**NOTE**

- Development suggestions: It is recommended that you perform the following cleanup tasks in **onDestroy**:

  1. Destroy the created panel (**InputMethodAbility.destroyPanel(panel)**).

  2. Cancel all event subscriptions (such as **InputMethodAbility.off('inputStart')**).

  3. Release other app resources (such as cached data and timers).

- Development suggestions: Failure to properly destroy panels in **onDestroy** may cause panel resource leaks and affect system resource usage.

Usage with related APIs: **onDestroy** must be used with the following APIs:

- **InputMethodAbility.destroyPanel(panel)**: Destroys the panel created in **onCreate**. It must be called in pair with **createPanel**.

- **InputMethodAbility.off('inputStart')** and more: Unsubscribe from the events subscribed in **onCreate**.

- **context.destroy()**: When you actively call **context.destroy()**, the system executes the **onDestroy** callback.

**Example**

```ts
import { InputMethodExtensionAbility } from '@kit.IMEKit';

class InputMethodExt extends InputMethodExtensionAbility {
  onDestroy(): void {
    // Destroy the panel, cancel event subscriptions, and perform other cleanup tasks.
    console.info('onDestroy');
  }
}
```

## Appendix

**InputMethodExtensionAbility** does not support references to the following modules.

| Kit | Module |
| -------- | -------- |
| Ability Kit |  [@ohos.ability.featureAbility (FeatureAbility Module)](../apis-ability-kit/js-apis-ability-featureAbility.md)</br>[@ohos.ability.particleAbility (ParticleAbility Module)](../apis-ability-kit/js-apis-ability-particleAbility.md) |
| Background Tasks Kit |  [@ohos.resourceschedule.backgroundTaskManager (Background Task Management)](../apis-backgroundtasks-kit/js-apis-resourceschedule-backgroundTaskManager.md)</br>[@ohos.reminderAgentManager (Agent-powered Reminder)](../apis-backgroundtasks-kit/js-apis-reminderAgentManager.md)</br> [@ohos.reminderAgent (Agent-powered Reminder)](../apis-backgroundtasks-kit/js-apis-reminderAgent.md) |
| Basic Services Kit | [@ohos.account.osAccount (OS Account Management)](../apis-basic-services-kit/js-apis-osAccount.md)</br>[@ohos.account.distributedAccount (Distributed Account Management)](../apis-basic-services-kit/js-apis-distributed-account.md)</br>[@ohos.wallpaper (Wallpaper)](../apis-basic-services-kit/js-apis-wallpaper.md) |
| Connectivity Kit |  [@ohos.bluetooth (Bluetooth)](../apis-connectivity-kit/js-apis-bluetooth.md)</br>[@ohos.bluetoothManager (Bluetooth)](../apis-connectivity-kit/js-apis-bluetoothManager.md)</br>[nfctech (Standard NFC Technology)](../apis-connectivity-kit/js-apis-nfctech.md)</br>[@ohos.nfc.controller (Standard NFC)](../apis-connectivity-kit/js-apis-nfcController.md)</br>[@ohos.nfc.cardEmulation (Standard NFC Card Emulation)](../apis-connectivity-kit/js-apis-cardEmulation.md)</br>[@ohos.connectedTag (Active Tags)](../apis-connectivity-kit/js-apis-connectedTag.md)</br>[@ohos.wifiext (WLAN Extension)](../apis-connectivity-kit/js-apis-wifiext.md)</br>[@ohos.wifiManager (WLAN)](../apis-connectivity-kit/js-apis-wifiManager.md)</br>[@ohos.wifiManagerExt (WLAN Extension)](../apis-connectivity-kit/js-apis-wifiManagerExt.md)</br>[tagSession (Standard NFC Tag Session)](../apis-connectivity-kit/js-apis-tagSession.md)</br> |
| Location Kit | [@ohos.geolocation (Geolocation)](../apis-location-kit/js-apis-geolocation.md)</br>[@ohos.geoLocationManager (Geolocation Manager)](../apis-location-kit/js-apis-geoLocationManager.md) |
| Telephony Kit | [@ohos.telephony.call (Call)](../apis-telephony-kit/js-apis-call.md)</br>[@ohos.telephony.data (Cellular Data)](../apis-telephony-kit/js-apis-telephony-data.md)</br>[@ohos.telephony.observer (Telephony Status Observer)](../apis-telephony-kit/js-apis-observer.md)</br>[@ohos.telephony.radio (Network Search)](../apis-telephony-kit/js-apis-radio.md)</br>[@ohos.telephony.sms (SMS)](../apis-telephony-kit/js-apis-sms.md)</br>[@ohos.telephony.sim (SIM Management)](../apis-telephony-kit/js-apis-sim.md) |