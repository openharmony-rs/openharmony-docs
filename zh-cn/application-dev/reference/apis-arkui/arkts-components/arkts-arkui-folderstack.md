# FolderStack

FolderStack继承自[Stack]{@link ./stack}（层叠布局）控件，新增了<!--RP1-->折叠屏悬停<!--RP1End-->能力，通过在FolderStack的配置项 [FolderStackOptions]{@link FolderStackOptions}的upperItems数组上设置子组件id，使相应子组件自动避让折叠屏折痕区后移到上半屏。FolderStack适用于双折叠设备的悬停态场景， 如视频播放、视频会议等应用，实现视频画面自动移至上半屏、控制面板保留在下半屏的布局。该组件能解决双折叠设备适配问题，带来提升用户体验、简化开发者布局适配工作的收益。 > **说明：** > > - 该组件从API version 11开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。 > > - 该组件的悬停态能力针对<!--RP2-->双折叠<!--RP2End-->设计，只在双折叠设备生效。可通过[FoldStatus]{@link FoldStatus}判断设备的折叠状态。 > > - 当该组件的父组件为[if/else：条件渲染](docroot://ui/rendering-control/arkts-rendering-control-ifelse.md)节点时，折叠屏悬停能力将会失效。

## 子组件 可以包含多个子组件。

## FolderStack

```TypeScript
FolderStack(options?: FolderStackOptions)
```

折叠屏悬停布局容器，继承自[Stack]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_，通过配置upperItems实现折叠屏悬停能力。当设备处于悬停态时，指定子组件自动移至上半屏，其他组件堆叠在下半屏。

**起始版本：** 11

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为11。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-FolderStackInterface-(options?: FolderStackOptions): FolderStackAttribute--><!--Device-FolderStackInterface-(options?: FolderStackOptions): FolderStackAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 否 | FolderStack的配置项，用于设置悬停态时需要移到上半屏的子组件。当需要使用折叠屏悬停能力时，通过upperItems数组指定子组件id；不 传入时FolderStack作为普通Stack组件使用，不启用悬停能力，upperItems默认为空数组。 |

## 汇总

