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
> - Menu不支持的通用属性：外描边设置下的属性、
> shadow。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 汇总

### 枚举

| 名称 | 说明 |
| --- | --- |
| [SubMenuExpandingMode](arkts-arkui-submenuexpandingmode-e.md) | Menu子菜单展开样式枚举。 |

## 示例

该示例通过配置MenuItem中的builder参数实现多级菜单。

```TypeScript
@Entry
@Component
struct Index {
  // $r('app.media.xxx')需要替换为开发者所需的图像资源文件。
  private iconStr: ResourceStr = $r('app.media.view_list_filled');
  private iconStr2: ResourceStr = $r('app.media.arrow_right_filled');

  @Builder
  SubMenu() {
    Menu() {
      MenuItem({ content: '复制', labelInfo: 'Ctrl+C' })
      MenuItem({ content: '粘贴', labelInfo: 'Ctrl+V' })
    }
  }

  @Builder
  MyMenu() {
    Menu() {
      MenuItem({ startIcon: $r('app.media.icon'), content: '菜单选项' })
      MenuItem({ startIcon: $r('app.media.icon'), content: '菜单选项' })
        .enabled(false)
      MenuItem({
        startIcon: this.iconStr,
        content: '菜单选项',
        endIcon: this.iconStr2,
        builder: (): void => this.SubMenu()
      })
      MenuItemGroup({ header: '小标题' }) {
        MenuItem({
          startIcon: this.iconStr,
          content: '菜单选项',
          endIcon: this.iconStr2,
          builder: (): void => this.SubMenu()
        })
        MenuItem({
          startIcon: $r('app.media.app_icon'),
          content: '菜单选项',
          endIcon: this.iconStr2,
          builder: (): void => this.SubMenu()
        })
      }
      MenuItem({
        startIcon: this.iconStr,
        content: '菜单选项',
      })
    }
  }

  build() {
    Row() {
      Column() {
        Text('click to show menu')
          .fontSize(50)
          .fontWeight(FontWeight.Bold)
      }
      .bindMenu(this.MyMenu)
      .width('100%')
    }
    .height('100%')
  }
}
```

该示例通过配置symbolStartIcon、symbolEndIcon实现symbol类型图标的菜单。

```TypeScript
// xxx.ets
import { SymbolGlyphModifier } from '@kit.ArkUI';

@Entry
@Component
struct Index {
  @State startIconModifier: SymbolGlyphModifier = new SymbolGlyphModifier($r('sys.symbol.ohos_mic')).fontSize('24vp');
  @State endIconModifier: SymbolGlyphModifier = new SymbolGlyphModifier($r('sys.symbol.ohos_trash')).fontSize('24vp');
  @State selectIconModifier: SymbolGlyphModifier =
    new SymbolGlyphModifier($r('sys.symbol.checkmark')).fontSize('24vp');
  @State select: boolean = true;

  @Builder
  SubMenu() {
    Menu() {
      MenuItem({ content: '复制', labelInfo: 'Ctrl+C' })
      MenuItem({ content: '粘贴', labelInfo: 'Ctrl+V' })
    }
  }

  @Builder
  MyMenu() {
    Menu() {
      MenuItem({ symbolStartIcon: this.startIconModifier, content: '菜单选项' })
      MenuItem({ symbolStartIcon: this.startIconModifier, content: '菜单选项' })
        .enabled(false)
      MenuItem({
        symbolStartIcon: this.startIconModifier,
        content: '菜单选项',
        symbolEndIcon: this.endIconModifier,
        builder: (): void => this.SubMenu()
      })
      MenuItemGroup({ header: '小标题' }) {
        MenuItem({
          symbolStartIcon: this.startIconModifier,
          content: '菜单选项',
          symbolEndIcon: this.endIconModifier,
          builder: (): void => this.SubMenu()
        })
        MenuItem({
          symbolStartIcon: this.startIconModifier,
          content: '菜单选项',
          symbolEndIcon: this.endIconModifier,
          builder: (): void => this.SubMenu()
        })
      }
      MenuItem({
        content: '菜单选项',
      }).selected(this.select).selectIcon(this.selectIconModifier)
    }
  }

  build() {
    Row() {
      Column() {
        Text('click to show menu')
          .fontSize(50)
          .fontWeight(FontWeight.Bold)
      }
      .bindMenu(this.MyMenu)
      .width('100%')
    }
    .height('100%')
  }
}
```

该示例通过配置subMenuExpandSymbol实现对Menu子菜单展开符号配置颜色和大小。

```TypeScript
import { SymbolGlyphModifier } from '@kit.ArkUI';

@Entry
@Component
struct Index {
  @State startIconModifier: SymbolGlyphModifier = new SymbolGlyphModifier($r('sys.symbol.ohos_star'))
  @State endIconModifier: SymbolGlyphModifier = new SymbolGlyphModifier($r('sys.symbol.ohos_mic'))
  @State expandSymbolModifier: SymbolGlyphModifier =
    new SymbolGlyphModifier($r('sys.symbol.chevron_down')).fontColor([Color.Red]).fontSize('24vp')

  @Builder
  SubMenu() {
    Menu() {
      MenuItem({
        symbolStartIcon: this.startIconModifier,
        content: '图标'
      })
      MenuItem({
        symbolStartIcon: this.startIconModifier,
        content: '列表'
      })
    }.backgroundColor(Color.Grey)
  }

  @Builder
  MyMenu() {
    Menu() {
      MenuItem({
        symbolStartIcon: this.startIconModifier,
        symbolEndIcon: this.endIconModifier,
        content: '新建文件夹',
        builder: (): void => this.SubMenu(),
      })
      MenuItem({
        symbolStartIcon: this.startIconModifier,
        content: '排序方式',
        builder: (): void => this.SubMenu(),
      })
      MenuItem({
        symbolStartIcon: this.startIconModifier,
        content: '查看方式',
        builder: (): void => this.SubMenu(),
      })
    }
    // 设置子菜单展开样式为嵌入式展开
    .subMenuExpandingMode(SubMenuExpandingMode.EMBEDDED_EXPAND)
    .backgroundColor(Color.Grey)
    // 设置子菜单展开符号
    .subMenuExpandSymbol(this.expandSymbolModifier)
  }

  build() {
    Button('click to show menu')
      .position({ top: 40, left: 40 })
      .bindMenu(this.MyMenu)
  }
}
```

该示例通过设置menuItemDivider和menuItemGroupDivider属性实现分割线样式。

```TypeScript
import { LengthMetrics } from '@kit.ArkUI'

@Entry
@Component
struct Index {

  @Builder
  MyMenu() {
    Menu() {
      MenuItem({ content: 'Item Content' })
      MenuItem({ content: 'Item Content' })
      MenuItem({ content: 'Item Content' })
      MenuItemGroup() {
        MenuItem({ content: 'Group Child' })
        MenuItem({ content: 'Group Child' })
      }
      MenuItem({ content: 'Item Content' })
    }
    // 设置菜单项分割线样式
    .menuItemDivider({
      strokeWidth: LengthMetrics.vp(5),
      color: '#d5d5d5',
      mode: DividerMode.EMBEDDED_IN_MENU
    })
    // 设置菜单项分组分割线样式
    .menuItemGroupDivider({
      strokeWidth: LengthMetrics.vp(5),
      color: '#707070',
      mode: DividerMode.EMBEDDED_IN_MENU
    })
  }

  build() {
    RelativeContainer() {
      Button('show menu')
        .bindMenu(this.MyMenu)
    }
    .height('100%')
    .width('100%')
  }
}
```

从API版本26.0.0开始，新增subMenuBuilder属性。

```TypeScript
import { LengthMetrics } from '@kit.ArkUI';

@Entry
@Component
struct Index {

  @Builder
  SubMenu() {
    Menu() {
      MenuItem({ content: '复制', labelInfo: 'Ctrl+C' })
      MenuItem({ content: '粘贴', labelInfo: 'Ctrl+V' })
    }
  }

  @Builder
  SubMenuContent() {
    Row() {
      // $r('app.media.startIcon')需要替换为开发者所需的图像资源文件。
      Image($r('app.media.startIcon')).width(20).height(20)
      Text('Custom Menu Item').margin({start: LengthMetrics.vp(5)})
    }.padding(20)
  }

  @Builder
  MyMenu() {
    Menu() {
      MenuItem(this.SubMenuContent)
      MenuItem(this.SubMenuContent)
        .enabled(false)
      MenuItem(this.SubMenuContent).subMenuBuilder(this.SubMenu)
    }
  }

  build() {
    Row() {
      Column() {
        Text('click to show menu')
          .fontSize(50)
          .fontWeight(FontWeight.Bold)
      }
      .bindMenu(this.MyMenu)
      .width('100%')
    }
    .height('100%')
  }
}
```
