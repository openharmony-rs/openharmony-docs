# WindowExtensionAbility（系统接口）

WindowExtensionAbility类。

**起始版本：** 9

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为9。

**废弃版本：** 21

<!--Device-unnamed-declare class WindowExtensionAbility--><!--Device-unnamed-declare class WindowExtensionAbility-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**系统接口：** 此接口为系统接口。

## onConnect

```TypeScript
onConnect(want: Want): void
```

当窗口扩展组件第一次连接ability时回调。

**起始版本：** 9

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为9。

**废弃版本：** 21

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-WindowExtensionAbility-onConnect(want: Want): void--><!--Device-WindowExtensionAbility-onConnect(want: Want): void-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| want | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 当前ability的Want类型信息，包括ability名称、bundle名称等。 |

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

## onDisconnect

```TypeScript
onDisconnect(want: Want): void
```

当所有连接到窗口扩展组件的ability断开连接时回调。

**起始版本：** 9

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为9。

**废弃版本：** 21

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-WindowExtensionAbility-onDisconnect(want: Want): void--><!--Device-WindowExtensionAbility-onDisconnect(want: Want): void-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| want | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 当前Ability的Want类型信息，包括ability名称、bundle名称等。 |

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

## onWindowReady

```TypeScript
onWindowReady(window: window.Window): void
```

当窗口被创建时回调。

**起始版本：** 9

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为9。

**废弃版本：** 21

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-WindowExtensionAbility-onWindowReady(window: window.Window): void--><!--Device-WindowExtensionAbility-onWindowReady(window: window.Window): void-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| window | window.Window | 是 | 当前窗口实例。 |

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

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为9。

**废弃版本：** 21

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-WindowExtensionAbility-context: WindowExtensionContext--><!--Device-WindowExtensionAbility-context: WindowExtensionContext-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**系统接口：** 此接口为系统接口。

