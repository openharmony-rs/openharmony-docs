# MenuItemGroupOptions

```TypeScript
declare interface MenuItemGroupOptions
```

MenuItem分组的标题和尾部信息。

**起始版本：** 9

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## footer

```TypeScript
footer?: ResourceStr | CustomBuilder
```

设置分组的菜单页脚，显示在分组中所有菜单项的底部。

未设置时，不显示菜单页脚。

**类型：** [ResourceStr](../arkts-apis/arkts-arkui-resourcestr-t.md) &#124; [CustomBuilder](arkts-arkui-common-comp-custombuilder-t.md)

**起始版本：** 9

**模型约束：** 此接口可在Stage模型和FA模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## header

```TypeScript
header?: ResourceStr | CustomBuilder
```

设置分组的标题，显示在分组中所有菜单项的顶部。

未设置时，不显示标题。

**类型：** [ResourceStr](../arkts-apis/arkts-arkui-resourcestr-t.md) &#124; [CustomBuilder](arkts-arkui-common-comp-custombuilder-t.md)

**起始版本：** 9

**模型约束：** 此接口可在Stage模型和FA模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
