# Menu

以垂直列表形式显示的菜单。

> **说明：**

> - Menu组件需和
> [bindMenu]{@link CommonMethod#bindMenu(content: Array<MenuElement> | CustomBuilder, options?: MenuOptions)}或
> [bindContextMenu]{@link CommonMethod#bindContextMenu(content: CustomBuilder, responseType: ResponseType, options?: ContextMenuOptions)}
> 方法配合使用，不支持作为普通组件单独使用。

## 子组件

包含[MenuItem]{@link menu_item}、[MenuItemGroup]{@link menu_item_group}子组件。

## Menu

```TypeScript
Menu()
```

作为菜单的固定容器，无参数。
> **说明：**  
>  
> - 菜单和菜单项宽度计算规则：  
> >  
> > - 布局过程中，期望每个菜单项的宽度一致。若子组件设置了宽度，则以[constraintSize]{@link CommonMethod#constraintSize}为准。  
> >  
> > - Menu不设置宽度的情况：Menu会对子组件MenuItem、MenuItemGroup设置默认2栅格的宽度，若菜单项内容区比2栅格宽，则会自适应撑开。  
> >  
> > - Menu设置宽度的情况：Menu会对子组件MenuItem、MenuItemGroup设置减去padding后的固定宽度。  
> >  
> > - Menu支持设置的最小宽度为64vp。  
>  
> - Menu不支持的通用属性：[外描边设置]{@link common}下的属性、  
> [shadow]{@link CommonMethod#shadow(value: ShadowOptions | ShadowStyle)}。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-MenuInterface-(): MenuAttribute--><!--Device-MenuInterface-(): MenuAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 汇总

- [SubMenuExpandingMode](arkts-arkui-menu-submenuexpandingmode-e.md)
