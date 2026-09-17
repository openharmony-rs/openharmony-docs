# DistributedExtensionAbility

The **DistributedExtensionAbility** module provides distributed extension capabilities and lifecycle callbacks for distributed ability creation, destruction, and connection.

**Since:** 20

**System capability:** SystemCapability.DistributedSched.AppCollaboration

## Modules to Import

```TypeScript
import { DistributedExtensionAbility } from '@kit.DistributedServiceKit';
```

## onCollaborate

```TypeScript
onCollaborate(wantParam: Record<string, Object>): AbilityConstant.CollaborateResult
```

Callback invoked to return the collaboration result in multi-device collaboration scenarios.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedSched.AppCollaboration

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| wantParam | Record&lt;string, Object&gt; | Yes | Want parameter, which supports only the key **"ohos.extra.param.key.supportCollaborateIndex"**. The key can be used to obtain the data passed by the caller and perform corresponding processing. |

**Return value:**

| Type | Description |
| --- | --- |
| [AbilityConstant.CollaborateResult](../../apis-ability-kit/arkts-apis/arkts-ability-abilityconstant-collaborateresult-e.md) | Collaboration result, that is, whether the target application accepts the collaboration request. |

**Examples**

```TypeScript
import { abilityConnectionManager, DistributedExtensionAbility } from '@kit.DistributedServiceKit';
import { AbilityConstant } from '@kit.AbilityKit';

export default class DistributedExtension extends DistributedExtensionAbility {
  onCollaborate(wantParam: Record<string, Object>) {
    console.info(`DistributedExtension onCollabRequest Accept to the result of Ability collaborate`);
    let sessionId = -1;
    const collaborationValues = wantParam["CollaborationValues"] as abilityConnectionManager.CollaborationValues;
    if (collaborationValues == undefined) {
      return sessionId;
    }
    console.info(`onCollab, collaborationValues: ${JSON.stringify(collaborationValues)}`);
    return AbilityConstant.CollaborateResult.ACCEPT;
  }
}
```

## onCreate

```TypeScript
onCreate(want: Want): void
```

Callback invoked to initialize the service logic when a **DistributedExtensionAbility** instance is created.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedSched.AppCollaboration

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| want | [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md) | Yes | Want information related to the **DistributedExtensionAbility** instance, including the ability name and bundle name. |

**Examples**

```TypeScript
import { Want } from '@kit.AbilityKit';
import { DistributedExtensionAbility } from '@kit.DistributedServiceKit';

export default class DistributedExtension extends DistributedExtensionAbility {
  onCreate(want: Want) {
    console.info(`DistributedExtension Create ok`);
    console.info(`DistributedExtension on Create want: ${JSON.stringify(want)}`);
    console.info(`DistributedExtension Create end`);
  }
}
```

## onDestroy

```TypeScript
onDestroy(): void
```

Callback invoked to clear resources when a **ServiceExtensionAbility** instance is destroyed.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedSched.AppCollaboration

**Examples**

```TypeScript
import { DistributedExtensionAbility } from '@kit.DistributedServiceKit';

export default class DistributedExtension extends DistributedExtensionAbility {
  onDestroy() {
    console.info('DistributedExtension onDestroy ok');
  }
}
```

## context

```TypeScript
context: DistributedExtensionContext
```

Context of the **DistributedExtension**. This context inherits from **ExtensionContext**.

**Type:** [DistributedExtensionContext](arkts-distributedservice-application-distributedextensioncontext-distributedextensioncontext-c.md)

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedSched.AppCollaboration
