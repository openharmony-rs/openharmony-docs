# AbilityFirstFrameStateObserver（系统接口）

定义了Ability首帧绘制完成事件监听对象，可以作为 [on](arkts-ability-appmanager-on-f-sys.md#onabilityfirstframestate) 的入参，用于监听Ability首帧绘制完成事件。

**起始版本：** 12

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

## onAbilityFirstFrameDrawn

```TypeScript
onAbilityFirstFrameDrawn(data: AbilityFirstFrameStateData): void
```

Ability首帧绘制完成时触发的回调函数。

**起始版本：** 12

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| data | [AbilityFirstFrameStateData](arkts-ability-abilityfirstframestatedata-i-sys.md) | 是 | 表示首帧绘制完成时返回的数据。 |

**示例**

```TypeScript
import { appManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

// 创建Ability首帧绘制状态监听对象
let observer: appManager.AbilityFirstFrameStateObserver = {
  onAbilityFirstFrameDrawn(data: appManager.AbilityFirstFrameStateData) {
    console.info(`onAbilityFirstFrameDrawn success, abilityFirstFrameStateData: ${data}.`);
  }
};

try {
  // 注册Ability首帧绘制完成事件监听
  appManager.on('abilityFirstFrameState', observer);
} catch (e) {
  let code = (e as BusinessError).code;
  let msg = (e as BusinessError).message;
  console.error(`appmanager.on failed, err code: ${code}, err msg: ${msg}.`);
}
```
