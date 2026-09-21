# @ohos.arkui.advanced.ComposeListItem

## 子组件

无

## 事件

不支持[通用事件](../arkts-components/arkts-arkui-common-comp.md#common)。

## 导入模块

```TypeScript
import { ComposeListItem, ContentItem, IconType, OperateButton, OperateCheck, OperateIcon, OperateItem } from '@kit.ArkUI';
```

## 汇总

### 类

| 名称 | 说明 |
| --- | --- |
| [ContentItem](arkts-arkui-arkui-advanced-composelistitem-contentitem-c.md) | 列表左侧显示的图标、图标大小以及中间元素文字内容。 |
| [OperateButton](arkts-arkui-arkui-advanced-composelistitem-operatebutton-c.md) | 列表右侧按钮元素的类型。 |
| [OperateCheck](arkts-arkui-arkui-advanced-composelistitem-operatecheck-c.md) | 列表右侧元素为Switch、CheckBox、Radio的类型。 |
| [OperateIcon](arkts-arkui-arkui-advanced-composelistitem-operateicon-c.md) | 列表右侧图标元素的类型。 |
| [OperateItem](arkts-arkui-arkui-advanced-composelistitem-operateitem-c.md) | 列表右侧显示的元素类型。 |

### 结构体

| 名称 | 说明 |
| --- | --- |
| [ComposeListItem](arkts-arkui-arkui-advanced-composelistitem-composelistitem-s.md) | 该组件用于展示一系列宽度相同的列表项，适用于展示连续、多行的同类数据组合（如图片与文本）。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [IconType](arkts-arkui-arkui-advanced-composelistitem-icontype-e.md) | 列表左侧图标类型。 |

## 示例

### 示例1（设置简单列表项）

该示例实现了带有主标题、副标题、描述、右侧图标及文本的简单列表项。



```TypeScript
// 该示例主要演示该组件的基础功能使用，包含左侧右侧元素的情况
import { IconType, ComposeListItem } from '@kit.ArkUI';

@Entry
@Component
struct ComposeListItemExample {
  build() {
    Column() {
      List() {
        ListItem() {
          ComposeListItem({
            contentItem: ({
              iconStyle: IconType.NORMAL_ICON,
              icon: $r('sys.media.ohos_app_icon'),
              primaryText: '双行列表',
              secondaryText: '辅助文字',
              description: '描述内容文字'
            }),
            operateItem: ({
              icon: {
                value: $r('sys.media.ohos_app_icon'),
                action: () => {
                  this.getUIContext().getPromptAction().showToast({
                    message: 'icon'
                  });
                } },
              text: '右侧文本'
            })
          })
        }
      }
    }
  }
}
```

### 示例2（设置右侧不同元素自定义播报）

从API version 18开始，该示例通过设置属性accessibilityText、accessibilityDescription、accessibilityLevel，实现右侧图标、按钮、单选框自定义屏幕朗读播报文本。



```TypeScript
import { IconType, ComposeListItem } from '@kit.ArkUI';
@Entry
@Component
struct ComposeListItemExample {
  build() {
    Column() {
      List() {
        ListItem() {
          ComposeListItem({
            contentItem: ({
              iconStyle: IconType.NORMAL_ICON,
              icon: $r('sys.media.ohos_app_icon'),
              primaryText: '双行列表',
              secondaryText: '辅助文字',
              description: '描述内容文字'
            }),
            operateItem: ({
              radio: {
                accessibilityText: '单选框', // 该单选框屏幕朗读播报文本为‘单选框’
                accessibilityDescription: '未选中', // 该单选框屏幕朗读播报描述为'未选中'
                accessibilityLevel: 'yes'  // 该项可被无障碍屏幕朗读聚焦
              }
            })
          })
        }

        ListItem() {
          ComposeListItem({
            contentItem: ({
              iconStyle: IconType.NORMAL_ICON,
              icon: $r('sys.media.ohos_app_icon'),
              primaryText: '双行列表',
              secondaryText: '辅助文字',
              description: '描述内容文字'
            }),
            operateItem: ({
              button: {
                text: '确定',
                accessibilityText: '这是一个按钮',
                accessibilityDescription: '单指双击即可执行',
                accessibilityLevel: 'no'  // 该按钮不可被屏幕朗读服务识别
              }
            })
          })
        }

        ListItem() {
          ComposeListItem({
            contentItem: ({
              iconStyle: IconType.NORMAL_ICON,
              icon: $r('sys.media.ohos_app_icon'),
              primaryText: '双行列表',
              secondaryText: '辅助文字',
              description: '描述内容文字'
            }),
            operateItem: ({
              icon: {
                value: $r('sys.media.ohos_app_icon'),
                action: () => {
                  this.getUIContext().getPromptAction().showToast({
                    message: 'icon'
                  });
                },
                accessibilityText: '这是一个icon', // 该icon屏幕朗读播报文本为‘这是一个icon’
                accessibilityDescription: '单指双击即可弹出', // 该icon屏幕朗读播报描述为'单指双击即可弹出'
                accessibilityLevel: 'yes'  // 该项可被无障碍屏幕朗读聚焦
              }
            })
          })
        }
      }
    }
  }
}
```

### 示例3（设置Symbol类型图标）

从API version 18开始，该示例通过设置ContentItem、OperateItem、OperateIcon的属性symbolStyle，展示了自定义Symbol类型图标。

```TypeScript
import { IconType, ComposeListItem, SymbolGlyphModifier } from '@kit.ArkUI';
@Entry
@Component
struct ComposeListItemExample {
  build() {
    Column() {
      List() {
        ListItem() {
          ComposeListItem({
            contentItem: ({
              iconStyle: IconType.NORMAL_ICON,
              icon: $r('sys.symbol.house'),
              primaryText: '双行列表',
              secondaryText: '辅助文字',
              description: '描述内容文字'
            }),
            operateItem: ({
              image: $r('sys.symbol.car'),
            })
          })
        }

        ListItem() {
          ComposeListItem({
            contentItem: ({
              iconStyle: IconType.NORMAL_ICON,
              icon: $r('sys.symbol.house'),
              symbolStyle: new SymbolGlyphModifier($r('sys.symbol.bell')).fontColor([Color.Red]),
              primaryText: '双行列表',
              secondaryText: '辅助文字',
              description: '描述内容文字'
            }),
            operateItem: ({
              image: $r('sys.symbol.car'),
              symbolStyle: new SymbolGlyphModifier($r('sys.symbol.heart')).fontColor([Color.Pink]),
            })
          })
        }

        ListItem() {
          ComposeListItem({
            contentItem: ({
              iconStyle: IconType.NORMAL_ICON,
              icon: $r('sys.symbol.house'),
              symbolStyle: new SymbolGlyphModifier($r('sys.symbol.bell')).fontColor([Color.Blue]),
              primaryText: '双行列表',
              secondaryText: '辅助文字',
              description: '描述内容文字'
            }),
            operateItem: ({
              icon: {
                value: $r('sys.symbol.car'),
                symbolStyle: new SymbolGlyphModifier($r('sys.symbol.heart')).fontColor([Color.Orange]),
                action: () => {
                  this.getUIContext().getPromptAction().showToast({
                    message: 'icon'
                  });
                }
              }
            })
          })
        }
      }
    }
  }
}
```
