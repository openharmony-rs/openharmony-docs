# AlphabetIndexer

可以与容器组件联动，用于按逻辑结构快速定位容器显示区域，适用于通讯录、城市列表、分类列表等需要快速定位内容的场景。
> **说明：** > > > 从API version 12开始，触控反馈默认开启；使用前请按[enableHapticFeedback](arkts-arkui-alphabetindexer-attribute.md#enablehapticfeedback)的说明配置振动权限。

## 子组件

无

## AlphabetIndexer

```TypeScript
AlphabetIndexer(options: AlphabetIndexerOptions)
```

创建索引条组件。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [AlphabetIndexerOptions](arkts-arkui-alphabetindexeroptions-i.md) | 是 | 设置索引条组件参数。 |

## 汇总

### 接口

| 名称 | 说明 |
| --- | --- |
| [AlphabetIndexerOptions](arkts-arkui-alphabetindexeroptions-i.md) | 用于设置索引条参数。 |

### 类型

| 名称 | 说明 |
| --- | --- |
| [OnAlphabetIndexerPopupSelectCallback](arkts-arkui-onalphabetindexerpopupselectcallback-t.md) | 提示弹窗二级索引项被选中时触发的事件。 |
| [OnAlphabetIndexerRequestPopupDataCallback](arkts-arkui-onalphabetindexerrequestpopupdatacallback-t.md) | [usingPopup](arkts-arkui-alphabetindexer-attribute.md#usingpopup)设置值为true，索引项被选中时触发的事件。 |
| [OnAlphabetIndexerSelectCallback](arkts-arkui-onalphabetindexerselectcallback-t.md) | 索引项被选中时触发的事件。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [IndexerAlign](arkts-arkui-indexeralign-e.md) | 索引条提示弹窗的对齐样式枚举。 |

## 示例

通过[onRequestPopupData](arkts-arkui-alphabetindexer-attribute.md#onrequestpopupdata)事件自定义提示弹窗显示文本内容。

```TypeScript
// xxx.ets
@Entry
@Component
struct AlphabetIndexerSample {
  private arrayA: string[] = ['安'];
  private arrayB: string[] = ['卜', '白', '包', '毕', '丙'];
  private arrayC: string[] = ['曹', '成', '陈', '催'];
  private arrayL: string[] = ['刘', '李', '楼', '梁', '雷', '吕', '柳', '卢'];
  private value: string[] = ['#', 'A', 'B', 'C', 'D', 'E', 'F', 'G',
    'H', 'I', 'J', 'K', 'L', 'M', 'N',
    'O', 'P', 'Q', 'R', 'S', 'T', 'U',
    'V', 'W', 'X', 'Y', 'Z'];

  build() {
    Stack({ alignContent: Alignment.Start }) {
      Row() {
        List({ space: 20, initialIndex: 0 }) {
          ForEach(this.arrayA, (item: string) => {
            ListItem() {
              Text(item)
                .width('80%')
                .height('5%')
                .fontSize(30)
                .textAlign(TextAlign.Center)
            }
          }, (item: string) => item)

          ForEach(this.arrayB, (item: string) => {
            ListItem() {
              Text(item)
                .width('80%')
                .height('5%')
                .fontSize(30)
                .textAlign(TextAlign.Center)
            }
          }, (item: string) => item)

          ForEach(this.arrayC, (item: string) => {
            ListItem() {
              Text(item)
                .width('80%')
                .height('5%')
                .fontSize(30)
                .textAlign(TextAlign.Center)
            }
          }, (item: string) => item)

          ForEach(this.arrayL, (item: string) => {
            ListItem() {
              Text(item)
                .width('80%')
                .height('5%')
                .fontSize(30)
                .textAlign(TextAlign.Center)
            }
          }, (item: string) => item)
        }
        .width('50%')
        .height('100%')

        AlphabetIndexer({ arrayValue: this.value, selected: 0 })
          .autoCollapse(false) // 关闭自适应折叠模式
          .enableHapticFeedback(false) // 关闭触控反馈
          .selectedColor(0xFFFFFF) // 选中项文本颜色
          .popupColor(0xFFFAF0) // 提示弹窗一级索引文本颜色
          .selectedBackgroundColor(0xCCCCCC) // 选中项背景颜色
          .popupBackground(0xD2B48C) // 提示弹窗背景颜色
          .usingPopup(true) // 索引项被选中时显示提示弹窗
          .selectedFont({ size: 16, weight: FontWeight.Bolder }) // 选中项文本样式
          .popupFont({ size: 30, weight: FontWeight.Bolder }) // 提示弹窗一级索引的文本样式
          .itemSize(28) // 索引项的尺寸大小
          .alignStyle(IndexerAlign.Left) // 提示弹窗在索引条右侧弹出
          .popupItemBorderRadius(24) // 设置提示弹窗索引项背板圆角半径
          .itemBorderRadius(14) // 设置索引项背板圆角半径
          .popupBackgroundBlurStyle(BlurStyle.NONE) // 设置提示弹窗的背景模糊材质
          .popupTitleBackground(0xCCCCCC) // 设置提示弹窗一级索引项背景颜色
          .popupSelectedColor(0x00FF00) // 提示弹窗二级索引选中项文本颜色
          .popupUnselectedColor(0x0000FF) // 提示弹窗二级索引未选中项文本颜色
          .popupItemFont({ size: 30, style: FontStyle.Normal }) // 提示弹窗二级索引项文本样式
          .popupItemBackgroundColor(0xCCCCCC) // 提示弹窗二级索引项背景颜色
          .onSelect((index: number) => {
            console.info(this.value[index] + ' Selected!');
          })
          .onRequestPopupData((index: number) => {
            // 当选中A时，提示弹窗里面的二级索引文本列表显示A对应的列表arrayA，选中B、C、L时也同样
            // 选中其余索引项时，提示弹窗二级索引文本列表为空，提示弹窗会只显示一级索引项
            if (this.value[index] == 'A') {
              return this.arrayA;
            } else if (this.value[index] == 'B') {
              return this.arrayB;
            } else if (this.value[index] == 'C') {
              return this.arrayC;
            } else if (this.value[index] == 'L') {
              return this.arrayL;
            } else {
              return [];
            }
          })
          .onPopupSelect((index: number) => {
            console.info('onPopupSelected:' + index);
          })
      }
      .width('100%')
      .height('100%')
    }
  }
}
```

通过[autoCollapse](#autocollapse11)属性开启自适应折叠模式。

```TypeScript
// xxx.ets
@Entry
@Component
struct AlphabetIndexerSample {
  private arrayA: string[] = ['安'];
  private arrayB: string[] = ['卜', '白', '包', '毕', '丙'];
  private arrayC: string[] = ['曹', '成', '陈', '催'];
  private arrayJ: string[] = ['嘉', '贾'];
  private value: string[] = ['#', 'A', 'B', 'C', 'D', 'E', 'F', 'G',
    'H', 'I', 'J', 'K', 'L', 'M', 'N',
    'O', 'P', 'Q', 'R', 'S', 'T', 'U',
    'V', 'W', 'X', 'Y', 'Z'];
  @State isNeedAutoCollapse: boolean = false;
  @State indexerHeight: string = '75%';

  build() {
    Stack({ alignContent: Alignment.Start }) {
      Row() {
        List({ space: 20, initialIndex: 0 }) {
          ForEach(this.arrayA, (item: string) => {
            ListItem() {
              Text(item)
                .width('80%')
                .height('5%')
                .fontSize(30)
                .textAlign(TextAlign.Center)
            }
          }, (item: string) => item)

          ForEach(this.arrayB, (item: string) => {
            ListItem() {
              Text(item)
                .width('80%')
                .height('5%')
                .fontSize(30)
                .textAlign(TextAlign.Center)
            }
          }, (item: string) => item)

          ForEach(this.arrayC, (item: string) => {
            ListItem() {
              Text(item)
                .width('80%')
                .height('5%')
                .fontSize(30)
                .textAlign(TextAlign.Center)
            }
          }, (item: string) => item)

          ForEach(this.arrayJ, (item: string) => {
            ListItem() {
              Text(item)
                .width('80%')
                .height('5%')
                .fontSize(30)
                .textAlign(TextAlign.Center)
            }
          }, (item: string) => item)
        }
        .width('50%')
        .height('100%')

        Column() {
          Column() {
            AlphabetIndexer({ arrayValue: this.value, selected: 0 })
              .autoCollapse(this.isNeedAutoCollapse) // 开启或关闭自适应折叠模式
              .height(this.indexerHeight) // 索引条高度
              .enableHapticFeedback(false) // 关闭触控反馈
              .selectedColor(0xFFFFFF) // 选中项文本颜色
              .popupColor(0xFFFAF0) // 提示弹窗一级索引文本颜色
              .selectedBackgroundColor(0xCCCCCC) // 选中项背景颜色
              .popupBackground(0xD2B48C) // 提示弹窗背景颜色
              .usingPopup(true) // 索引项被选中时显示提示弹窗
              .selectedFont({ size: 16, weight: FontWeight.Bolder }) // 选中项文本样式
              .popupFont({ size: 30, weight: FontWeight.Bolder }) // 提示弹窗一级索引的文本样式
              .itemSize(28) // 每一项的尺寸大小
              .alignStyle(IndexerAlign.Right) // 提示弹窗在索引条左侧弹出
              .popupTitleBackground(0xD2B48C) // 设置提示弹窗一级索引项背景颜色
              .popupSelectedColor(0x00FF00) // 提示弹窗二级索引选中项文本颜色
              .popupUnselectedColor(0x0000FF) // 提示弹窗二级索引未选中项文本颜色
              .popupItemFont({ size: 30, style: FontStyle.Normal }) // 提示弹窗二级索引项文本样式
              .popupItemBackgroundColor(0xCCCCCC) // 提示弹窗二级索引项背景颜色
              .onSelect((index: number) => {
                console.info(this.value[index] + ' Selected!');
              })
              .onRequestPopupData((index: number) => {
                // 当选中A时，提示弹窗里面的二级索引文本列表显示A对应的列表arrayA，选中B、C、J时也同样
                // 选中其余索引项时，提示弹窗二级索引文本列表为空，提示弹窗会只显示一级索引项
                if (this.value[index] == 'A') {
                  return this.arrayA;
                } else if (this.value[index] == 'B') {
                  return this.arrayB;
                } else if (this.value[index] == 'C') {
                  return this.arrayC;
                } else if (this.value[index] == 'J') {
                  return this.arrayJ;
                } else {
                  return [];
                }
              })
              .onPopupSelect((index: number) => {
                console.info('onPopupSelected:' + index);
              })
          }
          .height('80%')
          .justifyContent(FlexAlign.Center)

          Column() {
            Button('切换成折叠模式')
              .margin('5vp')
              .onClick(() => {
                this.isNeedAutoCollapse = true;
              })
            Button('切换索引条高度到30%')
              .margin('5vp')
              .onClick(() => {
                this.indexerHeight = '30%';
              })
            Button('切换索引条高度到70%')
              .margin('5vp')
              .onClick(() => {
                this.indexerHeight = '70%';
              })
          }.height('20%')
        }
        .width('50%')
        .justifyContent(FlexAlign.Center)
      }
      .width('100%')
      .height(720)
    }
  }
}
```

通过[popupBackgroundBlurStyle](#popupbackgroundblurstyle12)属性实现提示弹窗的背景模糊效果。

```TypeScript
// xxx.ets
@Entry
@Component
struct AlphabetIndexerSample {
  private arrayA: string[] = ['安'];
  private arrayB: string[] = ['卜', '白', '包', '毕', '丙'];
  private arrayC: string[] = ['曹', '成', '陈', '催'];
  private arrayL: string[] = ['刘', '李', '楼', '梁', '雷', '吕', '柳', '卢'];
  private value: string[] = ['#', 'A', 'B', 'C', 'D', 'E', 'F', 'G',
    'H', 'I', 'J', 'K', 'L', 'M', 'N',
    'O', 'P', 'Q', 'R', 'S', 'T', 'U',
    'V', 'W', 'X', 'Y', 'Z'];
  @State customBlurStyle: BlurStyle = BlurStyle.NONE;

  build() {
    Stack({ alignContent: Alignment.Start }) {
      Row() {
        List({ space: 20, initialIndex: 0 }) {
          ForEach(this.arrayA, (item: string) => {
            ListItem() {
              Text(item)
                .width('80%')
                .height('5%')
                .fontSize(30)
                .textAlign(TextAlign.Center)
            }
          }, (item: string) => item)

          ForEach(this.arrayB, (item: string) => {
            ListItem() {
              Text(item)
                .width('80%')
                .height('5%')
                .fontSize(30)
                .textAlign(TextAlign.Center)
            }
          }, (item: string) => item)

          ForEach(this.arrayC, (item: string) => {
            ListItem() {
              Text(item)
                .width('80%')
                .height('5%')
                .fontSize(30)
                .textAlign(TextAlign.Center)
            }
          }, (item: string) => item)

          ForEach(this.arrayL, (item: string) => {
            ListItem() {
              Text(item)
                .width('80%')
                .height('5%')
                .fontSize(30)
                .textAlign(TextAlign.Center)
            }
          }, (item: string) => item)
        }
        .width('30%')
        .height('100%')

        Column() {
          Column() {
            Text('切换模糊材质: ')
              .fontSize(24)
              .fontColor(0xcccccc)
              .width('100%')
            Button('COMPONENT_REGULAR')
              .margin('5vp')
              .width(200)
              .onClick(() => {
                this.customBlurStyle = BlurStyle.COMPONENT_REGULAR;
              })
            Button('BACKGROUND_THIN')
              .margin('5vp')
              .width(200)
              .onClick(() => {
                this.customBlurStyle = BlurStyle.BACKGROUND_THIN;
              })
          }.height('20%')

          Column() {
            AlphabetIndexer({ arrayValue: this.value, selected: 0 })
              .usingPopup(true) // 索引项被选中时显示提示弹窗
              .alignStyle(IndexerAlign.Left) // 提示弹窗在索引条右侧弹出
              .popupItemBorderRadius(24) // 设置提示弹窗索引项背板圆角半径
              .itemBorderRadius(14) // 设置索引项背板圆角半径
              .popupBackgroundBlurStyle(this.customBlurStyle) // 设置提示弹窗的背景模糊材质
              .popupTitleBackground(0xCCCCCC) // 设置提示弹窗一级索引项背景颜色
              .onSelect((index: number) => {
                console.info(this.value[index] + ' Selected!');
              })
              .onRequestPopupData((index: number) => {
                // 当选中A时，提示弹窗里面的二级索引文本列表显示A对应的列表arrayA，选中B、C、L时也同样
                // 选中其余索引项时，提示弹窗二级索引文本列表为空，提示弹窗会只显示一级索引项
                if (this.value[index] == 'A') {
                  return this.arrayA;
                } else if (this.value[index] == 'B') {
                  return this.arrayB;
                } else if (this.value[index] == 'C') {
                  return this.arrayC;
                } else if (this.value[index] == 'L') {
                  return this.arrayL;
                } else {
                  return [];
                }
              })
              .onPopupSelect((index: number) => {
                console.info('onPopupSelected:' + index);
              })
          }
          .height('80%')
        }
        .width('70%')
      }
      .width('100%')
      .height('100%')
      // $r('app.media.image')需要替换为开发者所需的图像资源文件。
      .backgroundImage($r("app.media.image"))
    }
  }
}
```
