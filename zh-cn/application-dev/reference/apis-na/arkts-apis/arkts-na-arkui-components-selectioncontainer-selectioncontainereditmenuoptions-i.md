# SelectionContainerEditMenuOptions

SelectionContainer自定义编辑菜单选项。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**废弃版本：** -1

<!--Device-unnamed-export declare interface SelectionContainerEditMenuOptions--><!--Device-unnamed-export declare interface SelectionContainerEditMenuOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onCreateMenu

```TypeScript
onCreateMenu?: OnCreateMenuCallback
```

每次菜单显示前触发，传入默认菜单项并返回处理后的菜单项。默认值为空，不触发该回调。

**类型：** OnCreateMenuCallback

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SelectionContainerEditMenuOptions-onCreateMenu?: OnCreateMenuCallback--><!--Device-SelectionContainerEditMenuOptions-onCreateMenu?: OnCreateMenuCallback-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onMenuItemClick

```TypeScript
onMenuItemClick?: OnMenuItemClickWithTextCallback
```

点击菜单项时触发，可拦截系统默认菜单执行行为。默认值为空，不触发该回调。

**类型：** [OnMenuItemClickWithTextCallback](../../apis-arkui/arkts-apis/arkts-arkui-onmenuitemclickwithtextcallback-t.md)

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SelectionContainerEditMenuOptions-onMenuItemClick?: OnMenuItemClickWithTextCallback--><!--Device-SelectionContainerEditMenuOptions-onMenuItemClick?: OnMenuItemClickWithTextCallback-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onPrepareMenu

```TypeScript
onPrepareMenu?: OnPrepareMenuCallback
```

文本选中内容变化后、菜单显示前触发，可在该回调中调整菜单数据。默认值为空，不触发该回调。

**类型：** OnPrepareMenuCallback

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SelectionContainerEditMenuOptions-onPrepareMenu?: OnPrepareMenuCallback--><!--Device-SelectionContainerEditMenuOptions-onPrepareMenu?: OnPrepareMenuCallback-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

