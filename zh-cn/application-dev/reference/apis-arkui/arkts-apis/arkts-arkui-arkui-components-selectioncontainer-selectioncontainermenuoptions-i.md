# SelectionContainerMenuOptions

配置选择菜单中的选项。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

<!--Device-unnamed-export interface SelectionContainerMenuOptions--><!--Device-unnamed-export interface SelectionContainerMenuOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onAppear

```TypeScript
onAppear?: Callback<string>
```

选择菜单出现时触发。回调参数为按Text组件视觉顺序拼接后的选中文本，拼接方式由textJoinStyle配置决定。默认值为空，不触发该回调。

**类型：** Callback&lt;string&gt;

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-SelectionContainerMenuOptions-onAppear?: Callback<string>--><!--Device-SelectionContainerMenuOptions-onAppear?: Callback<string>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onDisappear

```TypeScript
onDisappear?: Callback<void>
```

选择菜单消失时触发。默认值为空，不触发该回调。

**类型：** Callback&lt;void&gt;

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-SelectionContainerMenuOptions-onDisappear?: Callback<void>--><!--Device-SelectionContainerMenuOptions-onDisappear?: Callback<void>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onMenuHide

```TypeScript
onMenuHide?: Callback<string>
```

选择菜单隐藏时触发。回调参数为按Text组件视觉顺序拼接后的选中文本，拼接方式由textJoinStyle配置决定。默认值为空，不触发该回调。

**类型：** Callback&lt;string&gt;

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-SelectionContainerMenuOptions-onMenuHide?: Callback<string>--><!--Device-SelectionContainerMenuOptions-onMenuHide?: Callback<string>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onMenuShow

```TypeScript
onMenuShow?: Callback<string>
```

选择菜单显示时触发。回调参数为按Text组件视觉顺序拼接后的选中文本，拼接方式由textJoinStyle配置决定。默认值为空，不触发该回调。

**类型：** Callback&lt;string&gt;

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-SelectionContainerMenuOptions-onMenuShow?: Callback<string>--><!--Device-SelectionContainerMenuOptions-onMenuShow?: Callback<string>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

