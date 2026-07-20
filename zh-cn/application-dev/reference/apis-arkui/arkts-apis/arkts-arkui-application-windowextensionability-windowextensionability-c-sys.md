# WindowExtensionAbility（系统接口）

class of window extension ability.

**起始版本：** 9

**废弃版本：** 21

<!--Device-unnamed-declare class WindowExtensionAbility--><!--Device-unnamed-declare class WindowExtensionAbility-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { WindowExtensionContext } from '@kit.ArkUI';
```

<a id="onconnect"></a>
## onConnect

```TypeScript
onConnect(want: Want): void
```

Called back when a window extension is first connected to an ability.

**起始版本：** 9

**废弃版本：** 21

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-WindowExtensionAbility-onConnect(want: Want): void--><!--Device-WindowExtensionAbility-onConnect(want: Want): void-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| want | [Want](arkts-arkui-want-t-sys.md) | 是 | Indicates connection information about the Window ability. |

**示例：**

```TypeScript
import { WindowExtensionAbility } from '@kit.ArkUI';
import { Want } from '@kit.AbilityKit';

export default class MyWindowExtensionAbility extends WindowExtensionAbility {
  onConnect(want: Want) {
    console.info(`WindowExtAbility onConnect, abilityName: ${want.abilityName}`);
  }
}

```

<a id="ondisconnect"></a>
## onDisconnect

```TypeScript
onDisconnect(want: Want): void
```

Called back when all abilities connected to a window extension are disconnected.

**起始版本：** 9

**废弃版本：** 21

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-WindowExtensionAbility-onDisconnect(want: Want): void--><!--Device-WindowExtensionAbility-onDisconnect(want: Want): void-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| want | [Want](arkts-arkui-want-t-sys.md) | 是 | Indicates disconnection information about the window extension. |

**示例：**

```TypeScript
import { WindowExtensionAbility } from '@kit.ArkUI';
import { Want } from '@kit.AbilityKit';

export default class MyWindowExtensionAbility extends WindowExtensionAbility {
  onDisconnect(want: Want) {
    console.info(`WindowExtAbility onDisconnect, abilityName: ${want.abilityName}`);
  }
}

```

<a id="onwindowready"></a>
## onWindowReady

```TypeScript
onWindowReady(window: window.Window): void
```

Called back when window is created.

**起始版本：** 9

**废弃版本：** 21

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-WindowExtensionAbility-onWindowReady(window: window.Window): void--><!--Device-WindowExtensionAbility-onWindowReady(window: window.Window): void-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| window | window.Window | 是 | Current Window instance. |

**示例：**

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

**类型：** WindowExtensionContext

**起始版本：** 9

**废弃版本：** 21

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-WindowExtensionAbility-context: WindowExtensionContext--><!--Device-WindowExtensionAbility-context: WindowExtensionContext-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**系统接口：** 此接口为系统接口。

