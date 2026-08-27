# RequestInfo

表示发起方请求信息，作为窗口绑定模态弹框的入参。

**起始版本：** 9

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## 导入模块

```TypeScript
import { dialogRequest } from '@kit.AbilityKit';
```

## windowRect

```TypeScript
windowRect?: WindowRect
```

表示模态弹框的位置属性。

**类型：** [WindowRect](arkts-ability-dialogrequest-windowrect-i.md)

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**示例**

```TypeScript
import { AbilityConstant, UIAbility, Want, dialogRequest } from '@kit.AbilityKit';

export default class EntryAbility extends UIAbility {
  onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
    try {
      // 获取请求方的RequestInfo
      let requestInfo = dialogRequest.getRequestInfo(want);
      console.info(`getRequestInfo windowRect=, ${JSON.stringify(requestInfo.windowRect)}` );
    } catch (err) {
      console.error(`Failed to getRequestInfo. Code: ${err.code}, message: ${err.message}`);
    }
  }
}
```
