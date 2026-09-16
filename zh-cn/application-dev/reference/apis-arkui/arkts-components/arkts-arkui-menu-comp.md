# Menu

以垂直列表形式显示的菜单。Menu组件支持配置菜单项、子菜单、图标、分隔线等内容，可用于展示操作选项、功能入口等场景。

> **说明：**

> - Menu组件需和 > [bindMenu](arkts-arkui-commonmethod-c.md#bindmenu)或 > [bindContextMenu](arkts-arkui-commonmethod-c.md#bindcontextmenu) > 方法配合使用，不支持作为普通组件单独使用。

## 子组件

包含MenuItem、MenuItemGroup子组件。

## Menu

```TypeScript
Menu()
```

作为菜单的固定容器，无参数。

> **说明：** 
> 
> - 菜单和菜单项宽度计算规则：
> 
> 
> 
> - 布局过程中，期望每个菜单项的宽度一致。若子组件设置了宽度，则以constraintSize为准。
> 
> 
> 
> - Menu不设置宽度的情况：Menu会对子组件MenuItem、MenuItemGroup设置默认2栅格的宽度，若菜单项内容区比2栅格宽，则会自适应撑开。
> 
> 
> 
> - Menu设置宽度的情况：Menu会对子组件MenuItem、MenuItemGroup设置减去padding后的固定宽度。
> 
> 
> 
> - Menu支持设置的最小宽度为64vp。
> 
> - Menu不支持的通用属性：外描边设置下的属性、shadow。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 汇总

### 枚举

| 名称 | 说明 |
| --- | --- |
| [SubMenuExpandingMode](arkts-arkui-submenuexpandingmode-e.md) | Menu子菜单展开样式枚举。 |

## 示例

```TypeScript
### 示例1（设置多级菜单）

该示例通过配置MenuItem中的builder参数实现多级菜单。


```

```TypeScript
### 示例2（设置symbol类型图标）

该示例通过配置symbolStartIcon、symbolEndIcon实现symbol类型图标的菜单。


```

```TypeScript
### 示例3（设置Menu子菜单展开符号）

该示例通过配置subMenuExpandSymbol实现对Menu子菜单展开符号配置颜色和大小。


```

```TypeScript
### 示例4（设置分割线样式）

该示例通过设置menuItemDivider和menuItemGroupDivider属性实现分割线样式。


```

```TypeScript
### 示例5（设置自定义菜单项的多级菜单）

该示例通过设置subMenuBuilder属性为自定义菜单项添加多级菜单。

从API版本26.0.0开始，新增[subMenuBuilder](ts-basic-components-menuitem.md#submenubuilder)属性。
```
