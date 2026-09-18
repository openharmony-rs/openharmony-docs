# SelectionExtensionContext

**SelectionExtensionContext** is the context of [SelectionExtensionAbility](arkts-basicservices-selectioninput-selectionextensionability-selectionextensionability-c.md), which inherits from [ExtensionContext](../../apis-ability-kit/arkts-apis/arkts-ability-extensioncontext-c.md).

When a **SelectionExtensionAbility** component is instantiated, the system automatically creates the corresponding **SelectionExtensionContext**. You can call the [startAbility](#startability) API in **SelectionExtensionContext** to start other abilities in the same app. This is applicable when you need to redirect to another ability in the same app in word selection extension, helping users quickly obtain the functions or information associated with the selected word.

> **NOTE:** 
> 
> - This module is supported only on PCs/2-in-1 devices. You can use
> **canIUse('SystemCapability.SelectionInput.Selection')** to check whether the current device supports this
> function.

**Inheritance/Implementation:** SelectionExtensionContext extends [ExtensionContext](../../apis-ability-kit/arkts-apis/arkts-ability-extensioncontext-c.md)

**Since:** 24

**System capability:** SystemCapability.SelectionInput.Selection

## Modules to Import

```TypeScript
import { SelectionExtensionContext } from '@kit.BasicServicesKit';
```

## startAbility

```TypeScript
startAbility(want: Want): Promise<void>
```

Starts the target ability in the same app. This method is applicable when you need to redirect to another ability in the app in word selection extension. The system matches and starts the target ability based on the values of **bundleName** and **abilityName** specified in the **Want** object. This API uses a promise to return the result. For details about the ability startup mechanism, see [ExtensionContext](../../apis-ability-kit/arkts-apis/arkts-ability-extensioncontext-c.md).

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.SelectionInput.Selection

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| want | [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md) | Yes | Information about the target app to start. The main fields include **bundleName** (bundle name of the target app) and **abilityName** (name of the target ability). After this parameter is set, the system searches for and starts the corresponding ability based on the specified bundle name and ability name. Only abilities within the same app can be started. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [16000001](../../apis-ability-kit/errorcode-ability.md#16000001-ability-name-does-not-exist) | The specified ability does not exist. |
| [16000002](../../apis-ability-kit/errorcode-ability.md#16000002-incorrect-ability-type) | Incorrect ability type. |
| [16000004](../../apis-ability-kit/errorcode-ability.md#16000004-visibility-verification-failure) | Cannot start an invisible component. |
| [16000005](../../apis-ability-kit/errorcode-ability.md#16000005-process-permission-verification-failure) | The specified process does not have the permission. |
| [16000006](../../apis-ability-kit/errorcode-ability.md#16000006-cross-user-operation-is-not-allowed) | Cross-user operations are not allowed. |
| [16000008](../../apis-ability-kit/errorcode-ability.md#16000008-crowdtesting-application-expires) | The crowdtesting application expires. |
| [16000009](../../apis-ability-kit/errorcode-ability.md#16000009-ability-start-or-stop-failure-in-wukong-mode) | An ability cannot be started or stopped in Wukong mode. |
| [16000010](../../apis-ability-kit/errorcode-ability.md#16000010-continuation-flag-is-forbidden) | The call with the continuation and prepare continuation flag is forbidden. |
| [16000011](../../apis-ability-kit/errorcode-ability.md#16000011-context-does-not-exist) | The context does not exist. |
| [16000012](../../apis-ability-kit/errorcode-ability.md#16000012-application-under-control) | The application is controlled. |
| [16000013](../../apis-ability-kit/errorcode-ability.md#16000013-application-controlled-by-edm) | The application is controlled by EDM. |
| [16000019](../../apis-ability-kit/errorcode-ability.md#16000019-no-matching-ability-found-for-implicit-start) | No matching ability is found. |
| [16000050](../../apis-ability-kit/errorcode-ability.md#16000050-internal-error) | Internal error. |
| [16000053](../../apis-ability-kit/errorcode-ability.md#16000053-ability-not-in-the-foreground) | The ability is not on the top of the UI. |
| [16000055](../../apis-ability-kit/errorcode-ability.md#16000055-installation-free-timeout) | Installation-free timed out. |
| [16000061](../../apis-ability-kit/errorcode-ability.md#16000061-unsupported-operation) | Operation not supported. |
| [16000069](../../apis-ability-kit/errorcode-ability.md#16000069-extensionability-fails-to-start-a-third-party-application-in-strict-mode) | The extension cannot start the third party application. |
| [16000070](../../apis-ability-kit/errorcode-ability.md#16000070-extensionability-fails-to-start-a-serviceextensionability-in-strict-mode) | The extension cannot start the service. |
| [16000083](../../apis-ability-kit/errorcode-ability.md#16000083-specified-ability-cannot-be-started-by-this-type-of-extensionability) | The ExtensionAbility cannot start the ability due to system control. |
| [16200001](../../apis-ability-kit/errorcode-ability.md#16200001-caller-released) | The caller has been released. |

**Examples**

```TypeScript
import { SelectionExtensionAbility, BusinessError } from '@kit.BasicServicesKit';
import { rpc } from '@kit.IPCKit';
import { Want } from '@kit.AbilityKit';

class SelectionAbilityStub extends rpc.RemoteObject {
  constructor(descriptor: string) {
    super(descriptor);
  }
  onRemoteMessageRequest(
    code: number,
    data: rpc.MessageSequence,
    reply: rpc.MessageSequence,
    options: rpc.MessageOption
  ): boolean | Promise<boolean> {
    console.info(`onRemoteMessageRequest code: ${code}`);
    return true;
  }
}

class SelectionExtAbility extends SelectionExtensionAbility {
  onConnect(want: Want): rpc.RemoteObject {
    try {
      // Construct a Want object to specify the target ability to start.
      let wantAbility: Want = {
        bundleName: 'com.selection.selectionapplication',
        abilityName: 'EntryAbility',
      };
      // Start the target ability. this.context is automatically provided by the SelectionExtensionAbility instance and does not need to be obtained separately.
      this.context.startAbility(wantAbility).then(() => {
        console.info(`startAbility success`);
      }).catch((err: BusinessError) => {
        console.error(`Failed to startAbility. Error code: ${err.code}, error message: ${err.message}`);
      });
    } catch (err) {
      console.error(`Failed to startAbility. Error code: ${err.code}, error message: ${err.message}`);
    }
    return new SelectionAbilityStub('remote');
  }
}
```
