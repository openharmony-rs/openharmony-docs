# SwiperDynamicSyncScene

提供Swiper组件动态帧率场景的相关配置，适用于为动画过渡和手势跟手等不同交互场景设置差异化帧率范围，以兼顾流畅度和功耗。 > **说明：**> SwiperDynamicSyncScene继承自[DynamicSyncScene](arkts-arkui-arkui-uicontext-uicontext-c.md#UIContext)，对应Swiper的动态帧率场景。使用前需先通过UIContext的requireDynamicSyncScene方法获取实例，再调用继承的方法设置对应场景的帧率范围。

**继承/实现关系：** SwiperDynamicSyncScene extends [DynamicSyncScene](arkts-arkui-arkui-uicontext-dynamicsyncscene-c.md#DynamicSyncScene)

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**废弃版本：** -1

<!--Device-unnamed-export class SwiperDynamicSyncScene--><!--Device-unnamed-export class SwiperDynamicSyncScene-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## type

```TypeScript
readonly type: SwiperDynamicSyncSceneType
```

Swiper的动态帧率场景类型。

**类型：** [SwiperDynamicSyncSceneType](arkts-arkui-arkui-uicontext-swiperdynamicsyncscenetype-e.md)

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-SwiperDynamicSyncScene-readonly type: SwiperDynamicSyncSceneType--><!--Device-SwiperDynamicSyncScene-readonly type: SwiperDynamicSyncSceneType-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

