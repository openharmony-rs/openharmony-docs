# MarqueeDynamicSyncScene

提供Marquee组件动态帧率的配置能力，支持在Marquee组件运行动画时动态调节帧率，优化性能和功耗，适用于需要在跑马灯场景中平衡动画流畅度和系统资源消耗的场景。

**继承/实现关系：** MarqueeDynamicSyncScene extends [DynamicSyncScene](arkts-arkui-arkui-uicontext-dynamicsyncscene-c.md#DynamicSyncScene)

**起始版本：** 14

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为14。

**废弃版本：** -1

<!--Device-unnamed-export class MarqueeDynamicSyncScene--><!--Device-unnamed-export class MarqueeDynamicSyncScene-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## type

```TypeScript
readonly type: MarqueeDynamicSyncSceneType
```

Marquee的动态帧率场景类型。用于指定Marquee组件的动态帧率场景模式，不同场景类型对应不同的帧率调节策略，详见MarqueeDynamicSyncSceneType。

**类型：** [MarqueeDynamicSyncSceneType](arkts-arkui-arkui-uicontext-marqueedynamicsyncscenetype-e.md)

**起始版本：** 14

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为14。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

<!--Device-MarqueeDynamicSyncScene-readonly type: MarqueeDynamicSyncSceneType--><!--Device-MarqueeDynamicSyncScene-readonly type: MarqueeDynamicSyncSceneType-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

