# EditMenuOptions

EditMenuOptions

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare interface EditMenuOptions--><!--Device-unnamed-export declare interface EditMenuOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onCreateMenu

```TypeScript
onCreateMenu: OnCreateMenuCallback | undefined
```

在菜单创建时触发该回调，可在该回调中进行菜单数据设置。

**类型：** OnCreateMenuCallback \| undefined

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-EditMenuOptions-onCreateMenu: OnCreateMenuCallback | undefined--><!--Device-EditMenuOptions-onCreateMenu: OnCreateMenuCallback | undefined-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onMenuItemClick

```TypeScript
onMenuItemClick: OnMenuItemClickCallback | undefined
```

在菜单项被点击时触发该回调，用于处理菜单项的点击行为。

**类型：** OnMenuItemClickCallback \| undefined

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-EditMenuOptions-onMenuItemClick: OnMenuItemClickCallback | undefined--><!--Device-EditMenuOptions-onMenuItemClick: OnMenuItemClickCallback | undefined-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onPrepareMenu

```TypeScript
onPrepareMenu?: OnPrepareMenuCallback
```

当文本选择区域变化后显示菜单之前触发该回调，可在该回调中进行菜单数据设置。 与onCreateMenu功能相似但触发时机不同：onCreateMenu在菜单创建时触发，适用于初始化菜单项； 本接口在每次选择区域变化后、菜单显示前触发，适用于根据选择内容动态调整菜单。两者可同时使用。

**类型：** OnPrepareMenuCallback

**起始版本：** 24

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为24。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-EditMenuOptions-onPrepareMenu?: OnPrepareMenuCallback--><!--Device-EditMenuOptions-onPrepareMenu?: OnPrepareMenuCallback-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

