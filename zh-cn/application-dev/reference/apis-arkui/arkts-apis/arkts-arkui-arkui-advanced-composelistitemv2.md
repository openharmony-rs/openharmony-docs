# @ohos.arkui.advanced.ComposeListItemV2

## 导入模块

```TypeScript
import { ComposeListItemV2, ContentItemV2, ContentItemV2Options, IconTypeV2, OperateButtonV2, OperateButtonV2Options, OperateCheckV2, OperateCheckV2Options, OperateIconV2, OperateIconV2Options, OperateItemV2, OperateItemV2Options } from '@kit.ArkUI';
```

## 汇总

### 类

| 名称 | 说明 |
| --- | --- |
| [ContentItemV2](arkts-arkui-arkui-advanced-composelistitemv2-contentitemv2-c.md) | 列表左侧显示的图标、图标大小以及中间元素文字内容。 |
| [OperateButtonV2](arkts-arkui-arkui-advanced-composelistitemv2-operatebuttonv2-c.md) | 列表项右侧按钮元素的类型。 |
| [OperateCheckV2](arkts-arkui-arkui-advanced-composelistitemv2-operatecheckv2-c.md) | 列表项右侧元素为Switch、CheckBox、Radio的类型。当列表项右侧元素需要使用Switch、CheckBox、Radio时，可通过该类型配置对应属性。 |
| [OperateIconV2](arkts-arkui-arkui-advanced-composelistitemv2-operateiconv2-c.md) | 列表项右侧图标元素的类型。 |
| [OperateItemV2](arkts-arkui-arkui-advanced-composelistitemv2-operateitemv2-c.md) | 列表项右侧显示的元素类型。 |

### 结构体

| 名称 | 说明 |
| --- | --- |
| [ComposeListItemV2](arkts-arkui-arkui-advanced-composelistitemv2-composelistitemv2-s.md) | 该组件用于展示一系列宽度相同的列表项，适用于展示连续、多行的同类数据组合（如图片与文本）。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [ContentItemV2Options](arkts-arkui-arkui-advanced-composelistitemv2-contentitemv2options-i.md) | ContentItemV2构造函数的参数选项。 |
| [OperateButtonV2Options](arkts-arkui-arkui-advanced-composelistitemv2-operatebuttonv2options-i.md) | OperateButtonV2构造函数的参数选项。 |
| [OperateCheckV2Options](arkts-arkui-arkui-advanced-composelistitemv2-operatecheckv2options-i.md) | OperateCheckV2构造函数的参数选项。 |
| [OperateIconV2Options](arkts-arkui-arkui-advanced-composelistitemv2-operateiconv2options-i.md) | OperateIconV2构造函数的参数选项。 |
| [OperateItemV2Options](arkts-arkui-arkui-advanced-composelistitemv2-operateitemv2options-i.md) | OperateItemV2构造函数的参数选项。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [IconTypeV2](arkts-arkui-arkui-advanced-composelistitemv2-icontypev2-e.md) | 列表左侧图标类型。 |

### 类型

| 名称 | 说明 |
| --- | --- |
| [OnActionCallback](arkts-arkui-onactioncallback-t.md) | 列表项右侧元素为图标/箭头，通过点击触发回调函数的类型。 |
| [OnChangeCallback](arkts-arkui-onchangecallback-t.md) | 列表项右侧元素为Switch/CheckBox/Radio时，当状态发生改变时的回调函数对应的类型。 |

## 示例

### 示例1(设置简单列表项)

从API版本26.0.0开始，通过组件ComposeListItemV2接口实现带有主标题、副标题、描述、右侧按钮及文本的简单列表项。



```TypeScript
// 该示例主要演示该组件的基础功能使用，包含左侧右侧元素的情况
import { IconTypeV2, ComposeListItemV2, ContentItemV2, OperateItemV2, OperateIconV2 } from '@kit.ArkUI';

@Entry
@ComponentV2
struct ComposeListItemV2Example {
  build(): void {
    Column() {
      List() {
        ListItem() {
          ComposeListItemV2({
            contentItemV2: new ContentItemV2({
              iconStyle: IconTypeV2.NORMAL_ICON,
              icon: $r('sys.media.ohos_app_icon'),
              primaryText: '双行列表',
              secondaryText: '辅助文字',
              description: '描述内容文字'
            }),
            operateItemV2: new OperateItemV2({
              icon: new OperateIconV2({
                value: $r('sys.media.ohos_app_icon'),
                action: () => {
                  this.getUIContext().getPromptAction().showToast({
                    message: 'icon'
                  });
                }
              }),
              text: '右侧文本'
            })
          })
        }
      }
    }
  }
}
```

### 示例2(设置列表项右侧不同元素自定义播报)

从API版本26.0.0开始，通过设置属性接口accessibilityText、accessibilityDescription、accessibilityLevel，实现列表项右侧图标、按钮、单选框自定义屏幕朗读播报文本。



```TypeScript
import {
  IconTypeV2,
  ComposeListItemV2,
  ContentItemV2,
  OperateItemV2,
  OperateCheckV2,
  OperateButtonV2,
  OperateIconV2
} from '@kit.ArkUI';

@Entry
@ComponentV2
struct ComposeListItemV2Example {
  build(): void {
    Column() {
      List() {
        ListItem() {
          ComposeListItemV2({
            contentItemV2: new ContentItemV2({
              iconStyle: IconTypeV2.NORMAL_ICON,
              icon: $r('sys.media.ohos_app_icon'),
              primaryText: '双行列表',
              secondaryText: '辅助文字',
              description: '描述内容文字'
            }),
            operateItemV2: new OperateItemV2({
              radio: new OperateCheckV2({
                accessibilityText: '单选框', // 该单选框屏幕朗读播报文本为'单选框'
                accessibilityDescription: '未选中', // 该单选框屏幕朗读播报描述为'未选中'
                accessibilityLevel: 'yes'  // 该项可被无障碍屏幕朗读聚焦
              })
            })
          })
        }

        ListItem() {
          ComposeListItemV2({
            contentItemV2: new ContentItemV2({
              iconStyle: IconTypeV2.NORMAL_ICON,
              icon: $r('sys.media.ohos_app_icon'),
              primaryText: '双行列表',
              secondaryText: '辅助文字',
              description: '描述内容文字'
            }),
            operateItemV2: new OperateItemV2({
              button: new OperateButtonV2({
                text: '确定',
                accessibilityText: '这是一个按钮',
                accessibilityDescription: '单指双击即可执行',
                accessibilityLevel: 'no'  // 该按钮不可被屏幕朗读服务识别
              })
            })
          })
        }

        ListItem() {
          ComposeListItemV2({
            contentItemV2: new ContentItemV2({
              iconStyle: IconTypeV2.NORMAL_ICON,
              icon: $r('sys.media.ohos_app_icon'),
              primaryText: '双行列表',
              secondaryText: '辅助文字',
              description: '描述内容文字'
            }),
            operateItemV2: new OperateItemV2({
              icon: new OperateIconV2({
                value: $r('sys.media.ohos_app_icon'),
                action: () => {
                  this.getUIContext().getPromptAction().showToast({
                    message: 'icon'
                  });
                },
                accessibilityText: '这是一个icon', // 该icon屏幕朗读播报文本为'这是一个icon'
                accessibilityDescription: '单指双击即可弹出', // 该icon屏幕朗读播报描述为'单指双击即可弹出'
                accessibilityLevel: 'yes'  // 该项可被无障碍屏幕朗读聚焦
              })
            })
          })
        }
      }
    }
  }
}
```

### 示例3(设置Symbol类型图标)

从API版本26.0.0开始，通过设置ContentItemV2、OperateItemV2、OperateIconV2的属性接口symbolStyle，实现Symbol类型图标参数设置。

```TypeScript
import {
  IconTypeV2,
  ComposeListItemV2,
  ContentItemV2,
  OperateItemV2,
  OperateIconV2,
  SymbolGlyphModifier
} from '@kit.ArkUI';

@Entry
@ComponentV2
struct ComposeListItemV2Example {
  build(): void {
    Column() {
      List() {
        ListItem() {
          ComposeListItemV2({
            contentItemV2: new ContentItemV2({
              iconStyle: IconTypeV2.NORMAL_ICON,
              icon: $r('sys.symbol.house'),
              primaryText: '双行列表',
              secondaryText: '辅助文字',
              description: '描述内容文字'
            }),
            operateItemV2: new OperateItemV2({
              image: $r('sys.symbol.car'),
            })
          })
        }

        ListItem() {
          ComposeListItemV2({
            contentItemV2: new ContentItemV2({
              iconStyle: IconTypeV2.NORMAL_ICON,
              icon: $r('sys.symbol.house'),
              symbolStyle: new SymbolGlyphModifier($r('sys.symbol.bell')).fontColor([Color.Red]),
              primaryText: '双行列表',
              secondaryText: '辅助文字',
              description: '描述内容文字'
            }),
            operateItemV2: new OperateItemV2({
              image: $r('sys.symbol.car'),
              symbolStyle: new SymbolGlyphModifier($r('sys.symbol.heart')).fontColor([Color.Pink]),
            })
          })
        }

        ListItem() {
          ComposeListItemV2({
            contentItemV2: new ContentItemV2({
              iconStyle: IconTypeV2.NORMAL_ICON,
              icon: $r('sys.symbol.house'),
              symbolStyle: new SymbolGlyphModifier($r('sys.symbol.bell')).fontColor([Color.Blue]),
              primaryText: '双行列表',
              secondaryText: '辅助文字',
              description: '描述内容文字'
            }),
            operateItemV2: new OperateItemV2({
              icon: new OperateIconV2({
                value: $r('sys.symbol.car'),
                symbolStyle: new SymbolGlyphModifier($r('sys.symbol.heart')).fontColor([Color.Orange]),
                action: () => {
                  this.getUIContext().getPromptAction().showToast({
                    message: 'icon'
                  });
                }
              })
            })
          })
        }
      }
    }
  }
}
```
