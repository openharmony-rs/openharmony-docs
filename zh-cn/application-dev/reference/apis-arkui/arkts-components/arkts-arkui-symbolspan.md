# SymbolSpan

SymbolSpan作为Text组件的子组件，用于在文本中显示系统预置的图标小符号（Symbol图标）。支持设置颜色、大小、粗细、渲染策略和动效策略等属性，适用于需要在文本中嵌入图标符号的场景，如状态指示、功能标识等。 SymbolSpan仅支持系统预置的symbol资源，可继承父组件Text的属性设置。
> **说明：** > > - 该组件支持继承父组件Text的属性，即如果子组件未设置属性且父组件设置属性，则继承父组件设置的全部属性。 > > - SymbolSpan拖拽不会置灰显示。

## 子组件

不支持子组件。

## SymbolSpan

```TypeScript
SymbolSpan(value: Resource)
```

定义SymbolSpan组件构造函数。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | Resource | 是 | SymbolSpan组件的资源引用，如 \$r('sys.symbol.ohos_wifi')。仅支持系统预置的symbol资源，引用非symbol资源将显示异常。 |

## 汇总

## 示例

从API version 11开始，该示例通过[renderingStrategy](#renderingstrategy)、[effectStrategy](#effectstrategy)属性展示了不同的渲染和动效策略。

```TypeScript
// xxx.ets
@Entry
@Component
struct Index {
  build() {
    Column() {
      Row() {
        Column() {
          Text('Light')
          Text() {
            SymbolSpan($r('sys.symbol.ohos_trash'))
              .fontWeight(FontWeight.Lighter)
              .fontSize(96)
          }
        }

        Column() {
          Text('Normal')
          Text() {
            SymbolSpan($r('sys.symbol.ohos_trash'))
              .fontWeight(FontWeight.Normal)
              .fontSize(96)
          }
        }

        Column() {
          Text('Bold')
          Text() {
            SymbolSpan($r('sys.symbol.ohos_trash'))
              .fontWeight(FontWeight.Bold)
              .fontSize(96)
          }
        }
      }

      Row() {
        Column() {
          Text('单色')
          Text() {
            SymbolSpan($r('sys.symbol.ohos_folder_badge_plus'))
              .fontSize(96)
              .renderingStrategy(SymbolRenderingStrategy.SINGLE)
              .fontColor([Color.Black, Color.Green, Color.White])
          }
        }

        Column() {
          Text('多色')
          Text() {
            SymbolSpan($r('sys.symbol.ohos_folder_badge_plus'))
              .fontSize(96)
              .renderingStrategy(SymbolRenderingStrategy.MULTIPLE_COLOR)
              .fontColor([Color.Black, Color.Green, Color.White])
          }
        }

        Column() {
          Text('分层')
          Text() {
            SymbolSpan($r('sys.symbol.ohos_folder_badge_plus'))
              .fontSize(96)
              .renderingStrategy(SymbolRenderingStrategy.MULTIPLE_OPACITY)
              .fontColor([Color.Black, Color.Green, Color.White])
          }
        }
      }

      Row() {
        Column() {
          Text('无动效')
          Text() {
            SymbolSpan($r('sys.symbol.ohos_wifi'))
              .fontSize(96)
              .effectStrategy(SymbolEffectStrategy.NONE)
          }
        }

        Column() {
          Text('整体缩放动效')
          Text() {
            SymbolSpan($r('sys.symbol.ohos_wifi'))
              .fontSize(96)
              .effectStrategy(SymbolEffectStrategy.SCALE)
          }
        }

        Column() {
          Text('层级动效')
          Text() {
            SymbolSpan($r('sys.symbol.ohos_wifi'))
              .fontSize(96)
              .effectStrategy(SymbolEffectStrategy.HIERARCHICAL)
          }
        }
      }
    }
  }
}
```

从API version 12开始，该示例通过[attributeModifier](#attributemodifier12)属性创建指定样式图标。

```TypeScript
import { SymbolSpanModifier } from '@kit.ArkUI';

@Entry
@Component
struct Index {
  @State modifier: SymbolSpanModifier =
    new SymbolSpanModifier($r('sys.symbol.ohos_wifi')).fontColor([Color.Blue]).fontSize(100);

  build() {
    Row() {
      Column() {
        Text() {
          SymbolSpan(undefined).attributeModifier(this.modifier)
        }

        Button('更改SymbolSpanModifier')
          .onClick(() => {
            this.modifier = new SymbolSpanModifier($r("sys.symbol.ohos_trash")).fontColor([Color.Red]).fontSize(100);
          })
      }
      .width('100%')
    }
    .height('100%')
  }
}
```

从API版本26.0.0开始，新增[fontWeight](#fontweight-1)属性。

```TypeScript
// xxx.ets
@Entry
@Component
struct Index {
  build() {
    Column() {
      Row() {
        Column() {
          Text('font weight: 220')
          Text() {
            // ohos_trash为系统预置的垃圾桶小符号
            SymbolSpan($r('sys.symbol.ohos_trash'))
              .fontWeight(220, { enableVariableFontWeight: true })
              .fontSize(96)
          }
        }
        Column() {
          Text('            ')
        }
        Column() {
          Text('font weight: 660')
          Text() {
            // ohos_trash为系统预置的垃圾桶小符号
            SymbolSpan($r('sys.symbol.ohos_trash'))
              .fontWeight(660, { enableVariableFontWeight: true })
              .fontSize(96)
          }
        }
      }
      Row() {
        Text('    ')
      }
      Row() {
        Text('After set system text weight: Bold')
      }
      Row() {
        Column() {
          Text('device category: true')
          Text() {
            // ohos_trash为系统预置的垃圾桶小符号
            SymbolSpan($r('sys.symbol.ohos_trash'))
              .fontWeight(FontWeight.Normal, { enableDeviceFontWeightCategory: true })
              .fontSize(96)
          }
        }
        Column() {
          Text('    ')
        }
        Column() {
          Text('device category: false')
          Text() {
            // ohos_trash为系统预置的垃圾桶小符号
            SymbolSpan($r('sys.symbol.ohos_trash'))
              .fontWeight(FontWeight.Normal, { enableDeviceFontWeightCategory: false })
              .fontSize(96)
          }
        }
      }
    }
  }
}
```
