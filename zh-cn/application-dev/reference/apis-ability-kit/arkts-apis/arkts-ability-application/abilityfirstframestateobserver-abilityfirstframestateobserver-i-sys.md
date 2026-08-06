# AbilityFirstFrameStateObserver（系统接口）

定义了Ability首帧绘制完成事件监听对象，可以作为 [on]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_ 的入参，用于监听Ability首帧绘制完成事件。

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

<!--Device-unnamed-export interface AbilityFirstFrameStateObserver--><!--Device-unnamed-export interface AbilityFirstFrameStateObserver-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

## onAbilityFirstFrameDrawn

```TypeScript
onAbilityFirstFrameDrawn(data: AbilityFirstFrameStateData): void
```

Ability首帧绘制完成时触发的回调函数。

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

<!--Device-AbilityFirstFrameStateObserver-onAbilityFirstFrameDrawn(data: AbilityFirstFrameStateData): void--><!--Device-AbilityFirstFrameStateObserver-onAbilityFirstFrameDrawn(data: AbilityFirstFrameStateData): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| data | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 表示首帧绘制完成时返回的数据。 |

