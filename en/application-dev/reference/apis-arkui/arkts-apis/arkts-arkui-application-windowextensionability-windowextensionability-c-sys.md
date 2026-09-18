# WindowExtensionAbility (System API)

class of window extension ability.

**Since:** 9

**Deprecated since:** 21

**System capability:** SystemCapability.WindowManager.WindowManager.Core

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { WindowExtensionAbility, WindowExtensionContext } from '@kit.ArkUI';
```

## onConnect

```TypeScript
onConnect(want: Want): void
```

Called back when a window extension is first connected to an ability.

**Since:** 9

**Deprecated since:** 21

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.WindowManager.WindowManager.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| want | [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md) | Yes | Indicates connection information about the Window ability. |

**Examples**

```TypeScript
import { WindowExtensionAbility } from '@kit.ArkUI';
import { Want } from '@kit.AbilityKit';

export default class MyWindowExtensionAbility extends WindowExtensionAbility {
  onConnect(want: Want) {
    console.info(`WindowExtAbility onConnect, abilityName: ${want.abilityName}`);
  }
}
```

## onDisconnect

```TypeScript
onDisconnect(want: Want): void
```

Called back when all abilities connected to a window extension are disconnected.

**Since:** 9

**Deprecated since:** 21

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.WindowManager.WindowManager.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| want | [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md) | Yes | Indicates disconnection information about the window extension. |

**Examples**

```TypeScript
import { WindowExtensionAbility } from '@kit.ArkUI';
import { Want } from '@kit.AbilityKit';

export default class MyWindowExtensionAbility extends WindowExtensionAbility {
  onDisconnect(want: Want) {
    console.info(`WindowExtAbility onDisconnect, abilityName: ${want.abilityName}`);
  }
}
```

## onWindowReady

```TypeScript
onWindowReady(window: window.Window): void
```

Called back when window is created.

**Since:** 9

**Deprecated since:** 21

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.WindowManager.WindowManager.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| window | [window.Window](arkts-arkui-window-window-i.md) | Yes | Current Window instance. |

**Examples**

```TypeScript
import { WindowExtensionAbility, window } from '@kit.ArkUI';
import { BusinessError } from '@kit.BasicServicesKit';

export default class MyWindowExtensionAbility extends WindowExtensionAbility {
  onWindowReady(window: window.Window) {
    window.setUIContent('WindowExtAbility/pages/index1',(err:BusinessError) => {
      let pro = window.getWindowProperties();
      console.info(`WindowExtension pro: ${JSON.stringify(pro)}`);
      window.showWindow();
    });
  }
}
```

## context

```TypeScript
context: WindowExtensionContext
```

Indicates window extension ability context.

**Type:** [WindowExtensionContext](arkts-arkui-windowextensioncontext-t-sys.md)

**Since:** 9

**Deprecated since:** 21

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.WindowManager.WindowManager.Core

**System API:** This is a system API.
