# 常量

## SelectionContainer

```TypeScript
export declare const SelectionContainer: SelectionContainerInterface
```

SelectionContainer组件用于为多个文本节点提供跨节点文本选中、复制及菜单扩展能力，支持统一配置选中文本的手柄颜色和底板颜色，支持灵活的文本拼接策略，支持自定义选择菜单和扩展菜单选项。适用于需要跨多个Text组件实现文本 连续选中、统一复制、样式自定义及菜单扩展的场景，解决了多Text组件场景下文本选择体验割裂的问题，提升了用户在复杂文本布局中的交互体验。 > **说明：** > > - 本组件中选中文本相关回调返回的文本内容，按照Text组件的从上到下显示顺序进行拼接。 > > - 本组件默认布局走Stack，如有其他容器布局需求请在SelectionContainer内放置一个容器组件。 > > - SelectionContainer内跨节点选中文本时不显示放大镜，也不支持[getMagnifier](../../apis-na/arkts-apis/arkts-na-arkui-uicontext-uicontext-c.md#getmagnifier)主动设置放大镜。 > > - 仅Text组件中的文本内容参与跨节点选中与文本拼接。

### 子组件 可以包含子组件。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-unnamed-export declare const SelectionContainer: SelectionContainerInterface--><!--Device-unnamed-export declare const SelectionContainer: SelectionContainerInterface-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## SelectionContainerInstance

```TypeScript
export declare const SelectionContainerInstance: SelectionContainerAttribute
```

定义SelectionContainer组件实例。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-unnamed-export declare const SelectionContainerInstance: SelectionContainerAttribute--><!--Device-unnamed-export declare const SelectionContainerInstance: SelectionContainerAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

