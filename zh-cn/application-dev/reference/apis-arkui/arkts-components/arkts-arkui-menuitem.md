# MenuItem

用来展示菜单中具体的菜单选项。 > **说明：** > - 该组件从API版本26.0.0开始支持[WithTheme]{@link with_theme}。

## 子组件 无

## MenuItem

```TypeScript
MenuItem(value?: MenuItemOptions | CustomBuilder)
```

**起始版本：** 9

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为9。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-MenuItemInterface-(value?: MenuItemOptions | CustomBuilder): MenuItemAttribute--><!--Device-MenuItemInterface-(value?: MenuItemOptions | CustomBuilder): MenuItemAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | \_\_\_MD\_LINK\_USD\_0\_\_\_ \| CustomBuilder | 否 | 包含设置MenuItem的各项信息。需要使用标准菜单项配置（如起始图标、内容、标签等）时选择MenuItemOptions；需要自定义菜单项的显示内容和布局时选择CustomBuilder。如果不传该参数，则创建空的MenuItem对象。  |

## 汇总

