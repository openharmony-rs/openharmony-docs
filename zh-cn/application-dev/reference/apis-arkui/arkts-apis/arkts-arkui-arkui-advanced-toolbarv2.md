# @ohos.arkui.advanced.ToolBarV2

## 导入模块

```TypeScript
import { ToolBarV2ItemState, ToolBarV2SymbolGlyph, ToolBarV2SymbolGlyphOptions, ToolBarV2ItemText, ToolBarV2ItemTextOptions, ToolBarV2ItemIconType, ToolBarV2ItemImage, ToolBarV2ItemImageOptions, ToolBarV2, ToolBarV2Item, ToolBarV2ItemOptions, ToolBarV2Modifier, ToolBarV2ItemAction } from '@kit.ArkUI';
```

## 汇总

### 类

| 名称 | 说明 |
| --- | --- |
| [ToolBarV2Item](arkts-arkui-arkui-advanced-toolbarv2-toolbarv2item-c.md) | Declare type ToolBarV2Item |
| [ToolBarV2ItemImage](arkts-arkui-arkui-advanced-toolbarv2-toolbarv2itemimage-c.md) | Declare type ToolBarV2ItemImage |
| [ToolBarV2ItemText](arkts-arkui-arkui-advanced-toolbarv2-toolbarv2itemtext-c.md) | Declare type ToolBarV2ItemText |
| [ToolBarV2Modifier](arkts-arkui-arkui-advanced-toolbarv2-toolbarv2modifier-c.md) | Declare ToolBarV2Modifier used in ToolBar |
| [ToolBarV2SymbolGlyph](arkts-arkui-arkui-advanced-toolbarv2-toolbarv2symbolglyph-c.md) | Defines toolBarV2 symbolGlyph. |

### 结构体

| 名称 | 说明 |
| --- | --- |
| [ToolBarV2](arkts-arkui-arkui-advanced-toolbarv2-toolbarv2-s.md) | 工具栏用于展示针对当前界面内容的操作选项，在界面底部显示，适用于需要为用户提供快速操作入口的场景。底部最多显示5个入口，超过则收纳入“更多”子项中，在最右侧显示。适用于需要对当前页面内容进行快捷操作的场景，可帮助用户快速访问常用功能，提升操作效率。该组件基于[状态管理（V2）](../../../ui/state-management/arkts-state-management-overview.md#状态管理v2)实现，相较于[状态管理（V1）](../../../ui/state-management/arkts-state-management-overview.md#状态管理v1)，状态管理（V2）增强了对数据对象的深度观察与管理能力，不再局限于组件层级。借助状态管理（V2），开发者可以通过该组件更灵活地控制工具栏的数据和状态，实现更高效的用户界面刷新。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [ToolBarV2ItemImageOptions](arkts-arkui-arkui-advanced-toolbarv2-toolbarv2itemimageoptions-i.md) | Declare the options of ToolBarV2ItemImage |
| [ToolBarV2ItemOptions](arkts-arkui-arkui-advanced-toolbarv2-toolbarv2itemoptions-i.md) | Declare the options of ToolBarV2Item |
| [ToolBarV2ItemTextOptions](arkts-arkui-arkui-advanced-toolbarv2-toolbarv2itemtextoptions-i.md) | Declare the options of ToolBarV2ItemText |
| [ToolBarV2SymbolGlyphOptions](arkts-arkui-arkui-advanced-toolbarv2-toolbarv2symbolglyphoptions-i.md) | Declare the options of ToolBarV2SymbolGlyph |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [ToolBarV2ItemState](arkts-arkui-arkui-advanced-toolbarv2-toolbarv2itemstate-e.md) | Declare enum ToolBarV2ItemState |

### 类型

| 名称 | 说明 |
| --- | --- |
| [ToolBarV2ItemAction](arkts-arkui-toolbarv2itemaction-t.md) | Defines the action callback of ToolBarV2Item. |
| [ToolBarV2ItemIconType](arkts-arkui-toolbarv2itemicontype-t.md) | Defines the icon type of ToolBarV2 item. |

## 示例

### 示例1（工具栏不同状态的默认效果）

该示例展示了工具栏子项state属性分别设置ENABLE、DISABLE、ACTIVATE状态的不同显示效果。



```TypeScript
import { ToolBarV2ItemImage, ToolBarV2ItemState, ToolBarV2ItemText, ToolBarV2Item, ToolBarV2 } from '@kit.ArkUI';

@Entry
@ComponentV2
struct Index {
  @Local toolbarList: ToolBarV2Item[] = []

  aboutToAppear() {
    this.toolbarList.push(new ToolBarV2Item({
      content: new ToolBarV2ItemText(
        {
          text: '剪贴我是超超超超超超超超超长样式'
        }
      ),
      icon: new ToolBarV2ItemImage({
        src: $r('sys.media.ohos_ic_public_share')
      }),
      action: () => {
      },
    }))
    this.toolbarList.push(
      new ToolBarV2Item({
        content: new ToolBarV2ItemText(
          {
            text: '拷贝'
          }
        ),
        icon: new ToolBarV2ItemImage({
          src: $r('sys.media.ohos_ic_public_copy')
        }),
        action: () => {
        },
        state: ToolBarV2ItemState.DISABLE
      })
    )
    this.toolbarList.push(
      new ToolBarV2Item({
        content: new ToolBarV2ItemText(
          {
            text: '粘贴'
          }
        ),
        icon: new ToolBarV2ItemImage({
          src: $r('sys.media.ohos_ic_public_paste')
        }),
        action: () => {
        },
        state: ToolBarV2ItemState.ACTIVATE
      })
    )
    this.toolbarList.push(
      new ToolBarV2Item({
        content: new ToolBarV2ItemText(
          {
            text: '全选'
          }
        ),
        icon: new ToolBarV2ItemImage({
          src: $r('sys.media.ohos_ic_public_select_all')
        }),
        action: () => {
        },
      })
    )
    this.toolbarList.push(
      new ToolBarV2Item({
        content: new ToolBarV2ItemText(
          {
            text: '分享'
          }
        ),
        icon: new ToolBarV2ItemImage({
          src: $r('sys.media.ohos_ic_public_share')
        }),
        action: () => {
        },
      })
    )
    this.toolbarList.push(
      new ToolBarV2Item({
        content: new ToolBarV2ItemText(
          {
            text: '分享'
          }
        ),
        icon: new ToolBarV2ItemImage({
          src: $r('sys.media.ohos_ic_public_share')
        }),
        action: () => {
        },
      })
    )
  }

  build() {
    Row() {
      Stack() {
        Column() {
          ToolBarV2({
            activatedIndex: 2,
            toolBarList: this.toolbarList,
          })
        }
      }.align(Alignment.Bottom)
      .width('100%').height('100%')
    }
  }
}
```

### 示例2（设置工具栏自定义样式）

该示例通过设置属性ToolBarV2Modifier自定义工具栏高度、背景色、按压效果等样式。



```TypeScript
import {
  SymbolGlyphModifier,
  DividerModifier,
  LengthMetrics,
  ColorMetrics,
  ToolBarV2Item,
  ToolBarV2Modifier,
  ToolBarV2ItemText,
  ToolBarV2ItemImage,
  ToolBarV2,
  ToolBarV2ItemState,
  ToolBarV2SymbolGlyph
} from '@kit.ArkUI';

@Entry
@ComponentV2
struct Index {
  @Local toolbarList: ToolBarV2Item[] = [];
  private toolBarModifier: ToolBarV2Modifier =
    new ToolBarV2Modifier().height(LengthMetrics.vp(52))
      .backgroundColor(ColorMetrics.resourceColor(Color.Transparent))
      .stateEffect(false);
  @Local dividerModifier: DividerModifier = new DividerModifier().height(0);

  aboutToAppear() {
    this.toolbarList.push(
      new ToolBarV2Item({
        content: new ToolBarV2ItemText({
          text: 'Long long long long long long long long text',
          activatedColor: ColorMetrics.resourceColor($r('sys.color.font_primary'))
        }),
        icon: new ToolBarV2SymbolGlyph({
          normal: new SymbolGlyphModifier($r('sys.symbol.ohos_star')).fontColor([Color.Green]),
          activated: new SymbolGlyphModifier($r('sys.symbol.ohos_star')).fontColor([Color.Red]),
        }),
        action: () => {
        },
        state: ToolBarV2ItemState.ACTIVATE,
      })
    )
    this.toolbarList.push(
      new ToolBarV2Item({
        content: new ToolBarV2ItemText({
          text: 'Copy',
          activatedColor: ColorMetrics.resourceColor('#ffec5d5d')
        }),
        icon: new ToolBarV2ItemImage({
          src: $r('sys.media.ohos_ic_public_copy'),
          color: ColorMetrics.resourceColor('#ff18cb53'),
          activatedColor: ColorMetrics.resourceColor('#ffec5d5d'),
        }),
        action: () => {
        },
        state: ToolBarV2ItemState.DISABLE,
      }))
    this.toolbarList.push(
      new ToolBarV2Item({
        content: new ToolBarV2ItemText({
          text: 'Paste',
          color: ColorMetrics.resourceColor('#ff18cb53')
        }),
        icon: new ToolBarV2ItemImage({
          src: $r('sys.media.ohos_ic_public_paste'),
        }),
        action: () => {
        },
        state: ToolBarV2ItemState.ACTIVATE,
      })
    )
    this.toolbarList.push(
      new ToolBarV2Item({
        content: new ToolBarV2ItemText({
          text: 'All',
        }),
        icon: new ToolBarV2ItemImage({
          src: $r('sys.media.ohos_ic_public_select_all'),
        }),
        action: () => {
        },
        state: ToolBarV2ItemState.ACTIVATE,
      }))
    this.toolbarList.push(
      new ToolBarV2Item({
        content: new ToolBarV2ItemText({
          text: '分享',
        }),
        icon: new ToolBarV2ItemImage({
          src: $r('sys.media.ohos_ic_public_share'),
        }),
        action: () => {
        },
      }))
    this.toolbarList.push(
      new ToolBarV2Item({
        content: new ToolBarV2ItemText({
          text: '分享',
        }),
        icon: new ToolBarV2ItemImage({
          src: $r('sys.media.ohos_ic_public_share'),
        }),
        action: () => {
        },
      })
    )
  }

  build() {
    Row() {
      Stack() {
        Column() {
          ToolBarV2({
            toolBarModifier: this.toolBarModifier,
            dividerModifier: this.dividerModifier,
            activatedIndex: 0,
            toolBarList: this.toolbarList,
          })
            .height(52)
        }
      }.align(Alignment.Bottom)
      .width('100%').height('100%')
    }
  }
}
```

### 示例3（设置工具栏自定义播报）

该示例通过设置工具栏子项属性accessibilityText、accessibilityDescription、accessibilityLevel自定义屏幕朗读播报文本。

```TypeScript
import {
  DividerModifier,
  LengthMetrics,
  ColorMetrics,
  ToolBarV2Item,
  ToolBarV2Modifier,
  ToolBarV2ItemText,
  ToolBarV2ItemImage,
  ToolBarV2,
  ToolBarV2ItemState,
} from '@kit.ArkUI';

@Entry
@ComponentV2
struct Index {
  @Local toolbarList: ToolBarV2Item[] = [];
  private toolBarModifier: ToolBarV2Modifier =
    new ToolBarV2Modifier().height(LengthMetrics.vp(52))
      .backgroundColor(ColorMetrics.resourceColor(Color.Transparent))
      .stateEffect(false);
  @Local dividerModifier: DividerModifier = new DividerModifier().height(0);

  aboutToAppear() {
    this.toolbarList.push(
      new ToolBarV2Item({
        content: new ToolBarV2ItemText({
          text: '剪贴我是超超超超超超超超超长样式',
        }),
        icon: new ToolBarV2ItemImage({
          src: $r('sys.media.ohos_ic_public_share')
        }),
        action: () => {
        },
        accessibilityText: '剪贴', // 该项屏幕朗读播报文本为‘剪贴’
        accessibilityDescription: '单指双击即可剪贴', // 该项屏幕朗读播报描述为'单指双击即可剪贴'
        accessibilityLevel: 'yes'  // 该项可被无障碍屏幕朗读聚焦
      })
    )
    this.toolbarList.push(
      new ToolBarV2Item({
        content: new ToolBarV2ItemText({
          text: '拷贝',
        }),
        icon: new ToolBarV2ItemImage({
          src: $r('sys.media.ohos_ic_public_copy'),
        }),
        action: () => {
        },
        state: ToolBarV2ItemState.DISABLE,
        accessibilityLevel: 'no'  // 该项将无法被无障碍屏幕朗读聚焦
      }))
    this.toolbarList.push(
      new ToolBarV2Item({
        content: new ToolBarV2ItemText({
          text: '粘贴',
        }),
        icon: new ToolBarV2ItemImage({
          src: $r('sys.media.ohos_ic_public_paste'),
        }),
        action: () => {
        },
        state: ToolBarV2ItemState.ACTIVATE,
      })
    )
    this.toolbarList.push(
      new ToolBarV2Item({
        content: new ToolBarV2ItemText({
          text: '全选',
        }),
        icon: new ToolBarV2ItemImage({
          src: $r('sys.media.ohos_ic_public_select_all'),
        }),
        action: () => {
        },
      }))
    this.toolbarList.push(
      new ToolBarV2Item({
        content: new ToolBarV2ItemText({
          text: '分享',
        }),
        icon: new ToolBarV2ItemImage({
          src: $r('sys.media.ohos_ic_public_share'),
        }),
        action: () => {
        },
      }))
    this.toolbarList.push(
      new ToolBarV2Item({
        content: new ToolBarV2ItemText({
          text: '分享',
        }),
        icon: new ToolBarV2ItemImage({
          src: $r('sys.media.ohos_ic_public_share'),
        }),
        action: () => {
        },
      })
    )
  }

  build() {
    Row() {
      Stack() {
        Column() {
          ToolBarV2({
            toolBarModifier: this.toolBarModifier,
            dividerModifier: this.dividerModifier,
            activatedIndex: 0,
            toolBarList: this.toolbarList,
          })
            .height(52)
        }
      }.align(Alignment.Bottom)
      .width('100%').height('100%')
    }
  }
}
```
