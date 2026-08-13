# MenuItemGroup

该组件用于展示MenuItem的分组，支持设置分组的标题和尾部信息，用于组织和管理菜单项的分类结构。适用于需要在菜单中按类别组织多个菜单项的场景，通过分组清晰地展示菜单的层次结构，提升菜单的可读性和用户体验。 > **说明：** > - 该组件从API版本26.0.0开始支持WithTheme。

## 子组件 包含MenuItem子组件。

## MenuItemGroup

```TypeScript
MenuItemGroup(value?: MenuItemGroupOptions)
```

**起始版本：** 9

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为9。

**废弃版本：** -1

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-MenuItemGroupInterface-(value?: MenuItemGroupOptions): MenuItemGroupAttribute--><!--Device-MenuItemGroupInterface-(value?: MenuItemGroupOptions): MenuItemGroupAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [MenuItemGroupOptions](arkts-arkui-menuitemgroupoptions-i.md) | 否 | 设置MenuItemGroup的标题和尾部信息。<br/> 未设置时，不显示标题和尾部信息。 |

## 汇总

- [MenuItemGroupOptions](arkts-arkui-menuitemgroupoptions-i.md)
